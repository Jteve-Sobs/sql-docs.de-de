---
title: Konvertieren von DB-Library zum Massenkopieren in ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 55069754f96c36eb30d4f4af9229333405f0a982
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130888"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a>Konvertieren von DB-Library-Programmen zum Massenkopieren in ODBC-Programme
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Konvertieren eines Massenkopierprogramms für DB-Library, ODBC, ist einfach, da das Massenkopieren von unterstützten Funktionen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber die DB-Library-Funktionen zum Massenkopieren, mit Ausnahme der folgenden ähneln:  
  
-   DB-Library-Anwendungen übergeben als ersten Parameter von Funktionen zum Massenkopieren einen Zeiger auf eine DBPROCESS-Struktur. In ODBC-Anwendungen wird der DBPROCESS-Zeiger durch ein ODBC-Verbindungshandle ersetzt.  
  
-   DB-Library-Anwendungen rufen **BCP_SETL** vor dem Herstellen einer Verbindung, um Massenkopiervorgänge für eine DBPROCESS-Struktur zu aktivieren. ODBC-Anwendungen rufen stattdessen [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) vor dem Herstellen einer Verbindung mit Massenvorgängen für ein Verbindungshandle zu aktivieren:  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt keine DB-Library-Meldungs- und Fehlerbehandlungsroutinen; Sie müssen Aufrufen **SQLGetDiagRec** um von der ODBC-Massenkopierfunktionen ausgelöste Fehler und Meldungen zu erhalten. Die ODBC-Versionen der Massenkopierfunktionen geben die Standardrückgabecodes SUCCEED bzw. FAILED für das Massenkopieren zurück statt der Rückgabecodes im ODBC-Stil, wie SQL_SUCCESS oder SQL_ERROR.  
  
-   Die Werte für die DB-Library [Bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*Varlen* Parameter werden anders interpretiert als die ODBC **Bcp_bind**_CbData_Parameter.  
  
    |Angegebene Bedingung|DB-Library- *Varlen* Wert|ODBC *CbData* Wert|  
    |-------------------------|--------------------------------|-------------------------|  
    |Angabe von NULL-Werten|0|-1 (SQL_NULL_DATA)|  
    |Angabe von variablen Daten|-1|-10 (SQL_VARLEN_DATA)|  
    |Zeichen oder binäre Zeichenfolge mit der Länge 0|NA|0|  
  
     In DB-Library eine *Varlen* Wert-1 gibt an, dass Daten variabler Länge angegeben wird, den ODBC *CbData* wird interpretiert, dass nur NULL-Werte werden angegeben wird. Ändern Sie alle DB-Library *Varlen* von-1 in SQL_VARLEN_DATA und alle *Varlen* von 0 in SQL_NULL_DATA.  
  
-   Die DB-Library **Bcp_colfmt**_File_collen_ und den ODBC- [Bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*CbUserData* haben dasselbe Problem wie die  **Bcp_bind**_Varlen_ und *CbData* Parametern wie oben beschrieben. Ändern Sie alle DB-Library *File_collen* von-1 in SQL_VARLEN_DATA und alle *File_collen* von 0 in SQL_NULL_DATA.  
  
-   Die *iValue* Parameter der ODBC- [Bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) -Funktion ist ein void-Zeiger. In der DB-Library *iValue* wurde eine ganze Zahl. Wandeln Sie die Werte für die ODBC *iValue* in void *.  
  
-   Die **Bcp_control** -Option bcpmaxerrs legt fest, wie viele Zeilen Fehler enthalten können, bevor ein Massenkopiervorgang fehlschlägt. Der Standardwert für BCPMAXERRS ist 0 (Fehlschlagen beim ersten Fehler) in der DB-Library-Version von **Bcp_control** und 10 in der ODBC-Version. DB-Library-Anwendungen, die abhängig von der Standardwert von 0 beendet einen Massenkopiervorgang geändert werden müssen, um die ODBC-Funktion **Bcp_control** BCPMAXERRS auf 0 festgelegt.  
  
-   Die ODBC **Bcp_control** Funktion unterstützt die folgenden Optionen, die nicht von der DB-Library-Version unterstützt **Bcp_control**:  
  
    -   BCPODBC  
  
         Bei Festlegung auf "true" gibt an, dass **"DateTime"** und **Smalldatetime** müssen im Zeichenformat gespeicherten Werte ODBC-Zeitstempel Escape-Sequenz-Präfix und Suffix. Dies gilt nur für BCP_OUT-Vorgänge.  
  
         Bcpodbc auf "FALSE" festgelegt wurde eine **"DateTime"** -Wert konvertiert in eine Zeichenfolge wie folgt ausgegeben:  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         Bcpodbc auf TRUE festgelegt, die gleiche wurde **"DateTime"** -Wert wie folgt ausgegeben:  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   BCPKEEPIDENTITY  
  
         Durch die Festlegung dieser Option auf TRUE wird angegeben, dass Massenkopierfunktionen Datenwerte einfügen, die für Spalten mit einer IDENTITY-Einschränkung bereitgestellt werden. Wenn dies nicht festgelegt ist, werden neue Identitätswerte für die eingefügten Zeilen generiert.  
  
    -   BCPHINTS  
  
         Gibt verschiedene Optimierungen für das Massenkopieren an. Diese Option kann in Version 6.5 und früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht verwendet werden.  
  
    -   BCPFILECP  
  
         Gibt die Codepage für die Datendatei des Massenkopiervorgangs an.  
  
    -   BCPUNICODEFILE  
  
         Gibt an, dass eine Datendatei für das Massenkopieren im Zeichenmodus eine Unicode-Datei ist.  
  
-   Die ODBC **Bcp_colfmt** -Funktion nicht unterstützt die *File_type* Indikator für SQLCHAR da ein Konflikt mit der ODBC SQLCHAR-Typdefinition. Verwenden Sie stattdessen SQLCHARACTER für **Bcp_colfmt**.  
  
-   In den ODBC-Versionen von Funktionen zum Massenkopieren, das Format für die Arbeit mit **"DateTime"** und **Smalldatetime** -Werte in Zeichenfolgen wird die ODBC-Format Yyyy-mm-tt ss.sss verarbeitet werden; **Smalldatetime** Werte verwenden Sie das ODBC-Format Yyyy-mm-tt hh: mm:.  
  
     Die DB-Library-Versionen von Funktionen zum Massenkopieren akzeptieren **"DateTime"** und **Smalldatetime** -Werte in Zeichenfolgen, die mit verschiedenen Formaten:  
  
    -   Das Standardformat *mmm Dd Yyyy mmXX* , in denen *Xx* ist AM oder PM.  
  
    -   **"DateTime"** und **Smalldatetime** Zeichenfolgen in einem beliebigen Format, die von der DB-Library unterstützt **Dbconvert** Funktion.  
  
    -   Wenn die **internationale Einstellungen verwenden** Kontrollkästchen aktiviert ist, klicken Sie auf der DB-Library **Optionen** Registerkarte die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server-Clientkonfiguration, die DB-Library-Funktionen zum Massenkopieren auch akzeptieren Datumsangaben in den regionalen das Datumsformat für die gebietsschemaeinstellung des Registrierung des Clientcomputers definiert.  
  
     Die DB-Library-Funktionen zum Massenkopieren akzeptieren die ODBC keine **"DateTime"** und **Smalldatetime** Formate.  
  
     Wenn das SQL_SOPT_SS_REGIONALIZE-Anweisungsattribut auf SQL_RE_ON festgelegt wurde, akzeptieren die ODBC-Funktionen zum Massenkopieren auch Datumsangaben in dem regionalen Datumsformat, das für die Einstellung des Gebietsschemas in der Registrierung des Clientcomputers definiert wurde.  
  
-   Bei der Ausgabe von **Geld** Werte im Zeichenformat, ODBC-Bulk Copy Functions vier Dezimalstellen mit einfacher Genauigkeit und keine Trennzeichen für Tausenderstellen; DB-Library-Versionen nur zwei Dezimalstellen angeben und die Trennzeichen für Tausenderstellen enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)   
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
