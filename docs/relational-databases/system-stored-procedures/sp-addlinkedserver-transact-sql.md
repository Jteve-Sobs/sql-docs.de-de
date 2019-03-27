---
title: Sp_addlinkedserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addlinkedserver_TSQL
- sp_addlinkedserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlinkedserver
ms.assetid: fed3adb0-4c15-4a1a-8acd-1b184aff558f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b4ff861015fc669defee69fece5c26ee45d66eaa
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493910"
---
# <a name="spaddlinkedserver-transact-sql"></a>sp_addlinkedserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Verbindungsserver. Ein Verbindungsserver ermöglicht den Zugriff auf verteilte, heterogene Abfragen für OLE DB-Datenquellen. Nachdem ein Verbindungsserver erstellt wird **Sp_addlinkedserver**, verteilte Abfragen für diesen Server ausgeführt werden können. Wenn der Verbindungsserver als Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]definiert wird, können remote gespeicherte Prozeduren ausgeführt werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addlinkedserver [ @server= ] 'server' [ , [ @srvproduct= ] 'product_name' ]   
     [ , [ @provider= ] 'provider_name' ]  
     [ , [ @datasrc= ] 'data_source' ]   
     [ , [ @location= ] 'location' ]   
     [ , [ @provstr= ] 'provider_string' ]   
     [ , [ @catalog= ] 'catalog' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @server = ] 'server'` Ist der Name des verknüpften Servers erstellen. *server* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
`[ @srvproduct = ] 'product_name'` Ist der Produktname der OLE DB-Datenquelle als Verbindungsserver hinzufügen. *Product_name* ist **Nvarchar (** 128 **)**, hat den Standardwert NULL. Wenn **SQL Server**, *Provider_name*, *Data_source*, *Speicherort*, *Provider_string*, und *Katalog* müssen nicht angegeben werden.  
  
`[ @provider = ] 'provider_name'` Ist der eindeutige Programmbezeichner (PROGID) des OLE DB-Anbieters, der dieser Datenquelle entspricht. *Provider_name* muss eindeutig für den angegebenen OLE DB-Anbieter auf dem aktuellen Computer installiert sein. *Provider_name* ist **Nvarchar (** 128 **)**, hat den Standardwert NULL; aber wenn *Provider_name* wird weggelassen, wird SQLNCLI verwendet. (Wenn Sie SQLNCLI verwenden, leitet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur neuesten Version des OLE DB-Anbieters von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client um.) Es wird vorausgesetzt, dass der OLE DB-Anbieter mit der angegebenen PROGID in der Registrierung registriert ist.  
  
`[ @datasrc = ] 'data_source'` Ist der Name der Datenquelle an, wie er vom OLE DB-Anbieter interpretiert. *Data_source* ist **Nvarchar (** 4000 **)**. *Data_source* wird als DBPROP_INIT_DATASOURCE-Eigenschaft zum Initialisieren des OLE DB-Anbieters übergeben.  
  
`[ @location = ] 'location'` Ist der Speicherort der Datenbank an, wie er vom OLE DB-Anbieter interpretiert. *Speicherort* ist **Nvarchar (** 4000 **)**, hat den Standardwert NULL. *Speicherort* wird als DBPROP_INIT_LOCATION-Eigenschaft zum Initialisieren des OLE DB-Anbieters übergeben.  
  
`[ @provstr = ] 'provider_string'` Ist die OLE DB-Anbieter-spezifischen Verbindungsdaten-Zeichenfolge, die eine eindeutige Datenquelle identifiziert. *Provider_string* ist **Nvarchar (** 4000 **)**, hat den Standardwert NULL. *Standard* entweder an die IDataInitialize übergeben oder als DBPROP_INIT_PROVIDERSTRING-Eigenschaft festgelegt wird, um den OLE DB-Anbieter zu initialisieren.  
  
 Wenn der Verbindungsserver erstellt wird, für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, die Instanz kann angegeben werden, mit dem SERVER-Schlüsselwort als SERVER =*Servername*\\*Instancename*an einer bestimmten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Servername* ist der Name des Computers, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, und *Instancename* ist der Name der bestimmten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem der Benutzer verbunden wird.  
  
> [!NOTE]
>  Der Zugriff auf eine gespiegelte Datenbank ist nur dann möglich, wenn eine Verbindungszeichenfolge den Datenbanknamen enthält. Dieser Name ist notwendig, um Failoverversuche des Datenzugriffsanbieters zu ermöglichen. Die Datenbank kann angegeben werden, der **@provstr** oder **@catalog** Parameter. Optional kann in der Verbindungszeichenfolge auch ein Failoverpartnername angegeben werden.  
  
`[ @catalog = ] 'catalog'` Ist der Katalog verwendet werden, wenn eine Verbindung mit der OLE DB-Anbieter hergestellt wird. *Katalog* ist **Sysname**, hat den Standardwert NULL. *Katalog* wird als DBPROP_INIT_CATALOG-Eigenschaft zum Initialisieren des OLE DB-Anbieters übergeben. Wenn der Verbindungsserver für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiert wird, verweist catalog auf die Standarddatenbank, der der Verbindungsserver zugeordnet ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Die folgende Tabelle zeigt die Einrichtungsmöglichkeiten eines Verbindungsservers für Datenquellen, auf die über OLE DB zugegriffen werden kann. Für die Einrichtung eines Verbindungsservers für eine bestimmte Datenquelle gibt es mehrere Möglichkeiten; für die einzelnen Datenquellentypen sind möglicherweise mehrere Zeilen vorhanden. Diese Tabelle zeigt auch die **Sp_addlinkedserver** Parameterwerte für das Einrichten des verknüpften Servers verwendet werden soll.  
  
|OLE DB-Remotedatenquelle|OLE DB-Anbieter|product_name|provider_name|data_source|location|provider_string|catalog|  
|-------------------------------|---------------------|-------------------|--------------------|------------------|--------------|----------------------|-------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <sup>1</sup> (Standard)||||||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter||**SQLNCLI**|Netzwerkname von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (für Standardinstanz)|||Datenbankname (optional)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter||**SQLNCLI**|*Servername*\\*Instancename* (für bestimmte Instanz)|||Datenbankname (optional)|  
|Oracle, Version 8 und höher|Oracle-Anbieter für OLE DB|Any|**OraOLEDB.Oracle**|Alias für die Oracle-Datenbank||||  
|Access/Jet|Microsoft OLE DB-Anbieter für Jet|Any|**Microsoft.Jet.OLEDB.4.0**|Vollständiger Pfad der Jet-Datenbankdatei||||  
|ODBC-Datenquelle (ODBC data source)|Microsoft OLE DB-Anbieter für ODBC|Any|**MSDASQL**|System-DSN der ODBC-Datenquelle||||  
|ODBC-Datenquelle (ODBC data source)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für ODBC|Any|**MSDASQL**|||ODBC-Verbindungszeichenfolge||  
|Dateisystem|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für den Indexdienst|Any|**MSIDXS**|Katalogname von Indexdienstleistung||||  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel-Kalkulationstabelle|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für Jet|Any|**Microsoft.Jet.OLEDB.4.0**|Vollständiger Pfad der Excel-Datei||Excel 5.0||  
|IBM DB2-Datenbank|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für DB2|Any|**DB2OLEDB**|||Finden Sie unter [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für DB2-Dokumentation.|Katalogname der DB2-Datenbank|  
  
 <sup>1</sup> auf diese Weise für das Einrichten eines Verbindungsservers erzwingt, dass der Name des Verbindungsservers, auf die gleichen den Netzwerknamen der Remoteinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Verwendung *Data_source* um den Server anzugeben.  
  
 <sup>2</sup> "Any" gibt an, dass der Produktname beliebig sein kann.  
  
 Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist der Anbieter, der verwendet wird, mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wenn kein Anbietername angegeben ist, oder wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Produktname angegeben ist. Selbst wenn Sie den älteren Anbieternamen, SQLOLEDB, angeben, wird er beim persistenten Speichern im Katalog in SQLNCLI geändert.  
  
 Die *Data_source*, *Speicherort*, *Provider_string*, und *Katalog* Parameter zu identifizieren, die verknüpften Datenbanken Server verweist auf. Falls einer dieser Parameter den Wert NULL hat, wird die entsprechende OLE DB-Initialisierungseigenschaft nicht festgelegt.  
  
 Verwenden Sie in einer Clusterumgebung, wenn Sie Dateinamen angeben, um auf OLE DB-Datenquellen zu verweisen, den UNC-Namen (Universal Naming Convention) oder ein freigegebenes Laufwerk, um den Speicherort anzugeben.  
  
 **Sp_addlinkedserver** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
> [!IMPORTANT]
>  Wenn ein Verbindungsserver erstellt wird, mithilfe von **Sp_addlinkedserver**, für alle lokalen Anmeldenamen eine standardmäßige selbstzuordnung hinzugefügt. Für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anbieter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentifizierte Anmeldenamen möglicherweise für den Zugriff auf den Anbieter unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto. Administratoren sollten eventuell `sp_droplinkedsrvlogin <linkedserver_name>, NULL` verwenden, um die globale Zuordnung zu entfernen.  
  
## <a name="permissions"></a>Berechtigungen  
 Die `sp_addlinkedserver` -Anweisung erfordert die `ALTER ANY LINKED SERVER` Berechtigung. (SSMS **neuer Verbindungsserver** Dialogfeld wird implementiert, auf eine Weise, die erfordert die Mitgliedschaft in der `sysadmin` -Serverrolle sein.)  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-the-microsoft-sql-server-native-client-ole-db-provider"></a>A. Verwenden des Microsoft SQL Server Native Client-OLE DB-Anbieters  
 Im folgenden Beispiel wird der Verbindungsserver `SEATTLESales` erstellt. Der Produktname lautet `SQL Server`, und es wird kein Anbietername verwendet.  
  
```  
USE master;  
GO  
EXEC sp_addlinkedserver   
   N'SEATTLESales',  
   N'SQL Server';  
GO  
```  
  
 Das folgende Beispiel erstellt einen Verbindungsserver `S1_instance1` auf einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter.  
  
```  
EXEC sp_addlinkedserver     
   @server=N'S1_instance1',   
   @srvproduct=N'',  
   @provider=N'SQLNCLI',   
   @datasrc=N'S1\instance1';  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-microsoft-access"></a>B. Verwenden des Microsoft OLE DB-Anbieters für Microsoft Access  
 Der Microsoft.Jet.OLEDB.4.0-Anbieter stellt eine Verbindung mit Microsoft Access-Datenbanken her, die das 2002-2003-Format verwenden. Im folgenden Beispiel wird der Verbindungsserver `SEATTLE Mktg` erstellt.  
  
> [!NOTE]  
>  In diesem Beispiel wird vorausgesetzt, dass beide [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access und die **Northwind** -Datenbank installiert sind und dass die **Northwind** Datenbank befindet sich in C:\Msoffice\Access\Samples.  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.Jet.OLEDB.4.0',   
   @srvproduct = N'OLE DB Provider for Jet',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.mdb';  
GO  
```  
  
 Der Microsoft.ACE.OLEDB.12.0-Anbieter stellt eine Verbindung mit Microsoft Access-Datenbanken her, die das 2007-Format verwenden. Im folgenden Beispiel wird der Verbindungsserver `SEATTLE Mktg` erstellt.  
  
> [!NOTE]  
>  In diesem Beispiel wird vorausgesetzt, dass beide [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access und die **Northwind** -Datenbank installiert sind und dass die **Northwind** Datenbank befindet sich in C:\Msoffice\Access\Samples.  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.ACE.OLEDB.12.0',   
   @srvproduct = N'OLE DB Provider for ACE',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.accdb';  
GO  
```  
  
### <a name="c-using-the-microsoft-ole-db-provider-for-odbc-with-the-datasource-parameter"></a>C. Verwenden des Microsoft OLE DB-Anbieters für ODBC mit dem data_source-Parameter  
 Das folgende Beispiel erstellt einen Verbindungsserver namens `SEATTLE Payroll` , verwendet der [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für ODBC (`MSDASQL`) und die *Data_source* Parameter.  
  
> [!NOTE]  
>  Der angegebene ODBC-Datenquellenname muss vor der Verwendung des Verbindungsservers auf dem Server als System-DSN definiert werden.  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Payroll',   
   @srvproduct = N'',  
   @provider = N'MSDASQL',   
   @datasrc = N'LocalServer';  
GO  
```  
  
### <a name="d-using-the-microsoft-ole-db-provider-for-excel-spreadsheet"></a>D. Verwenden des Microsoft OLE DB-Anbieters für Excel-Arbeitsblätter  
 Zum Erstellen einer Verbindungsserverdefinition mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für Jet auf einem Excel-Arbeitsblatt im 1997-2003-Format erstellen zunächst einen benannten Bereich in Excel unter Angabe von Spalten und Zeilen des auszuwählenden Excel-Arbeitsblatts. Auf den Namen des Bereichs kann dann als Tabellenname in einer verteilten Abfrage verwiesen werden.  
  
```  
EXEC sp_addlinkedserver 'ExcelSource',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   'c:\MyData\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
GO  
```  
  
 Um auf Daten zugreifen zu können, die sich in einer Excel-Kalkulationstabelle befinden, ordnen Sie einem Zellenbereich einen Namen zu. Die folgende Abfrage kann für den Zugriff auf den angegebenen benannten Bereich `SalesData` als Tabelle mithilfe des zuvor eingerichteten Verbindungsservers verwendet werden.  
  
```  
SELECT *  
   FROM ExcelSource...SalesData;  
GO  
```  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter einem Domänenkonto ausgeführt wird, das Zugriff auf eine Remotefreigabe hat, kann ein UNC-Pfad anstelle eines zugeordneten Laufwerks verwendet werden.  
  
```  
EXEC sp_addlinkedserver 'ExcelShare',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   '\\MyServer\MyShare\Spreadsheets\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
```  
  
 Verwenden Sie den ACE-Anbieter, um eine Verbindung mit einem Excel-Arbeitsblatt im Excel 2007-Format herzustellen.  
  
```  
EXEC sp_addlinkedserver @server = N'ExcelDataSource',   
@srvproduct=N'ExcelData', @provider=N'Microsoft.ACE.OLEDB.12.0',   
@datasrc=N'C:\DataFolder\People.xlsx',  
@provstr=N'EXCEL 12.0' ;  
  
```  
  
### <a name="e-using-the-microsoft-ole-db-provider-for-jet-to-access-a-text-file"></a>E. Verwenden des Microsoft OLE DB-Anbieters für Jet für den Zugriff auf eine Textdatei  
 Im folgenden Beispiel wird ein Verbindungsserver für den direkten Zugriff auf Textdateien erstellt, ohne die Dateien als Tabellen in einer MDB-Datei von Microsoft Access zu verknüpfen. Der Anbieter ist `Microsoft.Jet.OLEDB.4.0`, und die Anbieterzeichenfolge lautet `Text`.  
  
 Die Datenquelle ist der vollständige Pfad des Verzeichnisses mit den Textdateien. Eine Datei namens schema.ini, die die Struktur der Textdateien beschreibt, muss im selben Verzeichnis wie die Textdateien vorhanden sein. Weitere Informationen zum Erstellen der Datei Schema.ini finden Sie in der Dokumentation zur Jet-Datenbank-Engine.  
  
```  
--Create a linked server.  
EXEC sp_addlinkedserver txtsrv, N'Jet 4.0',   
   N'Microsoft.Jet.OLEDB.4.0',  
   N'c:\data\distqry',  
   NULL,  
   N'Text';  
GO  
  
--Set up login mappings.  
EXEC sp_addlinkedsrvlogin txtsrv, FALSE, Admin, NULL;  
GO  
  
--List the tables in the linked server.  
EXEC sp_tables_ex txtsrv;  
GO  
  
--Query one of the tables: file1#txt  
--using a four-part name.   
SELECT *   
FROM txtsrv...[file1#txt];  
```  
  
### <a name="f-using-the-microsoft-ole-db-provider-for-db2"></a>F. Verwenden des Microsoft OLE DB-Anbieters für DB2  
 Im folgenden Beispiel wird der Verbindungsserver `DB2` erstellt, der `Microsoft OLE DB Provider for DB2` verwendet.  
  
```  
EXEC sp_addlinkedserver  
   @server=N'DB2',  
   @srvproduct=N'Microsoft OLE DB Provider for DB2',  
   @catalog=N'DB2',  
   @provider=N'DB2OLEDB',  
   @provstr=N'Initial Catalog=PUBS;  
       Data Source=DB2;  
       HostCCSID=1252;  
       Network Address=XYZ;  
       Network Port=50000;  
       Package Collection=admin;  
       Default Schema=admin;';  
```  
  
### <a name="g-add-a-includesssdsfullincludessssdsfull-mdmd-as-a-linked-server-for-use-with-distributed-queries-on-cloud-and-on-premise-databases"></a>G. Hinzufügen einer [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] als Verbindungsserver für verteilte Abfragen in lokalen Datenbanken und Clouddatenbanken  
 Sie können eine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] als Verbindungsserver hinzufügen und diesen dann für verteilte Abfragen verwenden, die lokale Datenbanken und Clouddatenbanken umfassen. Dies ist eine Komponente für hybride Datenbanklösungen, die sich auf lokale Unternehmensnetzwerke und die Windows Azure-Cloud erstrecken.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Produktpaket umfasst die verteilte Abfrage-Funktion, die Ihnen ermöglicht, Abfragen zum Kombinieren von Daten aus lokalen Datenquellen und Remotedatenquellen schreiben (einschließlich Daten aus nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellen) als Verbindungsserver definiert. Jede [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (außer der virtuellen Masterdatenbank) kann als einzelner Verbindungsserver hinzugefügt und wie jede andere Datenbank direkt in Datenbankanwendungen verwendet werden.  
  
 Die Vorteile der Verwendung einer [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] sind: Verwaltbarkeit, Hochverfügbarkeit, Skalierbarkeit, ein vertrautes Entwicklungsmodell sowie ein relationales Datenmodell. Auf welche Weise eine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] von Ihrer Datenbank in der Cloud verwendet wird, richtet sich nach den Anwendungsanforderungen. Sie können alle Daten gleichzeitig auf eine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] verschieben oder einige Daten stufenweise umlagern, während die übrigen Daten in der lokalen Umgebung verbleiben. Für eine derartige hybride Datenbankanwendung können [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]en jetzt als Verbindungsserver hinzugefügt werden, während die Datenbankanwendung verteilte Abfragen ausgeben kann, um Daten aus [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]en und lokalen Datenquellen zu kombinieren.  
  
 Hier ist ein einfaches Beispiel, das über das Herstellen einer Verbindung mit einem [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] Verwendung von verteilten Abfragen:  
  
```  
------ Configure the linked server  
-- Add one Windows Azure SQL DB as Linked Server  
EXEC sp_addlinkedserver  
@server='myLinkedServer', -- here you can specify the name of the linked server  
@srvproduct='',       
@provider='sqlncli', -- using SQL Server Native Client  
@datasrc='myServer.database.windows.net',   -- add here your server name  
@location='',  
@provstr='',  
@catalog='myDatabase'  -- add here your database name as initial catalog (you cannot connect to the master database)  
-- Add credentials and options to this linked server  
EXEC sp_addlinkedsrvlogin  
@rmtsrvname = 'myLinkedServer',  
@useself = 'false',  
@rmtuser = 'myLogin',             -- add here your login on Azure DB  
@rmtpassword = 'myPassword' -- add here your password on Azure DB  
EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;  
------ Now you can use the linked server to execute 4-part queries  
-- You can create a new table in the Azure DB  
exec ('CREATE TABLE t1tutut2(col1 int not null CONSTRAINT PK_col1 PRIMARY KEY CLUSTERED (col1) )') at myLinkedServer  
-- Insert data from your local SQL Server  
exec ('INSERT INTO t1tutut2 VALUES(1),(2),(3)') at myLinkedServer  
  
-- Query the data using 4-part names  
select * from myLinkedServer.myDatabase.dbo.myTable  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilte Abfragen, gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [sp_setnetname &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setnetname-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
