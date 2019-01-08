---
title: Bcp_control | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_control
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_control function
ms.assetid: 32187282-1385-4c52-9134-09f061eb44f5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 323ea04d32501f04156ffa81452fad5e5cf86664
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52753082"
---
# <a name="bcpcontrol"></a>bcp_control
  Ändert die Standardeinstellungen für verschiedene Steuerelementparameter für einen Massenkopiervorgang zwischen einer Datei und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_control (  
HDBC   
hdbc  
,  
INT   
eOption  
,  
void*   
iValue  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *HDBC*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *eOption*  
 Ist einer der folgenden Werte:  
  
 BCPABORT  
 Beendet einen Massenkopiervorgang, der bereits ausgeführt wird. Rufen Sie **Bcp_control** mit einer *eOption* -Wert bcpabort von einem anderen Thread beendet einen laufenden Massenkopiervorgang. Die *iValue* Parameter wird ignoriert.  
  
 BCPBATCH  
 Die Anzahl von Zeilen pro Batch. Der Standardwert ist 0, womit beim Extrahieren von Daten alle Zeilen in einer Tabelle oder beim Kopieren von Daten nach [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle Zeilen in der Benutzerdatendatei angegeben werden. Ein Wert kleiner als 1 setzt BCPBATCH auf den Standardwert zurück.  
  
 BCPDELAYREADFMT  
 Ein boolescher Wert, wenn auf True festgelegt, führt dazu, dass [Bcp_readfmt](bcp-readfmt.md) , bei der Ausführung lesen. Wenn False (Standard), Bcp_readfmt sofort wird die Formatdatei zu lesen. Ein Sequenzfehler tritt treten auf, wenn BCPDELAYREADFMT den Wert "true", und Sie Bcp_columns oder Bcp_setcolfmt aufrufen.  
  
 Ein Sequenzfehler tritt auch aufrufen `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)FALSE)` nach dem Aufruf `bcp_control(hdbc,` BCPDELAYREADFMT`, (void *)TRUE)` und Bcp_writefmt.  
  
 Weitere Informationen finden Sie unter [Metadatenermittlung](../native-client/features/metadata-discovery.md).  
  
 BCPFILECP  
 *iValue* enthält die Nummer der Codepage für die Datendatei. Sie können die Nummer der Codepage angeben, z. B. 1252 oder 850 bzw. einen der folgenden Werte  
  
 BCPFILE_ACP: Daten in der Datei befinden sich in der Microsoft Windows? die Codepage des Clients.  
  
 BCPFILE_OEMCP: Daten in der Datei befinden sich auf der OEM-Codepage des Clients (Standard).  
  
 BCPFILE_RAW: Daten in der Datei befinden sich auf der Codepage von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 BCPFILEFMT  
 Die Versionsnummer des Datendateiformats. Dies kann 80 sein ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]), 90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]), 100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), 110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]), oder 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). Der Standardwert ist 120. Dies ist beim Exportieren und Importieren von Daten in Formate nützlich, die in früheren Versionen des Servers unterstützt wurden. Beispielsweise zum Importieren von Daten, die aus einer Textspalte abgerufen wurde eine [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Server in einer **varchar(max)** -Spalte in eine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher, sollten Sie 80 angeben. Auf ähnliche Weise bei Angabe 80 beim Exportieren von Daten aus einer **varchar(max)** Spalte gespeichert wie in den Spalten in gespeichert werden die [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] formatieren, und importieren Sie in einer Textspalte eine [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Server.  
  
 BCPFIRST  
 Dies ist die erste Datenzeile der zu kopierenden Datei oder Tabelle. Der Standard ist 1; ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück.  
  
 BCPFIRSTEX  
 Gibt für BCP-OUT-Vorgänge die erste Zeile der Datenbanktabelle an, die in die Datendatei kopiert werden soll.  
  
 Gibt für BCP-IN-Vorgänge die erste Zeile der Datendatei an, die in die Datenbanktabelle kopiert werden soll.  
  
 Die *iValue* -Parameter sollte die Adresse einer signierten 64-Bit-Ganzzahl, die mit dem Wert sein. Der maximale Wert, der an BCPFIRSTEX übergeben werden kann, ist 2 ^ 63-1.  
  
 BCPFMTXML  
 Gibt an, dass die generierte Formatdatei im XML-Format sein soll. Es ist standardmäßig deaktiviert.  
  
 XML-Formatdateien bieten größere Flexibilität, sind jedoch mit einigen Einschränkungen verbunden. Beispielsweise können Sie nicht das Präfix und das Abschlusszeichen für ein Feld gleichzeitig angeben in älteren Formatdateien möglich war.  
  
> [!NOTE]  
>  XML-Formatdateien werden nur unterstützt, wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zusammen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client installiert wird.  
  
 BCPHINTS  
 *iValue* enthält einen SQLTCHAR-Zeichenfolgenzeiger. Die adressierte Zeichenfolge gibt entweder Verarbeitungshinweise für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Massenkopieren oder eine Transact-SQL-Anweisung an, die ein Resultset zurückgibt. Wenn eine Transact-SQL-Anweisung angegeben ist, die mehr als ein Resultset zurückgibt, werden alle auf das erste Resultset folgenden Resultsets nicht berücksichtigt. Weitere Informationen zum Massenkopieren Verarbeitungshinweise, finden Sie unter [Hilfsprogramm "Bcp"](../../tools/bcp-utility.md).  
  
 BCPKEEPIDENTITY  
 Wenn *iValue* TRUE ist, gibt an, dass Massenkopierfunktionen Datenwerte, die für einen bereitgestellten einfügen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Spalten, die mit einer Identity-Einschränkung. Die Eingabedatei muss Werte für die IDENTITY-Spalten angeben. Wenn dies nicht festgelegt ist, werden neue Identitätswerte für die eingefügten Zeilen generiert. Alle in der Datei für die IDENTITY-Spalten vorhandenen Daten werden ignoriert.  
  
 BCPKEEPNULLS  
 Bestimmt, ob leere Datenwerte in der Datei in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle in NULL-Werte konvertiert werden. Wenn *iValue* TRUE ist, werden leere Werte konvertiert werden, auf NULL in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle. In der Standardeinstellung werden leere Werte in einen Standardwert für die Spalte in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle konvertiert, sofern ein Standardwert angegeben ist.  
  
 BCPLAST  
 Entspricht der letzten zu kopierenden Zeile. In der Standardeinstellung werden alle Zeilen kopiert. Ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück.  
  
 BCPLASTEX  
 Gibt für BCP-OUT-Vorgänge die letzte Zeile der Datenbanktabelle an, die in die Datendatei kopiert werden soll.  
  
 Gibt für BCP-IN-Vorgänge die letzte Zeile der Datendatei an, die in die Datenbanktabelle kopiert werden soll.  
  
 Die *iValue* -Parameter sollte die Adresse einer signierten 64-Bit-Ganzzahl, die mit dem Wert sein. Der maximale Wert, der an BCPLASTEX übergeben werden kann, ist 2^63-1.  
  
 BCPMAXERRS  
 Gibt die Anzahl von Fehlern an, die zulässig sind, bevor der Massenkopiervorgang fehlschlägt. Der Standardwert ist 10; ein Wert kleiner als 1 setzt diese Option auf den Standardwert zurück. Beim Massenkopieren sind maximal 65.535 Fehler zulässig. Wenn für diese Option größere Werte als 65.535 festgelegt werden, wird diese Option auf 65.535 festgelegt.  
  
 BCPODBC  
 Wenn "true" gibt an, dass **"DateTime"** und **Smalldatetime** ODBC-Zeitstempel Escape-Sequenz-Präfix und Suffix im Zeichenformat gespeicherten Werte verwenden. Die BCPODBC-Option gilt nur für BCP_OUT.  
  
 Bei "FALSE" eine **"DateTime"** Wert, der 1. Januar 1997 darstellt, auf die Zeichenfolge konvertiert wird: 1997-01-01 00:00:00.000. Wenn "true" werden die gleichen **"DateTime"** -Wert wie folgt dargestellt: {ts ' 1997-01-01 00:00:00.000'}.  
  
 BCPROWCOUNT  
 Gibt die Anzahl von Zeilen zurück, auf die sich der aktuelle (oder letzte) BCP-Vorgang auswirkt.  
  
 BCPTEXTFILE  
 Wenn der Wert TRUE ist, wird angegeben, dass die Datendatei eine Textdatei und keine Binärdatei ist. Bei einer Textdatei bestimmt BCP, ob es sich um Unicode handelt, indem der Unicode-Bytemarker in den ersten beiden Bytes der Datendatei überprüft wird.  
  
 BCPUNICODEFILE  
 Wenn der Wert TRUE ist, wird angegeben, dass die Eingabedatei eine Unicode-Datei ist.  
  
 *iValue*  
 Ist der Wert für den angegebenen *eOption*. *iValue* wird ein Ganzzahlwert (LONGLONG), die in einen void-Zeiger können für zukünftige Erweiterungen auf 64-Bit-Werte umgewandelt.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Funktion werden verschiedene Steuerelementparameter für Massenkopiervorgänge festgelegt, einschließlich der Anzahl von Fehlern, die vor dem Abbrechen eines Massenkopiervorgangs zulässig sind, der Nummern der ersten und letzten Zeilen, die aus einer Datendatei kopiert werden sollen, und der Batchgröße.  
  
 Außerdem wird diese Funktion dazu verwendet, die SELECT-Anweisung beim Massenkopieren des Resultsets einer SELECT-Anweisung aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzugeben. Legen Sie *eOption* auf BCPHINTS und *iValue* um einen Zeiger auf eine SQLTCHAR-Zeichenfolge, die mit der SELECT-Anweisung zu erhalten.  
  
 Diese Steuerelementparameter sind nur beim Kopieren zwischen einer Benutzerdatei und einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle sinnvoll. Steuerelementparameter-Einstellungen haben keine Auswirkungen auf zum kopierten Zeilen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [Bcp_sendrow](bcp-sendrow.md).  
  
## <a name="example"></a>Beispiel  
  
```  
// Variables like henv not specified.  
SQLHDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("address"), _T("address.add"), _T("addr.err"),  
   DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the number of rows per batch.   
if (bcp_control(hdbc, BCPBATCH, (void*) 1000) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set file column count.   
if (bcp_columns(hdbc, 1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Set the file format.   
if (bcp_colfmt(hdbc, 1, 0, 0, SQL_VARLEN_DATA, '\n', 1, 1)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
printf_s("%ld rows processed by bulk copy.", nRowsProcessed);  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
