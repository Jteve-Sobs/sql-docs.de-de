---
title: char und varchar (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- varchar
- varchar_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fixed-length data types [SQL Server]
- character data type
- char data type
- varchar(max) data type
- variable-length data types [SQL Server]
- varchar data type
- utf8
ms.assetid: 282cd982-f4fb-4b22-b2df-9e8478f13f6a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d2f36af646ee1fb41279b8401c5e2bdf18ed6896
ms.sourcegitcommit: 96032813f6bf1cba680b5e46d82ae1f0f2da3d11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54299387"
---
# <a name="char-and-varchar-transact-sql"></a>char und varchar (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

> [!div class="nextstepaction"]
> [Senden Sie uns Ihr Feedback zum Inhaltsverzeichnis der SQL-Dokumentation!](https://aka.ms/sqldocsurvey)

Dieser Artikel beschreibt Zeichendatentypen, die entweder über eine feste Länge – **char** – oder über eine variable Länge – **varchar** – verfügen. Ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] gilt Folgendes: Wenn eine Sortierung mit aktiviertem UTF-8 verwendet wird, speichern diese Datentypen den gesamten Bereich der [Unicodezeichendaten](../../relational-databases/collations/collation-and-unicode-support.md#Unicode_Defn) und verwenden die Zeichencodierung [UTF-8](https://www.wikipedia.org/wiki/UTF-8). Wenn eine Sortierung ohne aktivierte UTF-8 angegeben wird, speichern diese Datentypen nur eine Teilmenge von Zeichen, die von der entsprechenden Codepage dieser Sortierung unterstützt wird.
  
## <a name="arguments"></a>Argumente  
**char** [ ( *n* ) ]: Zeichenfolgendaten mit fester Länge. *n* definiert die Zeichenfolgenlänge in Byte und muss ein Wert zwischen 1 bis 8.000 sein. Für Einzelbyte-Codierungszeichensätze wie *Latein* beträgt die Speichergröße *n* Byte, und die Anzahl von Zeichen, die gespeichert werden können, ist ebenfalls *n*. Für Multibyte-Codierungszeichensätze beträgt die Speichergröße noch *n* Byte, aber die Anzahl von Zeichen, die gespeichert werden können, ist ggf. kleiner als *n*. Das ISO-Synonym für **char** lautet **character**. Weitere Informationen zu Zeichensätzen finden Sie unter [Einzelbyte- und Mehrbyte-Zeichensätze](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets).

**varchar** [ ( *n* | **max** ) ]: Zeichenfolgendaten mit variabler Länge. *n* definiert die Zeichenfolgenlänge in Byte und ist ein Wert zwischen 1 bis 8.000. **max** gibt an, dass die maximale Speichergröße 2^31-1 Byte (2 GB) beträgt. Für Einzelbyte-Codierungszeichensätze wie *Latein* beträgt die Speichergröße *n* Byte + 2 Byte, und die Anzahl von Zeichen, die gespeichert werden können, ist ebenfalls *n*. Für Multibyte-Codierungszeichensätze beträgt die Speichergröße noch *n* Byte + 2 Byte, aber die Anzahl von Zeichen, die gespeichert werden können, ist ggf. kleiner als *n*. Die ISO-Synonyme für **varchar** lauten **charvarying** oder **charactervarying**. Weitere Informationen zu Zeichensätzen finden Sie unter [Einzelbyte- und Mehrbyte-Zeichensätze](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets).

## <a name="remarks"></a>Remarks  
Wenn *n* in einer Datendefinitions- oder Variablendeklarationsanweisung nicht angegeben ist, beträgt die Standardlänge 1. Wenn *n* für die Verwendung der CAST- und CONVERT-Funktionen nicht angegeben ist, beträgt die Standardlänge 30.
  
Objekten, die **char** oder **varchar** verwenden, wird die Standardsortierung der Datenbank zugewiesen, es sei denn, mithilfe der COLLATE-Klausel wird eine bestimmte Sortierung zugewiesen. Die Sortierung bestimmt die Codepage, die zum Speichern der Zeichendaten verwendet wird.

Multibyte-Codierungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfassen:
-   Doppelbyte-Zeichensätze (DBCS) für einige ostasiatische Sprachen mit Codepages 936 und 950 (Chinesisch), 932 (Japanisch) oder 949 (Koreanisch).
-   UTF-8 mit Codepage 65001. **Gilt für:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]))

Wenn Sie Websites haben, die mehrere Sprachen unterstützen:
- Ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] wird eine Sortierung mit aktiviertem UTF-8 empfohlen, um Unicode zu unterstützen und Probleme bei der Zeichenkonvertierung zu vermeiden. 
- Wenn Sie eine ältere Version von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verwenden, sollten Sie die Unicodedatentypen **nchar** oder **nvarchar** verwenden, um Probleme bei der Zeichenkonvertierung zu vermeiden.   

Wenn Sie **char** oder **varchar** verwenden, wird Folgendes empfohlen:
- Verwenden Sie **char**, wenn die Dateneinträge einer Spalte jeweils gleich lang sind.  
- Verwenden Sie **varchar**, wenn sich die Dateneinträge einer Spalte in ihrer Größe erheblich unterscheiden.  
- Verwenden Sie **varchar(max)**, wenn die Dateneinträge einer Spalte unterschiedlich lang sind, und die Zeichenfolgenlänge 8.000 Byte überschreitet.  
  
Wenn OFF für SET ANSI_PADDING festgelegt ist, während CREATE TABLE oder ALTER TABLE ausgeführt wird, wird eine als NULL definierte Spalte vom Typ **char** als **varchar** behandelt.
  
> [!WARNING]
> Jede varchar(max)- oder nvarchar(max)-Spalte, die ungleich NULL ist, erfordert 24 Byte an zusätzlicher fester Verteilung, die während eines Sortiervorgangs hinsichtlich des Zeilenlimits von 8.060 Byte gelten. Dies kann zur Erstellung einer impliziten Beschränkung der Anzahl der varchar(max)- oder nvarchar(max)-Spalten führen, die ungleich NULL sind und in einer Tabelle erstellt werden können.  
Beim Erstellen der Tabelle (außerhalb der üblichen Warnung darüber, dass die maximale Zeilengröße das zulässige Maximum von 8.060 Byte überschreitet) oder beim Einfügen der Daten wird kein spezieller Fehler ausgegeben. Diese große Zeilengröße kann während einiger normaler Vorgänge Fehler (z. B. Fehler 512) verursachen. Dazu gehören z. B. die Aktualisierung des gruppierten Indexschlüssels oder Teile des vollständigen Spaltensatzes. Bis zum Ausführen eines Vorgangs können Benutzer diese Fehler nicht vorhersehen.
  
##  <a name="_character"></a> Konvertieren von Zeichendaten  
Werden Zeichenausdrücke in einen Zeichendatentyp mit einer anderen Größe konvertiert, dann werden Werte, die für den neuen Datentyp zu lang sind, abgeschnitten. Der **uniqueidentifier** -Typ wird bei der Konvertierung von Zeichenausdrücken als Zeichentyp behandelt und unterliegt daher den Kürzungsregeln für die Konvertierung in einen Zeichentyp. Weitere Informationen finden Sie im Abschnitt "Beispiele" weiter unten.
  
Wenn ein Zeichenausdruck in einen Zeichenausdruck eines anderen Datentyps oder einer anderen Größe konvertiert wird (z.B. **char(5)** in **varchar(5)** oder **char(20)** in **char(15)**), wird die Sortierung des Eingabewerts dem konvertierten Wert zugewiesen. Wird ein Nichtzeichenausdruck zu einem Zeichendatentyp konvertiert, wird die Standardsortierung der aktuellen Datenbank dem konvertierten Wert zugewiesen. In beiden Fällen können Sie mithilfe der [COLLATE](../../t-sql/statements/collations.md)-Klausel auch eine bestimmte Sortierung zuweisen.
  
> [!NOTE]  
> Codepageübersetzungen werden für die Datentypen **char** und **varchar**, nicht jedoch für den **text**-Datentyp unterstützt. Wie auch bei früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird der Datenverlust während der Codepageübersetzung nicht gemeldet.  
  
Zeichenausdrücke, die in einen ungefähren **numerischen** Datentyp konvertiert werden, können die optionale Exponentialschreibweise enthalten (den Kleinbuchstaben e oder den Großbuchstaben E, auf den ein optionales Plus- (+) oder Minuszeichen (-) und dann eine Zahl folgt).
  
Zeichenausdrücke, die in einen exakten **numerischen** Datentyp konvertiert werden, müssen aus Ziffern, einem Dezimaltrennzeichen und einem optionalen Plus- (+) oder Minuszeichen (-) zusammengesetzt sein. Führende Leerzeichen werden ignoriert. Kommas als Trennzeichen (z. B. das Trennzeichen in 123.456,00) sind in der Zeichenfolge nicht zulässig.
  
Zeichenausdrücke, die in die Datentypen **money** oder **smallmoney** konvertiert werden, können außerdem ein optionales Dezimaltrennzeichen und ein Dollarzeichen ($) enthalten. Kommas als Trennzeichen (wie in 123.456,00 $) sind zulässig.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-showing-the-default-value-of-n-when-used-in-variable-declaration"></a>A. Anzeigen des Standardwerts von n bei Verwendung in einer Variablendeklaration.  
Das folgende Beispiel zeigt, dass der Standardwert von *n* für die Datentypen `char` und `varchar` 1 ist, wenn diese in einer Variablendeklaration verwendet werden.
  
```sql
DECLARE @myVariable AS varchar = 'abc';  
DECLARE @myNextVariable AS char = 'abc';  
--The following returns 1  
SELECT DATALENGTH(@myVariable), DATALENGTH(@myNextVariable);  
GO  
```  
  
### <a name="b-showing-the-default-value-of-n-when-varchar-is-used-with-cast-and-convert"></a>B. Anzeigen des Standardwerts von n, wenn varchar mit CAST und CONVERT verwendet wird.  
Das folgende Beispiel zeigt, dass 30 der Standardwert von *n* ist, wenn der Datentyp `char` oder `varchar` in den Funktionen `CAST` und `CONVERT` verwendet wird.
  
```sql
DECLARE @myVariable AS varchar(40);  
SET @myVariable = 'This string is longer than thirty characters';  
SELECT CAST(@myVariable AS varchar);  
SELECT DATALENGTH(CAST(@myVariable AS varchar)) AS 'VarcharDefaultLength';  
SELECT CONVERT(char, @myVariable);  
SELECT DATALENGTH(CONVERT(char, @myVariable)) AS 'VarcharDefaultLength';  
```  
  
### <a name="c-converting-data-for-display-purposes"></a>C. Konvertieren von Daten zu Anzeigezwecken  
Im folgenden Beispiel werden zwei Spalten in Zeichentypen konvertiert und ein bestimmtes Format auf die angezeigten Daten angewendet. Ein **money**-Typ wird in Zeichendaten konvertiert, und das Format 1 wird angewendet. Bei diesem werden für die Werte zwei Ziffern rechts vom Dezimalpunkt und links vom Dezimalpunkt nach jeder dritten Ziffer ein Trennzeichen angezeigt. Ein **datetime**-Typ wird in Zeichendaten konvertiert, und das Format 3 wird angewendet, durch das die Daten im Format dd/mm/yy anzeigt werden. In der WHERE-Klausel wird ein **money**-Typ in einen Zeichentyp umgewandelt, um einen Vergleichsvorgang für die Zeichenfolgen ausführen zu können.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT  BusinessEntityID,   
   SalesYTD,   
   CONVERT (varchar(12),SalesYTD,1) AS MoneyDisplayStyle1,   
   GETDATE() AS CurrentDate,   
   CONVERT(varchar(12), GETDATE(), 3) AS DateDisplayStyle3  
FROM Sales.SalesPerson  
WHERE CAST(SalesYTD AS varchar(20) ) LIKE '1%';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
BusinessEntityID SalesYTD              DisplayFormat CurrentDate             DisplayDateFormat  
---------------- --------------------- ------------- ----------------------- -----------------  
278              1453719.4653          1,453,719.47  2011-05-07 14:29:01.193 07/05/11  
280              1352577.1325          1,352,577.13  2011-05-07 14:29:01.193 07/05/11  
283              1573012.9383          1,573,012.94  2011-05-07 14:29:01.193 07/05/11  
284              1576562.1966          1,576,562.20  2011-05-07 14:29:01.193 07/05/11  
285              172524.4512           172,524.45    2011-05-07 14:29:01.193 07/05/11  
286              1421810.9242          1,421,810.92  2011-05-07 14:29:01.193 07/05/11  
288              1827066.7118          1,827,066.71  2011-05-07 14:29:01.193 07/05/11  
```  
  
### <a name="d-converting-uniqueidentifer-data"></a>D. Konvertieren von uniqueidentifier-Daten  
Das folgende Beispiel konvertiert einen `uniqueidentifier` -Wert in einen `char` -Datentyp.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
Im folgenden Beispiel wird das Abschneiden von Daten veranschaulicht, wenn der Wert zu lang für den Datentyp ist, in den er konvertiert wird. Da der **uniqueidentifier** -Typ auf 36 Zeichen beschränkt ist, werden die Zeichen, die diese Länge überschreiten, abgeschnitten.
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Siehe auch
[nchar und nvarchar &#40;Transact-SQL&#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[COLLATE &#40;Transact-SQL&#41;](../../t-sql/statements/collations.md)  
[Datentypkonvertierung &#40;Datenbank-Engine&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Schätzen der Größe einer Datenbank](../../relational-databases/databases/estimate-the-size-of-a-database.md)     
[Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md)    
[Einzelbyte- und Mehrbyte-Zeichensätze](/cpp/c-runtime-library/single-byte-and-multibyte-character-sets)
  
