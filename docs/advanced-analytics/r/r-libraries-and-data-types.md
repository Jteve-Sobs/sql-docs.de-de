---
title: R-an-SQL-datentypkonvertierungen – SQL Server Machine Learning Services
description: Überprüfen Sie die Converstions Typ implizite und explizite Daten zwischen R und SQL Server in Data Science und Machine learning-Lösungen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 79570a1479078234328a17d4de2a12c821c76f3d
ms.sourcegitcommit: e2d65828faed6f4dfe625749a3b759af9caa7d91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59671116"
---
# <a name="data-type-mappings-between-r-and-sql-server"></a>Geben Sie datentypzuordnungen zwischen R und SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Überprüfen Sie für R-Lösungen, die auf die Funktion für die R-Integration in SQL Server-Machine Learning-Dienste ausgeführt werden die Liste der nicht unterstützten Datentypen und datentypkonvertierungen, die möglicherweise implizit durchgeführt werden, wenn Daten zwischen R-Bibliotheken und SQL Server übergeben werden.

## <a name="base-r-version"></a>Basis-R-version

SQL Server 2016 R Services und SQL Server 2017 Machine Learning Services mit R, werden mit bestimmten Versionen von Microsoft R Open ausgerichtet. Die neueste Version, SQL Server 2017 Machine Learning Services basiert beispielsweise auf Microsoft R Open 3.3.3.

Öffnen Sie zum Anzeigen der R-Version, die mit einer bestimmten Instanz von SQL Server verknüpften **RGui**. Für die Standardinstanz wäre der Pfad wie folgt: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64\`

Das Tool lädt die Basis-R und andere Bibliotheken. Paketinformationen-Version wird in einer Benachrichtigung für jedes Paket bereitgestellt, die beim sitzungsstart geladen wird. 

## <a name="r-and-sql-data-types"></a>R und SQL-Datentypen

Während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt mehrere Dutzend verschiedene Datentypen, R verfügt über eine begrenzte Anzahl von skalaren Datentypen (numerisch, komplex, logisch, Zeichen, ganze Zahl Datum/Uhrzeit und Rohdaten). Jedes Mal, wenn Sie daher Daten aus verwenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in R-Skripts Daten können implizit konvertiert werden in einen kompatiblen Datentyp. Allerdings häufig eine exakte Konvertierung nicht automatisch durchgeführt werden, und ein Fehler zurückgegeben wird, wie z. B. "Unbehandelter SQL-Datentyp".

Dieser Abschnitt enthält die implizite Konvertierungen, die bereitgestellt werden, und nicht unterstützten Datentypen aufgeführt. Einige Anleitungen für die Zuordnung von Datentypen zwischen R und SQL Server enthalten.

## <a name="implicit-data-type-conversions-between-r-and-sql-server"></a>Implizite Datentypenkonvertierung zwischen R und SQL Server

Die folgende Tabelle zeigt die Änderungen der Datentypen und Werte an, wenn Daten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einem R-Skript verwendet und anschließend an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurückgegeben werden.

|SQL-Typ|R-Klasse|Resultsettyp|Kommentare|
|-|-|-|-|
|**bigint**|`numeric`|**float**||
|**binary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Nur als Eingabeparameter und als Ausgabe zulässig|
|**bit**|`logical`|**bit**||
|**char(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||
|**datetime**|`POSIXct`|**datetime**|Dargestellt als GMT|
|**Datum**|`POSIXct`|**datetime**|Dargestellt als GMT|
|**decimal(p,s)**|`numeric`|**float**||
|**float**|`numeric`|**float**||
|**int**|`integer`|**int**||
|**money**|`numeric`|**float**||
|**numeric(p,s)**|`numeric`|**float**||
|**real**|`numeric`|**float**||
|**smalldatetime**|`POSIXct`|**datetime**|Dargestellt als GMT|
|**smallint**|`integer`|**int**||
|**smallmoney**|`numeric`|**float**||
|**tinyint**|`integer`|**int**||
|**uniqueidentifier**|`character`|**varchar(max)**||
|**varbinary(n)**<br /><br /> n <= 8000|`raw`|**varbinary(max)**|Nur als Eingabeparameter und als Ausgabe zulässig|
|**varbinary(max)**|`raw`|**varbinary(max)**|Nur als Eingabeparameter und als Ausgabe zulässig|
|**varchar(n)**<br /><br /> n <= 8000|`character`|**varchar(max)**||


## <a name="data-types-not-supported-by-r"></a>Von R nicht unterstützte Datentypen

Folgende Typen von Datentypkategorien, die vom [Typsystem von SQL Server](../../t-sql/data-types/data-types-transact-sql.md) unterstützt werden, verursachen möglicherweise Probleme, wenn Sie an R-Code übergeben werden:

+ Datentypen in der **andere** Abschnitt des Artikels System Typ SQL: **Cursor**, **Zeitstempel**, **Hierarchyid**,  **Uniqueidentifier**, **Sql_variant**, **Xml**, **Tabelle**
+ Alle räumlichen Typen
+ **image**

## <a name="data-types-that-might-convert-poorly"></a>Datentypen, die möglicherweise schlecht konvertiert werden

+ Die meisten Datum-/Zeittypen sollten funktionieren; nur **dattimeoffset** funktioniert nicht 
+ Die meisten numerischen Datentypen werden unterstützt; allerdings schlagen Konvertierungen von **money** und **smallmoney** möglicherweise fehl
+ **varchar** wird unterstützt; da jedoch SQL Server grundsätzlich Unicode verwendet, wird empfohlen, wenn möglich **nvarchar** und andere Unicode-Textdatentypen zu verwenden.
+ Funktionen aus der RevoScaleR-Bibliothek können mit dem Präfix „rx“ versehen werden, um die binären SQL-Datentypen (**binary** und **varbinary**) zu behandeln; in den meisten Szenarios ist für diese Typen jedoch eine spezielle Behandlung vonnöten. In den meisten Fällen funktioniert R-Code nicht mit binären Spalten.

  
 Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)

## <a name="changes-in-data-types-between-sql-server-2016-and-earlier-versions"></a>Was sich bei Datentypen in SQL Server 2016 im Vergleich zu früheren Versionen geändert hat

Microsoft SQL Server 2016 und Microsoft Azure SQL Database kommen mit Verbesserungen bei der Datentypkonvertierung und bei mehreren anderen Vorgängen. Die meisten dieser Verbesserungen tragen zu einer verbesserten Genauigkeit beim Arbeiten mit Gleitkommatypen bei; außerdem gibt es kleine Änderungen bei Vorgängen mit herkömmlichen **datetime**-Typen.

Diese Verbesserungen stehen Ihnen standardmäßig zur Verfügung, wenn Sie einen Datenbankkompatibilitätsgrad von 130 oder höher verwenden. Wenn Sie allerdings einen anderen Kompatibilitätsgrad verwenden oder über eine ältere Version mit der Datenbank verbunden sind, sehen Sie möglicherweise Unterschiede in der Genauigkeit von Zahlen oder anderen Ergebnissen. 

Weitere Informationen finden Sie unter [SQL Server 2016 improvements in handling some data types and uncommon operations (Verbesserungen der Behandlung einiger Datentypen und seltener Vorgänge in SQL Server 2016)](https://support.microsoft.com/help/4010261/sql-server-2016-improvements-in-handling-some-data-types-and-uncommon-).
 

## <a name="verify-r-and-sql-data-schemas-in-advance"></a>Überprüfen R- und SQL-Datenschemas im Voraus 

Im Allgemeinen ist es empfehlenswert, die  `str()` -Funktion zu verwenden, um die interne Struktur und den Typ des R-Objekts zu erhalten, wenn Sie nicht wissen, wie ein spezieller Datentyp oder eine Datenstruktur in R verwendet wird. Das Ergebnis der Funktion wird in die R-Konsole gedruckt, und ist auch in den Abfrageergebnissen verfügbar, in der Registerkarte **Meldungen** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. 

Beim Abrufen von Daten aus einer Datenbank für die Verwendung in R-Code sollten Sie immer entfernt werden Spalten, die in R verwendet werden können, sowie Spalten, die nicht hilfreich bei der Analyse, z. B. GUIDS (Uniqueidentifier), Zeitstempel und andere Spalten, die zum Überwachen, oder die Herkunfts- Informationen, die von ETL-Prozesse erstellt werden. 

Beachten Sie, dass die Leistung von R-Code durch unnötige Spalten deutlich beeinträchtigt werden kann, besonders dann, wenn Spalten mit hoher Kardinalität als Faktoren verwendet werden. Aus diesem Grund wird empfohlen, im System gespeicherte Prozeduren von SQL Server und Informationsansichten zu verwenden, um die Datentypen für eine angegebene Tabelle im Voraus abzurufen und inkompatible Spalten entweder zu löschen oder zu konvertieren. Weitere Informationen finden Sie unter [Information Schema Views in Transact-SQL (Ansichten des Informationsschemas in Transact-SQL)](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)

Falls ein bestimmter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp in R nicht unterstützt wird, Sie aber die Datenspalten im R-Skript verwenden müssen, empfehlen wir Ihnen, die Funktionen [„Cast“ und „Convert“ &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md) zu verwenden, um sicherzustellen, dass die Datentypenkonvertierungen wie gewünscht ausgeführt werden, bevor Sie die Daten in Ihrem R-Skript verwenden.  

> [!WARNING]
> Wenn Sie **rxDataStep** verwenden, um inkompatible Spalten beim Verschieben von Daten fallen zu lassen, denken Sie daran, dass die Argumente _varsToKeep_ und _varsToDrop_ für den Datenquelltyp **RxSqlServerData** nicht unterstützt werden.


## <a name="examples"></a>Beispiele

### <a name="example-1-implicit-conversion"></a>Beispiel 1: Implizite Konvertierung

In folgendem Beispiel wird veranschaulicht, wie Daten auf dem Weg zwischen SQL Server und R umgewandelt werden.

Die Abfrage ruft eine Reihe von Werten aus einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle, und verwendet die gespeicherte Prozedur [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) um die Werte, die mithilfe der R-Laufzeitumgebung auszugeben.

```sql
CREATE TABLE MyTable (    
 c1 int,    
 c2 varchar(10),    
 c3 uniqueidentifier    
);    
go    
INSERT MyTable VALUES(1, 'Hello', newid());    
INSERT MyTable VALUES(-11, 'world', newid());    
SELECT * FROM MyTable;    
  
EXECUTE sp_execute_external_script    
 @language = N'R'    
 , @script = N'    
inputDataSet["cR"] <- c(4, 2)    
str(inputDataSet)    
outputDataSet <- inputDataSet'    
 , @input_data_1 = N'SELECT c1, c2, c3 FROM MyTable'    
 , @input_data_1_name = N'inputDataSet'    
 , @output_data_1_name = N'outputDataSet'    
 WITH RESULT SETS((C1 int, C2 varchar(max), C3 varchar(max), C4 float));  
```

**Ergebnisse**

||||||
|-|-|-|-|-|
||C1|C2|C3|C4|
|1|1|Hello|6e225611-4b58-4995-a0a5-554d19012ef1|4|
|1|-11|world|6732ea46-2d5d-430b-8ao1-86e7f3351c3e|2|

Beachten Sie die Verwendung der `str` -Funktion in R, um das Schema der Ausgabedaten zu erhalten. Diese Funktion gibt die folgenden Informationen zurück:

<code>'data.frame':2 obs. of  4 variables:</code>
<code> $ c1: int  1 -11</code>
<code> $ c2: Factor w/ 2 levels "Hello","world": 1 2</code>
<code> $ c3: Factor w/ 2 levels "6732EA46-2D5D-430B-8A01-86E7F3351C3E",..: 2 1</code>
<code> $ cR: num  4 2</code>

Daraus können Sie erkennen, dass die folgenden Datentypenkonvertierungen implizit als Teil der Abfrage durchgeführt wurden:

-   **Spalte C1**. Die Spalte wird in **ssNoversion** als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in R als `integer` und im Ausgaberesultset als **ssNoversion** dargestellt.  
  
     Es wurde keine Typenkonvertierung durchgeführt.  
  
-   **Spalte C2**. Die Spalte wird in **ssNoversion** als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in R als `factor` und im Ausgaberesultset als **varchar(max)** dargestellt.  
  
     Beachten Sie, wie sich die Ausgabe ändert; jede Zeichenfolge von R (entweder ein Faktor oder eine reguläre Zeichenfolge) wird als **varchar(max)** dargestellt, unabhängig von der Länge der Zeichenfolge.  
  
-   **Spalte C3**.  Die Spalte wird in **ssNoversion** als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in R als `character` und im Ausgaberesultset als **varchar(max)** dargestellt.
  
     Beachten Sie die ausgeführte Datentypenkonvertierung. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt den **ssNoversion** , R jedoch nicht; daher werden die Bezeichner als Zeichenfolgen dargestellt.
  
-   **Spalte C4**. Die Spalte enthält Werte, die vom R-Skript generiert wurden und die in den ursprünglichen Daten nicht vorhanden waren.


## <a name="example-2-dynamic-column-selection-using-r"></a>Beispiel 2: Dynamische Spaltenauswahl mithilfe von R

Im folgenden Beispiel wird veranschaulicht, wie Sie R-Code zum Prüfen auf ungültige Spaltentypen verwenden können. Der R-Code ruft das Schema der angegebenen Tabelle mithilfe der Systemsichten von SQL Server ab und entfernt alle Spalten, die einen angegebenen ungültigen Typen aufweisen.

```R
connStr <- "Server=.;Database=TestDB;Trusted_Connection=Yes"
data <- RxSqlServerData(connectionString = connStr, sqlQuery = "SELECT COLUMN_NAME FROM TestDB.INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = N'testdata' AND DATA_TYPE <> 'image';")
columns <- rxImport(data)
columnList <- do.call(paste, c(as.list(columns$COLUMN_NAME), sep = ","))
sqlQuery <- paste("SELECT", columnList, "FROM testdata")
```

## <a name="see-also"></a>Siehe auch

