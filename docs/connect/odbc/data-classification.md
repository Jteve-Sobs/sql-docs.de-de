---
title: Verwenden von Klassifizierung von Daten mit Microsoft ODBC-Treiber für SQLServer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-makouz
ms.author: v-makouz
manager: kenvh
ms.openlocfilehash: 0d010bcfc74011cb0e7e2864aeff97e65bf16203
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53211489"
---
# <a name="data-classification"></a>Datenklassifizierung
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>Übersicht
Zum Verwalten von sensiblen Daten, SQL Server und Azure SQL-Server wurde die Möglichkeit eingeführt, die Datenbankspalten mit Vertraulichkeit Metadaten zu bereitzustellen, können die Client-Anwendung auf verschiedene Arten von sensiblen Daten (z. B. im Gesundheitswesen, finanzielle, usw. zu behandeln ) in Übereinstimmung mit den Datenschutzrichtlinien.

Weitere Informationen dazu, wie Spalten Klassifizierung zuweisen, finden Sie unter [SQL-Datenermittlung und-Klassifizierung](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-2017).

Microsoft ODBC-Treiber 17.2 ermöglicht den Abruf dieser Metadaten über SQLGetDescField unter Verwendung des Bezeichners der SQL_CA_SS_DATA_CLASSIFICATION-Feld.

## <a name="format"></a>Format
SQLGetDescField weist die folgende Syntax:

```  
SQLRETURN SQLGetDescField(  
     SQLHDESC        DescriptorHandle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     FieldIdentifier,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```
*DescriptorHandle*  
 [Eingabe] IRD (Implementierungszeilendeskriptor) behandeln. Kann durch einen Aufruf von SQLGetStmtAttr mit SQL_ATTR_IMP_ROW_DESC-Anweisungsattribut abgerufen werden
  
 *RecNumber*  
 [Eingabe] 0
  
 *FieldIdentifier*  
 [Eingabe] SQL_CA_SS_DATA_CLASSIFICATION
  
 *ValuePtr*  
 [Ausgabe] Ausgabepuffer
  
 *BufferLength*  
 [Eingabe] Die Länge des Ausgabepuffers in bytes

 *StringLengthPtr* [Ausgabe] Zeiger auf den Puffer, in dem die Gesamtzahl der verfügbaren zurückzugebenden in Bytes zurückgegeben *ValuePtr*.
 
> [!NOTE]
> Wenn die Größe des Puffers unbekannt ist, sie kann bestimmt werden durch Aufrufen von SQLGetDescField mit *ValuePtr* wie NULL und untersuchen den Wert der *StringLengthPtr*.
 
Wenn Datenklassifizierung Informationen nicht verfügbar ist, ist ein *ungültige Deskriptorfeld* Fehler zurückgegeben.

Bei einem erfolgreichen Aufruf SQLGetDescField, der Puffer verweist *ValuePtr* enthält die folgenden Daten:

 `nn nn [n sensitivitylabels] tt tt [t informationtypes] cc cc [c columnsensitivitys]`

> [!NOTE]
> `nn nn`, `tt tt`, und `cc cc` multibyte ganzen Zahlen besteht, die mit dem niedrigstwertigen Byte an der niedrigsten Adresse gespeichert werden.

*`sensitivitylabel`* und *`informationtype`* sind beide im Format

 `nn [n bytes name] ii [i bytes id]`

*`columnsensitivity`* das Format

 `nn nn [n sensitivityprops]`

Für jede Spalte *(c)*, *n* 4-Byte- *`sensitivityprops`* vorhanden sind:

 `ss ss tt tt`

s - Index in die *`sensitivitylabels`* Array `FF FF` , wenn keine Bezeichnung

t - Index in die *`informationtypes`* Array `FF FF` , wenn keine Bezeichnung


<br><br>
Das Format der Daten kann die folgenden Pseudo-Strukturen ausgedrückt werden:

```
struct IDnamePair {
 BYTE nameLen;
 USHORT name[nameLen];
 BYTE idLen;
 USHORT id[idLen];
};

struct SensitivityProp {
 USHORT labelIdx;
 USHORT infoTypeIdx;
};

USHORT nLabels;
struct IDnamePair labels[nLabels];
USHORT nInfoTypes;
struct IDnamePair infotypes[nInfoTypes];
USHORT nColumns;
struct {
 USHORT nProps;
 struct SensitivityProp[nProps];
} columnClassification[nColumns];
```


## <a name="code-sample"></a>Codebeispiel
Testen Sie die Anwendung zeigt, wie zum Lesen von Metadaten für die Datenklassifizierung. Für Windows können sie das mit kompiliert werden `cl /MD dataclassification.c /I (directory of msodbcsql.h) /link odbc32.lib` , und führen Sie mit einer Verbindungszeichenfolge und einer SQL-Abfrage (die gibt Spalten klassifiziert) als Parameter:

```
#ifdef _WIN32
#include <windows.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include <msodbcsql.h>
#include <stdio.h>
SQLHANDLE env, dbc, stmt;
void checkRC_exit(SQLRETURN rc, SQLHANDLE hand, SQLSMALLINT htype, int retcode, char *action)
{
    if ((rc == SQL_ERROR || rc == SQL_SUCCESS_WITH_INFO) && hand)
    {
        char msg[1024], state[6];
        int i = 0;
        SQLRETURN rc2;
        SQLINTEGER err;
        SQLSMALLINT lenout;
        while ((rc2 = SQLGetDiagRec(htype, hand, ++i, state, &err, msg, sizeof(msg), &lenout)) == SQL_SUCCESS ||
            rc2 == SQL_SUCCESS_WITH_INFO)
            printf("%d (%d)[%s]%s\n", i, err, state, msg);
    }
    if (rc == SQL_ERROR && retcode)
    {
        printf("Error occurred%s%s\n", action ? " upon " : "", action ? action : "");
        exit(retcode);
    }
}
void printLabelInfo(char *type, char **pptr)
{
    char *ptr = *pptr;
    unsigned short nlabels;
    printf("----- %s(%u) -----\n", type, nlabels = *(unsigned short*)ptr);
    ptr += sizeof(unsigned short);
    while (nlabels--)
    {
        int namelen, idlen;
        char *nameptr, *idptr;
        namelen = *ptr++;
        nameptr = ptr;
        ptr += namelen * 2;
        idlen = *ptr++;
        idptr = ptr;
        ptr += idlen * 2;
        wprintf(L"Name: \"%.*s\" Id: \"%.*s\"\n", namelen, nameptr, idlen, idptr);
    }
    *pptr = ptr;
}
int main(int argc, char **argv)
{
    unsigned char *dcbuf;
    unsigned int dclen = 0;
    SQLRETURN rc;
    SQLHANDLE ird;
    if (argc < 3)
    {
        fprintf(stderr, "usage: dataclassification connstr query\n");
        return 1;
    }
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_ENV, 0, &env), 0, 0,
        2, "allocate environment");
    checkRC_exit(SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0), env, SQL_HANDLE_ENV,
        3, "set ODBC version");
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc), env, SQL_HANDLE_ENV,
        4, "allocate connection");
    checkRC_exit(SQLDriverConnect(dbc, 0, argv[1], SQL_NTS, 0, 0, 0, SQL_DRIVER_NOPROMPT), dbc, SQL_HANDLE_DBC,
        5, "connect to server");
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt), dbc, SQL_HANDLE_DBC,
        6, "allocate statement");
    checkRC_exit(SQLExecDirect(stmt, argv[2], SQL_NTS), stmt, SQL_HANDLE_STMT,
        7, "execute query");
    checkRC_exit(SQLGetStmtAttr(stmt, SQL_ATTR_IMP_ROW_DESC, (SQLPOINTER)&ird, SQL_IS_POINTER, 0), stmt, SQL_HANDLE_STMT,
        8, "get IRD handle");
    rc = SQLGetDescFieldW(ird, 0, SQL_CA_SS_DATA_CLASSIFICATION, dcbuf, 0, &dclen);
    if (rc != SQL_SUCCESS && rc != SQL_SUCCESS_WITH_INFO)
    {
        checkRC_exit(rc, ird, SQL_HANDLE_DESC, 0, 0);
        printf("Error reading SQL_CA_SS_DATA_CLASSIFICATION IRD field. Ensure that the driver and\n"
            "server both support the Data Classification feature, and that the query returns columns\n"
            "with classification information.\n");
    }
    else
    {
        SQLINTEGER dclenout;
        unsigned char *dcptr;
        unsigned short ncols;
        printf("Data Classification information (%u bytes):\n", dclen);
        if (!(dcbuf = malloc(dclen)))
        {
            printf("Memory Allocation Error");
            return 9;
        }
        checkRC_exit(SQLGetDescFieldW(ird, 0, SQL_CA_SS_DATA_CLASSIFICATION, dcbuf, dclen, &dclenout),
            ird, SQL_HANDLE_DESC, 10, "reading SQL_CA_SS_DATA_CLASSIFICATION");
        dcptr = dcbuf;
        printLabelInfo("Labels", &dcptr);
        printLabelInfo("Information Types", &dcptr);
        printf("----- Column Sensitivities(%u) -----\n", ncols = *(unsigned short*)dcptr);
        dcptr += sizeof(unsigned short);
        while (ncols--)
        {
            unsigned short nprops = *(unsigned short*)dcptr;
            dcptr += sizeof(unsigned short);
            while (nprops--)
            {
                unsigned short labelidx, typeidx;
                labelidx = *(unsigned short*)dcptr; dcptr += sizeof(unsigned short);
                typeidx = *(unsigned short*)dcptr; dcptr += sizeof(unsigned short);
                printf(labelidx == 0xFFFF ? "(none) " : "%u ", labelidx);
                printf(typeidx == 0xFFFF ? "(none)\n" : "%u\n", typeidx);
            }
            printf("-----\n");
        }
        if (dcptr != dcbuf + dclen)
        {
            printf("Error: unexpected parse of DATACLASSIFICATION data\n");
            return 11;
        }
        free(dcbuf);
    }
    return 0;
}
```

