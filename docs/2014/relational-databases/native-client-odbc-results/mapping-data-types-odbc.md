---
title: Zuordnen von Datentypen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [ODBC]
- result sets [ODBC], data types
- ODBC data types, mapping
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], mapping
- sql_variant data type
- SQL Server Native Client ODBC driver, data types
ms.assetid: 4ba0924d-9fca-4c48-aced-0a8d817b3dde
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcca4bc6161526d1bd78e55bc9452f2d7d9d69d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200001"
---
# <a name="mapping-data-types-odbc"></a>Zuordnen von Datentypen (ODBC)
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber ordnet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL-Datentypen in ODBC-SQL-Datentypen. In den folgenden Abschnitten werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-SQL-Datentypen sowie die ODBC-SQL-Datentypen, denen sie zugeordnet werden, erläutert. Außerdem werden die ODBC-SQL-Datentypen und die zugehörigen ODBC-C-Datentypen sowie die unterstützten und standardmäßigen Konvertierungen erklärt.  
  
> [!NOTE]  
>  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Zeitstempel** -Datentyp wird dem SQL_BINARY- oder SQL_VARBINARY ODBC-Datentyp zugeordnet, da die Werte in **Zeitstempel** Spalten sind nicht **"DateTime"** Werte aber **binary(8)** oder **varbinary(8)** Werte, die die Sequenz der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Aktivität in der Zeile. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber einen SQL_C_WCHAR-Wert (Unicode) erkennt, der eine ungerade Anzahl von Bytes enthält, wird das letzte ungerade Byte abgeschnitten.  
  
## <a name="dealing-with-sqlvariant-data-type-in-odbc"></a>Arbeiten mit dem 'sql_variant'-Datentyp in ODBC  
 Die **Sql_variant** -Datentypspalte darf keines der Datentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] außer großer Objekte (LOBs), z. B. **Text**, **Ntext**, und  **Image**. Beispielsweise kann die Spalte enthalten **Smallint** Werte für einige Zeilen **"float"** Werte für die anderen Zeilen hat und **Char/Nchar** Werte im weiteren Verlauf.  
  
 Die **Sql_variant** Datentyp ähnelt der **Variant** -Datentyp in Microsoft Visual Basic??.  
  
### <a name="retrieving-data-from-the-server"></a>Abrufen von Daten vom Server  
 ODBC verfügt nicht über ein Konzept von variant-Typen, beschränken die Verwendung der **Sql_variant** -Datentyp mit einer ODBC-Treiber in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], wenn die Bindung angegeben wird, die **Sql_variant** Datentyp muss an eines der dokumentierten ODBC-Datentypen gebunden werden. **SQL_CA_SS_VARIANT_TYPE**, ein neues Attribut für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt den Datentyp einer Instanz zurück. die **Sql_variant** Spalte für den Benutzer.  
  
 Wenn kein binden festgelegt ist, die [SQLGetData](../native-client-odbc-api/sqlgetdata.md) Funktion kann verwendet werden, um zu bestimmen, den Datentyp einer Instanz in der **Sql_variant** Spalte.  
  
 Zum Abrufen **Sql_variant** Daten gehen Sie folgendermaßen vor.  
  
1.  Rufen Sie **SQLFetch** zum Positionieren auf die Zeile abgerufen.  
  
2.  Rufen Sie **SQLGetData**, und legen Sie SQL_C_BINARY für den Typ und für die Data 0. Dies zwingt den Treiber zum Lesen der **Sql_variant** Header. Der Header enthält den Datentyp dieser Instanz in der **Sql_variant** Spalte. **SQLGetData** gibt die Größe (in Byte) des Werts zurück.  
  
3.  Rufen Sie [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) durch Angabe **SQL_CA_SS_VARIANT_TYPE** als Attributwert. Diese Funktion gibt die C-Datentyp der Instanz in der **Sql_variant** Spalte an den Client.  
  
 Im folgenden Codesegment werden die vorhergehenden Schritte gezeigt.  
  
```  
while ((retcode = SQLFetch (hstmt))==SQL_SUCCESS)  
{  
    if (retcode != SQL_SUCCESS && retcode != SQL_SUCCESS_WITH_INFO)  
    {  
        SQLError (NULL, NULL, hstmt, NULL,   
                    &lNativeError,szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    retcode = SQLGetData (hstmt, 1, SQL_C_BINARY,   
                                pBuff,0,&Indicator);//Figure out the length  
    if (retcode != SQL_SUCCESS_WITH_INFO && retcode != SQL_SUCCESS)  
    {  
        SQLError (NULL, NULL, hstmt, NULL, &lNativeError,   
                    szError,MAX_DATA,&sReturned);  
        printf_s ("%s\n",szError);  
        goto Exit;  
    }  
    printf_s ("Byte length : %d ",Indicator); //Print out the byte length  
  
    int iValue = 0;  
    retcode = SQLColAttribute (hstmt, 1, SQL_CA_SS_VARIANT_TYPE, NULL,   
                                        NULL,NULL,&iValue);  //Figure out the type  
    printf_s ("Sub type = %d ",iValue);//Print the type, the return is C_type of the column]  
  
// Set up a new binding or do the SQLGetData on that column with   
// the appropriate type  
}  
```  
  
 Wenn der Benutzer die Bindung mit erstellt [SQLBindCol](../native-client-odbc-api/sqlbindcol.md), liest der Treiber die Metadaten und Daten. Der Treiber konvertiert die Daten dann in den entsprechenden in der Bindung angegebenen ODBC-Typ.  
  
### <a name="sending-data-to-the-server"></a>Senden von Daten an den Server  
 **SQL_SS_VARIANT**, einen neuen Datentyp für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber wird für Datenübertragungen an verwendet eine **Sql_variant** Spalte. Beim Senden von Daten an den Server mit Parametern (z. B. INSERT INTO TableName VALUES (?,?)), [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) wird verwendet, um die Parameterinformationen, einschließlich der C-Typ und dem entsprechenden geben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Typ. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber konvertiert den C-Datentyp in einen entsprechenden **Sql_variant** Untertypen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verarbeiten von Ergebnissen &#40;ODBC&#41;](processing-results-odbc.md)  
  
  
