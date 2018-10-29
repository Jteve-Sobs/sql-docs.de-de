---
title: DAX-Formelkompatibilität im DirectQuery-Modus (SSAS 2014) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
ms.topic: conceptual
ms.assetid: de83cfa9-9ffe-4e24-9c74-96a3876cb4bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 61018db803a8459f10fc6cb0bf49c89dd9c685ed
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100321"
---
# <a name="dax-formula-compatibility-in-directquery-mode-ssas-2014"></a>DAX-Formelkompatibilität im DirectQuery-Modus (SSAS 2014)
Die Programmiersprache Data Analysis Expression (DAX) dienen zum Erstellen von Measures und andere benutzerdefinierten Formeln für die Verwendung in Analysis Services-tabellenmodellen, [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Datenmodellen in Excel-Arbeitsmappen und Datenmodellen für Power BI Desktop. In den meisten Punkten, die Modelle, die Sie in diesen Umgebungen erstellen, identisch sind und können Sie die gleichen Measures, Beziehungen und KPIs usw. Wenn Sie ein tabellarisches Analysis Services-Modell erstellen und es im DirectQuery-Modus bereitstellen, gibt es jedoch einige Einschränkungen für die Formeln, die Sie verwenden können. Dieses Thema bietet einen Überblick über diese Unterschiede, listet die Funktionen, die nicht in SQL Server 2014 Analysis Services-Tabulars-Modell mit Kompatibilitätsgrad 1100 oder 1103 und im DirectQuery-Modus unterstützt werden und listet die Funktionen, die unterstützt werden aber möglicherweise andere Ergebnisse zurückgeben.  
  
In diesem Thema verwenden wir den Begriff *im Arbeitsspeicher gespeicherten Modells* zum Verweisen auf tabellarische Modelle die vollständig werden im Arbeitsspeicher zwischengespeicherte Daten auf einer im tabellarischen Modus ausgeführten Analysis Services-Server gehostet. Wir verwenden *DirectQuery-Modelle* für tabellarische Modelle zu verweisen, die im DirectQuery-Modus bereitgestellt und/oder erstellt wurden. Weitere Informationen zum DirectQuery-Modus finden Sie unter [DirectQuery-Modus (SSAS – tabellarisch)](http://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5).  
  
  
## <a name="bkmk_SemanticDifferences"></a>Unterschiede zwischen dem speicherinternen und DirectQuery-Modus  
Abfragen eines Modells, das im DirectQuery-Modus bereitgestellt wird, können andere Ergebnisse zurückgeben als bei der Bereitstellung desselben Modells im Arbeitsspeicher. Dies ist, da mit DirectQuery, Daten direkt aus einem relationalen Datenspeicher abgerufen und für Formeln erforderliche Aggregationen mithilfe der relevanten relationalen Engine, anstatt die xVelocity-in-Memory-Analyse-Engine (VertiPaq) für den Speicher ausgeführt werden und Berechnung.  
  
Beispielsweise behandeln bestimmte relationale Datenspeicher numerische Werte, Daten, NULL-Werte usw. auf unterschiedliche Weise.  
  
Im Gegensatz dazu dient die DAX-Programmiersprache zum möglichst genauen Emulieren des Verhaltens von Funktionen in Microsoft Excel. Beispielsweise versucht Excel bei der Behandlung von NULL-Werten, leeren Zeichenfolgen und Werten gleich 0 unabhängig vom genauen Datentyp die optimale Antwort bereitzustellen. Folglich verhält sich die xVelocity-Engine auf die gleiche Weise. Wird jedoch ein Tabellenmodell im DirectQuery-Modus bereitgestellt und übergibt es Formeln an eine relationale Datenquelle zur Auswertung, müssen die Daten gemäß der Semantik der relationalen Datenquelle behandelt werden. Dabei werden in der Regel leere Zeichenfolgen anders behandelt als NULL-Zeichenfolgen. Aus diesem Grund kann die gleiche Formel ein anderes Ergebnis zurückgeben als im Fall der Auswertung anhand von zwischengespeicherten Daten sowie Daten, die lediglich aus dem relationalen Speicher zurückgegeben wurden.  
  
Darüber hinaus können nicht einige Funktionen auf allen im DirectQuery-Modus verwendet werden, da die Berechnung erfordern würde, die Daten im aktuellen Kontext an die relationale Datenquelle als Parameter gesendet werden. Misst z. B. einem [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Arbeitsmappe verwenden häufig die Verwendung von zeitintelligenzfunktionen, die innerhalb der Arbeitsmappe verfügbare Datumsbereiche verweisen. Derartige Formeln können im Allgemeinen nicht im DirectQuery-Modus verwendet werden.  
  
## <a name="semantic-differences"></a>Semantische Unterschiede  
Dieser Abschnitt listet die Typen der üblichen semantischen Unterschiede auf. Zudem werden Einschränkungen beschrieben, die u. U. für die Verwendung von Funktionen oder für Abfrageergebnisse gelten.  
  
### <a name="bkmk_Comparisons"></a>Vergleiche  
Die DAX-Programmiersprache in speicherinternen Modellen unterstützt Vergleiche von zwei Ausdrücken, die in Skalarwerte verschiedener Datentypen aufgelöst werden. Modelle, die im DirectQuery-Modus bereitgestellt werden, verwenden jedoch die Datentypen und Vergleichsoperatoren der relationalen Engine und geben daher u. U. unterschiedliche Ergebnisse zurück.  
  
Die folgenden Vergleiche geben immer einen Fehler zurück, wenn sie in einer Berechnung in einer DirectQuery-Datenquelle verwendet werden:  
  
-   Numerischer Datentyp im Vergleich zu einem Zeichenfolgen-Datentyp  
  
-   Numerischer Datentyp im Vergleich zu einem booleschen Wert  
  
-   Zeichenfolgen-Datentyp im Vergleich zu einem booleschen Wert  
  
Im Allgemeinen toleriert die DAX-Programmiersprache mehr Datentypkonflikte in speicherinternen Modellen und versucht bis zu zweimal, eine implizite Umwandlung von Werten durchzuführen (wie in diesem Abschnitt beschrieben). An einen relationalen Datenspeicher im DirectQuery-Modus gesendete Formeln werden jedoch strenger ausgewertet, wobei die Regeln der relationalen Engine berücksichtigt werden und mit höherer Wahrscheinlichkeit ein Fehlschlag auftritt.  
  
**Vergleiche von Zeichenfolgen und Zahlen**  
BEISPIEL: `“2” < 3`  
  
Die Formel vergleicht eine Textzeichenfolge mit einer Zahl. Der Ausdruck ist sowohl bei Modellen im DirectQuery-Modus als auch bei speicherinternen Modellen **true** .  
  
Bei einem speicherinternen Modell lautet das Ergebnis **true** , da Zahlen als Zeichenfolgen implizit in einen numerischen Datentyp für Vergleiche mit anderen Zahlen umgewandelt werden. SQL wandelt auch Textzahlen implizit in Zahlen für den Vergleich mit numerischen Datentypen um.  
  
Beachten Sie, dass dies eine Änderung des Verhaltens von der ersten Version von [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]darstellt, die **false**zurückgeben würde, da der Text „2“ stets im Vergleich zu einer Zahl als größer betrachtet wird.  
  
**Vergleich von Text mit booleschen Werten**  
BEISPIEL: `“VERDADERO” = TRUE`  
  
Dieser Ausdruck vergleicht eine Textzeichenfolge mit einem booleschen Wert. Im Allgemeinen führt der Vergleich von einem Zeichenfolgenwert mit einem booleschen Wert bei DirectQuery-Modellen bzw. speicherinternen Modellen zu einem Fehler. Diese Regel gilt jedoch nicht, wenn die Zeichenfolge das Wort **true** oder **false**enthält. Wenn die Zeichenfolge Werte des Typs „true“ oder „false“ enthält, erfolgt eine Umwandlung in einen booleschen Wert. Daraufhin wird der Vergleich ausgeführt und ein logisches Ergebnis zurückgegeben.  
  
**Vergleich von NULL-Werten**  
BEISPIEL: `EVALUATE ROW("X", BLANK() = BLANK())`  
  
Diese Formel vergleicht die SQL-Entsprechung eines NULL-Werts mit einem NULL-Wert. Sie gibt für speicherinterne Modelle sowie DirectQuery-Modelle **true** zurück. Eine Bereitstellung erfolgt im DirectQuery-Modell, um ein ähnliches Verhalten beim speicherinternen Modell zu gewährleisten.  
  
Beachten Sie, dass ein NULL-Wert in Transact-SQL niemals gleich einem NULL-Wert ist. In der DAX-Programmiersprache jedoch ist ein Leerzeichen gleich einem anderen Leerzeichen. Dieses Verhalten gilt für alle speicherinternen Modelle. Im DirectQuery-Modus wird hauptsächlich die Semantik von SQL Server verwendet. In diesem Fall wird jedoch von der Semantik abgewichen, indem ein neues Verhalten für Vergleiche von NULL-Werten verwendet wird.  
  
### <a name="bkmk_Casts"></a>Typumwandlungen  
  
Es gibt in der DAX-Programmiersprache keine Umwandlungsfunktion als solche, aber implizite Umwandlungen werden bei vielen Vergleichsvorgängen sowie arithmetischen Vorgängen ausgeführt. Anhand des Vergleichsvorgangs bzw. arithmetischen Vorgangs wird der Datentyp des Ergebnisses bestimmt. Beispiel:  
  
-   Boolesche Werte werden bei arithmetischen Vorgängen als numerisch betrachtet, beispielsweise als TRUE + 1. Alternativ wird die Funktion MIN für eine Spalte mit booleschen Werten angewendet. Ein NOT-Vorgang gibt ebenfalls einen numerischen Wert zurück.  
  
-   Boolesche Werte werden stets als logische Werte in Vergleichen sowie bei Verwendung mit EXACT, AND, OR, &amp;&amp;oder || betrachtet.  
  
**Umwandeln einer Zeichenfolge in einen booleschen Wert**  
Bei speicherinternen Modellen sowie DirectQuery-Modellen sind Umwandlungen in boolesche Werte nur bei folgenden Zeichenfolgen zulässig: **""** (leere Zeichenfolge), **true**, **false**. Dabei wird eine leere Zeichenfolge in einen FALSE-Wert umgewandelt.  
  
Umwandlungen anderer Zeichenfolgen in den booleschen Datentyp führen zu einem Fehler.  
  
**Umwandeln einer Zeichenfolge in ein Datum/eine Uhrzeit**  
Umwandlungen von Zeichenfolgendarstellungen für Daten und Uhrzeiten in tatsächliche **datetime** -Werte verhalten sich im DirectQuery-Modus auf die gleiche Weise wie bei SQL Server.  
  
Informationen zu den Regeln für Umwandlungen von Zeichenfolgen in **"DateTime"** Datentypen in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Modellen finden Sie unter den [Syntaxreferenz für DAX](https://msdn.microsoft.com/library/ee634217.aspx).  
  
Modelle, die den speicherinternen Datenspeicher verwenden, unterstützen weniger Textformate für Datumsangaben als die entsprechenden von SQL Server unterstützten Zeichenfolgenformate. Die DAX-Programmiersprache unterstützt jedoch benutzerdefinierte Datums- und Uhrzeitformate.  
  
**Umwandeln von Zeichenfolgen in andere nicht-boolesche Werte**  
Bei der Umwandlung von Zeichenfolgen in nicht-boolesche Werte verhält sich der DirectQuery-Modus auf die gleiche Weise wie SQL Server. Weitere Informationen finden Sie unter [CAST und CONVERT (Transact-SQL)](http://msdn.microsoft.com/a87d0850-c670-4720-9ad5-6f5a22343ea8).  
  
**Umwandlung von Zahlen in Zeichenfolgen nicht zulässig**  
BEISPIEL: `CONCATENATE(102,”,345”)`  
  
Die Umwandlung von Zahlen in Zeichenfolgen ist bei SQL Server nicht zulässig.  
  
Diese Formel gibt einen Fehler in Tabellenmodellen und im DirectQuery-Modus zurück. Die Formel erzeugt allerdings in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]ein Ergebnis.  
  
**Keine Unterstützung für Umwandlungen mit zwei Versuchen in DirectQuery**  
Bei speicherinternen Modellen erfolgt oftmals ein zweiter Umwandlungsversuch, wenn der erste fehlgeschlagen ist. Dies geschieht nicht im DirectQuery-Modus.  
  
BEISPIEL: `TODAY() + “13:14:15”`  
  
In diesem Ausdruck weist der erste Parameter den Typ **datetime** und der zweite Parameter den Typ **string**auf. Die Umwandlungen werden jedoch im Fall der Kombination der Operanden unterschiedlich gehandhabt. DAX führt eine implizite Umwandlung von **string** in **double**aus. Bei speicherinternen Modellen versucht die Formel-Engine, eine direkte Umwandlung in **double** vorzunehmen. Missling dieser Vorgang, wird versucht, die Zeichenfolge in **datetime** umzuwandeln.  
  
Im DirectQuery-Modus wird nur die direkte Umwandlung von **string** in **double** übernommen. Schlägt diese Umwandlung fehl, gibt die Formel einen Fehler zurück.  
  
### <a name="bkmk_Math"></a>Mathematische Funktionen und arithmetische Vorgänge  
Einige mathematische Funktionen geben im DirectQuery-Modus andere Ergebnisse zurück. Dies ist auf Unterschiede des zugrunde liegenden Datentyps oder der Umwandlungen zurückzuführen, die in Vorgängen übernommen werden können. Zudem können sich die zuvor beschriebenen Einschränkungen der zulässigen Werte auf das Ergebnis von arithmetischen Vorgängen auswirken.  
  
**Reihenfolge der Hinzufügung**  
Wenn Sie eine Formel erstellen, die eine Reihe von Zahlen hinzufügt, verarbeitet ein speicherinternes Modell die Zahlen u. U. in einer anderen Reihenfolge als ein DirectQuery-Modell.  Liegen demnach viele sehr hohe positive Zahlen und sehr hohe negative Zahlen vor, wird möglicherweise ein Fehler in einem Vorgang zurückgegeben, und ein weiterer Vorgang wird ausgelöst.  
  
**Verwendung der POWER-Funktion**  
BEISPIEL: `POWER(-64, 1/3)`  
  
Im DirectQuery-Modus kann die POWER-Funktion keine negativen Werte als Basis für Berechnungen mit Bruchexponenten verwenden. Dies ist das erwartete Verhalten in SQL Server.  
  
Bei einem speicherinternen Modell gibt die Formel den Wert "-4" zurück.  
  
**Numerische Überlaufvorgänge**  
In Transact-SQL geben Vorgänge, die zu einem numerischen Überlauf führen, einen Überlauffehler zurück. Daher geben auch Formeln, die zu einem Überlauf führen, einen Fehler im DirectQuery-Modus zurück.  
  
Die gleiche Formel gibt allerdings bei Verwendung in einem speicherinternen Modell eine ganze Zahl mit einer Länge von acht Byte zurück. Das liegt daran, dass die Formel-Engine keine Überprüfungen für numerische Überläufe ausführt.  
  
**LOG-Funktionen mit Leerzeichen geben andere Ergebnisse zurück.**  
SQL Server behandelt NULL-Werte und Leerzeichen anders als die xVelocity-Engine. Daher gibt die folgende Formel einen Fehler im DirectQuery-Modus zurück, während sie beim speicherinternen Modell den Unendlichkeitswert (–inf) zurückgibt.  
  
`EXAMPLE: LOG(blank())`  
  
Die gleichen Einschränkungen gelten für die anderen logarithmischen Funktionen: LOG10 und LN.  
  
Weitere Informationen zum **blank** -Datentyp in der DAX-Programmiersprache finden Sie in der [DAX-Syntaxspezifikation für PowerPivot](https://msdn.microsoft.com/library/ee634217.aspx).  
  
**Division durch 0 und Division durch Leerzeichen**  
Im DirectQuery-Modus führt die Division durch null (0) bzw. die Division durch BLANK stets zu einem Fehler. SQL Server unterstützt nicht die Definition der Unendlichkeit, und da das natürliche Ergebnis jeder Division durch 0 die Unendlichkeit ist, entspricht das Ergebnis einem Fehler. SQL Server unterstützt jedoch die Division durch NULL-Werte, und das Ergebnis muss stets einem NULL-Wert entsprechen.  
  
Anstelle der Rückgabe unterschiedlicher Ergebnisse für diese Vorgänge geben beide Vorgangstypen (Division durch null und Division durch einen NULL-Wert) im DirectQuery-Modus einen Fehler zurück.  
  
Beachten Sie, dass die Division durch 0 in Excel und in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] -Modellen auch einen Fehler zurückgibt. Die Division durch ein Leerzeichen gibt ein Leerzeichen zurück.  
  
Die folgenden Ausdrücke sind in speicherinternen Modellen gültig, schlagen jedoch im DirectQuery-Modus fehl:  
  
`1/BLANK`  
  
`1/0`  
  
`0.0/BLANK`  
  
`0/0`  
  
Der Ausdruck `BLANK/BLANK` ist ein besonderer Fall, der `BLANK` sowohl in speicherinternen Modellen als auch im DirectQuery-Modus zurückgibt.  
  
### <a name="bkmk_Ranges"></a>Unterstützte numerische und Datums-/ Bereiche  
Formeln in [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] und tabellarische Modelle im Arbeitsspeicher sind unterliegen denselben Einschränkungen wie Excel in Bezug auf die maximal zulässige Werte für reelle Zahlen und Datumsangaben. Unterschiede können jedoch entstehen, wenn der maximale Wert von einer Berechnung oder einer Abfrage zurückgegeben wird, oder wenn Werte konvertiert, umgewandelt, gerundet oder gekürzt werden.  
  
-   Werden Werte der Typen **Currency** und **Real** multipliziert, und ist das Ergebnis größer als der maximal mögliche Wert, wird im DirectQuery-Modus kein Fehler ausgelöst. Zudem wird ein NULL-Wert zurückgegeben.  
  
-   Bei speicherinternen Modellen wird kein Fehler ausgelöst, aber der maximale Wert wird zurückgegeben.  
  
Da die zulässigen Datumsbereiche für Excel und SQL Server unterschiedlich sind, kann im Allgemeinen gewährleistet werden, dass Ergebnisse nur übereinstimmen, wenn sich Datumsangaben innerhalb des üblichen Datumsbereichs befinden. Dazu gehören die folgenden Datumsangaben:  
  
-   Frühestes Datum: 1. März 1990  
  
-   Letztes Datum: 31. Dezember 9999  
  
Wenn in Formeln verwendete Datumsangaben außerhalb dieses Bereichs liegen, führt entweder die Formel zu einem Fehler, oder die Ergebnisse stimmen nicht überein.  
  
**Von CEILING unterstützte Gleitkommawerte**  
BEISPIEL: `EVALUATE ROW("x", CEILING(-4.398488E+30, 1))`  
  
Die Transact-SQL-Entsprechung für die DAX-CEILING-Funktion unterstützt nur Werte mit einer Größe von maximal 10^19. Als Faustregel gilt, dass Gleitkommawerte in **bigint**passen sollten.  
  
**Datepart-Funktionen mit Datumsangaben außerhalb des Bereichs**  
Bei Ergebnissen im DirectQuery-Modus wird gewährleistet, dass diese den Ergebnissen von speicherinternen Modellen nur entsprechen, wenn sich das als Argument verwendete Datum innerhalb des gültigen Datumsbereichs befindet. Werden diese Bedingungen nicht erfüllt, wird entweder ein Fehler ausgelöst, oder die Formel gibt in DirectQuery andere Ergebnisse zurück als im speicherinternen Modus.  
  
BEISPIEL: `MONTH(0)` oder `YEAR(0)`  
  
Im DirectQuery-Modus geben die Ausdrücke 12 bzw. 1899 zurück.  
  
Bei speicherinternen Modellen geben die Ausdrücke 1 bzw. 1900 zurück.  
  
BEISPIEL:  `EOMONTH(0.0001, 1)`  
  
Die Ergebnisse dieses Ausdrucks stimmen nur überein, wenn sich die als Parameter angegebenen Daten innerhalb des gültigen Datumsbereichs befinden.  
  
BEISPIEL: `EOMONTH(blank(), blank())` oder `EDATE(blank(), blank())`  
  
Die Ergebnisse dieses Ausdrucks sollten im DirectQuery-Modus sowie im speicherinternen Modus gleich sein.  
  
**Kürzen von Zeitwerten**  
BEISPIEL: `SECOND(1231.04097222222)`  
  
Im DirectQuery-Modus wird das Ergebnis auf Basis der Regeln für SQL Server gekürzt. Zudem ergibt der Ausdruck den Wert "59".  
  
Bei speicherinternen Modellen werden die Ergebnisse jedes Zwischenvorgangs gerundet. Daher ergibt der Ausdruck den Wert "0".  
  
Im folgenden Beispiel wird veranschaulicht, wie dieser Wert berechnet wird:  
  
1.  Der Bruch der Eingabe (0.04097222222) wird mit 24 multipliziert.  
  
2.  Der resultierende Stundenwert (0.98333333328) wird mit 60 multipliziert.  
  
3.  Der resultierende Minutenwert ist 58.9999999968.  
  
4.  Der Bruch des Minutenwerts (0.9999999968) wird mit 60 multipliziert.  
  
5.  Der resultierende zweite Wert (59.999999808) wird auf 60 aufgerundet.  
  
6.  60 entspricht 0.  
  
**SQL-Zeitdatentyp nicht unterstützt**  
Bei speicherinternen Modellen wird die Verwendung des neuen **Time** -Datentyps nicht unterstützt. Im DirectQuery-Modus geben Formeln, die mit diesem Datentyp auf Spalten verweisen, einen Fehler zurück. Zeitdatenspalten können nicht in ein speicherinternes Modell importiert werden.  
  
Allerdings [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] in zwischengespeicherten Modellen mitunter wandelt die Engine den Zeitwert in einen zulässigen Datentyp und die Formel gibt ein Ergebnis zurück.  
  
Dieses Verhalten beeinflusst alle Funktionen, die eine Datumsspalte als Parameter verwenden.  
  
### <a name="bkmk_Currency"></a>Currency  
Im DirectQuery-Modus muss der Wert innerhalb des folgenden Bereichs liegen, wenn das Ergebnis eines arithmetischen Vorgangs den Typ **Currency**aufweist:  
  
-   Minimum: -922337203685477,5808  
  
-   Maximum: 922337203685477,5807  
  
**Kombinieren von Währungs- und REAL-Datentypen**  
BEISPIEL: `Currency sample 1`  
  
Wenn die Typen **Currency** und **Real** multipliziert werden und das Ergebnis größer als 9223372036854774784 (0x7ffffffffffffc00) ist, wird im DirectQuery-Modus kein Fehler ausgelöst.  
  
Bei einem speicherinternen Modell wird ein Fehler ausgelöst, wenn der absolute Wert des Ergebnisses größer als 922337203685477,4784 ist.  
  
**Vorgang führt zu einem Wert außerhalb des Bereichs**  
BEISPIEL: `Currency sample 2`  
  
Wenn Vorgänge zu zwei Währungswerten einen Wert ergeben, der sich außerhalb des angegebenen Bereichs befindet, wird bei speicherinternen Modellen ein Fehler ausgegeben, jedoch nicht bei DirectQuery-Modellen.  
  
**Kombinieren von Währungsdatentypen mit anderen Datentypen**  
Die Division von Währungswerten durch Werte anderer numerischer Typen kann zu unterschiedlichen Ergebnissen führen.  
  
### <a name="bkmk_Aggregations"></a>Aggregationsfunktionen  
Statistische Funktionen in einer Tabelle mit einer Zeile geben andere Ergebnisse zurück. Aggregationsfunktionen für leere Tabellen verhalten sich zudem bei speicherinternen Modellen anders als im DirectQuery-Modus.  
  
**Statistische Funktionen für eine Tabelle mit einer einzelnen Zeile**  
Wenn die als Argument verwendete Tabelle eine einzelne Zeile enthält, geben statistische Funktionen wie STDEV und VAR im DirectQuery-Modus einen NULL-Wert zurück.  
  
In einem speicherinternen Modell gibt eine Formel, die STDEV oder VAR für eine Tabelle mit einer einzelnen Zeile verwendet, einen Fehler wegen einer Division durch 0 zurück.  
  
### <a name="bkmk_Text"></a>Textfunktionen  
Da relationale Datenspeicher andere Textdatentypen bereitstellen als Excel, werden bei der Suche nach Zeichenfolgen oder bei der Arbeit mit Teilzeichenfolgen möglicherweise andere Ergebnisse zurückgegeben. Die Länge der Zeichenfolgen kann auch unterschiedlich sein.  
  
Im Allgemeinen funktioniert jede Zeichenfolgenbearbeitung, die Spalten mit fester Größe verwendet, wie Argumente über andere Ergebnisse verfügen können.  
  
Darüber hinaus unterstützen einige Textfunktionen in SQL Server zusätzliche Argumente, die nicht in Excel bereitgestellt werden. Wenn die Formel das fehlende Argument erfordert, können andere Ergebnisse oder Fehler im speicherinternen Modell zurückgegeben werden.  
  
**Vorgänge, die ein Zeichen mit LEFT, RIGHT usw. zurückgeben, geben möglicherweise das richtige Zeichen zurück – allerdings in einer anderen Schreibweise. Alternativ werden keine Ergebnisse zurückgegeben.**  
BEISPIEL: `LEFT([“text”], 2)`  
  
Im DirectQuery-Modus entspricht die Schreibweise des Zeichens, das zurückgegeben wird, stets dem Buchstaben, der in der Datenbank gespeichert wird. Das xVelocity-Engine verwendet jedoch aus Leistungsgründen einen anderen Algorithmus für die Komprimierung und Indizierung von Werten.  
  
Standardmäßig wird die Latin1_General-Sortierung verwendet (ohne Berücksichtigung der Groß-/Kleinschreibung und mit Unterscheidung von Akzenten). Sind mehrere Instanzen einer Textzeichenfolge in Kleinbuchstaben, Großbuchstaben oder mit gemischter Schreibweise vorhanden, werden folglich alle Instanzen als gleiche Zeichenfolge betrachtet, und nur die erste Instanz der Zeichenfolge wird im Index gespeichert. Sämtliche Textfunktionen, die bei gespeicherten Zeichenfolgen ausgeführt werden, rufen den angegebenen Teil des indizierten Formulars ab. Daher gibt die Beispielformel den gleichen Wert für die gesamte Spalte zurück und verwendet dabei die erste Instanz als Eingabe.  
  
[Zeichenfolgenspeicher und -sortierung in tabellarischen Modellen](http://msdn.microsoft.com/8516f0ad-32ee-4688-a304-e705143642ca)  
  
Dieses Verhalten gilt auch für andere Textfunktionen, einschließlich RIGHT, MID usw.  
  
**Zeichenfolgenlänge wirkt sich auf Ergebnisse aus**  
BEISPIEL: `SEARCH(“within string”, “sample target  text”, 1, 1)`  
  
Wenn Sie mit der SEARCH-Funktion nach einer Zeichenfolge suchen und die Zielzeichenfolge länger ist als die WITHIN-Zeichenfolge, löst der DirectQuery-Modus einen Fehler aus.  
  
Bei einem speicherinternen Modell wird die gesuchte Zeichenfolge zurückgegeben. Dabei wird jedoch ihre Länge auf die des &lt;WITHIN-Texts&gt;gekürzt.  
  
BEISPIEL: `EVALUATE ROW("X", REPLACE("CA", 3, 2, "California") )`  
  
Wenn die Ersatzzeichenfolge länger ist als die Originalzeichenfolge, gibt die Formel im DirectQuery-Modus einen NULL-Wert zurück.  
  
Bei speicherinternen Modellen entspricht das Verhalten der Formel dem von Excel. Dabei werden die Quellzeichenfolge und Ersatzzeichenfolge verkettet, wodurch CACalifornia zurückgegeben wird.  
  
**TRIM (implizit) in der Mitte von Zeichenfolgen**  
BEISPIEL: `TRIM(“ A sample sentence with leading white space”)`  
  
Der DirectQuery-Modus übersetzt die DAX-TRIM-Funktion in die SQL-Anweisung `LTRIM(RTRIM(<column>))`. Folglich werden nur führende und nachfolgende Leerstellen entfernt.  
  
Im Gegensatz dazu entfernt die gleiche Formel in einem speicherinternen Modell Leerzeichen innerhalb der Zeichenfolge – gemäß dem Verhalten von Excel.  
  
**RTRIM (implizit) mit Verwendung der LEN-Funktion**  
BEISPIEL: `LEN(‘string_column’)`  
  
Wie bei SQL Server entfernt auch der DirectQuery-Modus Leerstellen am Ende der Zeichenfolgenspalten automatisch (Ausführung der impliziten RTRIM-Funktion). Daher können Formeln, die die LEN-Funktion verwenden, andere Werte zurückgeben, wenn die Zeichenfolge nachfolgende Leerzeichen aufweist.  
  
**Der speicherinterne Modus unterstützt zusätzliche Parameter für SUBSTITUTE.**  
BEISPIEL: `SUBSTITUTE([Title],”Doctor”,”Dr.”)`  
  
BEISPIEL: `SUBSTITUTE([Title],”Doctor”,”Dr.”, 2)`  
  
Im DirectQuery-Modus können Sie nur die Version dieser Funktion verwenden, die über drei (3) Parameter verfügt: ein Verweis auf eine Spalte, der alte Text und der neue Text. Wenn Sie die zweite Formel verwenden, wird ein Fehler ausgelöst.  
  
Bei speicherinternen Modellen können Sie einen optionalen vierten Parameter verwenden, um die Instanznummer der zu ersetzenden Zeichenfolge anzugeben. Beispielsweise können Sie nur die zweite Instanz ersetzen usw.  
  
**Einschränkungen der Zeichenfolgenlänge für REPT-Vorgänge**  
Bei speicherinternen Modellen muss die Länge einer Zeichenfolge, die sich aus einem REPT-Vorgang ergibt, weniger als 32.767 Zeichen umfassen.  
  
Diese Einschränkung gilt nicht für den DirectQuery-Modus.  
  
**Vorgänge für Teilzeichenfolgen geben abhängig von Zeichentyp andere Ergebnisse zurück**  
BEISPIEL: `MID([col], 2, 5)`  
  
Wenn der Eingabetext **varchar** oder **nvarchar**lautet, ist das Ergebnis der Formel immer gleich.  
  
Entspricht der Text jedoch einem Zeichen mit fester Länge, und ist der Wert für *&lt;num_chars&gt;* größer als die Länge der Zielzeichenfolge, wird im DirectQuery-Modus am Ende der Ergebniszeichenfolge ein Leerzeichen hinzugefügt.  
  
Bei einem speicherinternen Modell endet das Ergebnis beim letzten Zeichenfolgenzeichen (ohne Auffüllung).  
  
## <a name="bkmk_SupportedFunc"></a>Im DirectQuery-Modus unterstützte Funktionen  
Die folgenden DAX-Funktionen können im DirectQuery-Modus verwendet werden, allerdings mit den im vorherigen Abschnitt beschriebenen Qualifikationen.  
  
**Textfunktionen**  
  
CONCATENATE  
  
FIND  
  
LEFT  
  
LEN  
  
MID  
  
REPLACE  
  
REPT  
  
RIGHT  
  
SUBSTITUTE  
  
TRIM  
  
**Statistische Funktionen**  
  
COUNT  
  
STDEV.P  
  
STDEV.S  
  
STDEVX.P  
  
STDEVX.S  
  
VAR.P  
  
VAR.S  
  
VARX.P  
  
VARX.S  
  
**Datum/Uhrzeit-Funktionen**  
  
DATE  
  
EDATE  
  
EOMONTH  
  
DATE  
  
TIME  
  
SECOND  
  
**Mathematische Funktionen und zahlenfunktionen**  
  
CEILING  
  
LN  
  
LOG  
  
LOG10  
  
POWER  
  
**DAX-Tabellenabfragen**  
  
Es gibt einige Einschränkungen, wenn Sie Formeln anhand eines DirectQuery-Modells auswerten, indem Sie DAX-Tabellenabfragen verwenden. DirectQuery unterstützt in einer ORDER BY-Klausel keinen zweimaligen Verweis auf dieselbe Spalte. Die entsprechende Transact-SQL-Anweisung kann nicht erstellt werden, und die Abfrage schlägt fehl.  
  
Bei einem speicherinternen Modell hat das Wiederholen der ORDER BY-Klausel keine Auswirkung auf die Ergebnisse.  
  
## <a name="bkmk_NotSupportedFunc"></a>Funktionen, die im DirectQuery-Modus nicht unterstützt.  
Einige DAX-Funktionen werden nicht in Modellen unterstützt, die im DirectQuery-Modus bereitgestellt werden. Wird eine bestimmte Funktion nicht unterstützt, kann dies auf mindestens einen der folgenden Gründe zurückgeführt werden:  
  
-   Die zugrunde liegende relationale Engine kann keine Berechnungen ausführen, die gleichwertig mit denen der xVelocity-Engine sind.  
  
-   Die Formel lässt sich nicht in einen entsprechenden SQL-Ausdruck umwandeln.  
  
-   Die Leistung des umgewandelten Ausdrucks und die resultierenden Berechnungen sind nicht akzeptabel.  
  
Die folgenden DAX-Funktionen können in DirectQuery-Modellen nicht verwendet werden.  
  
**Pfad-Funktionen**  
  
PATH  
  
PATHCONTAINS  
  
PATHITEM  
  
PATHITEMREVERSE  
  
PATHLENGTH  
  
**Sonstige Funktionen**  
  
COUNTBLANK  
  
FIXED  
  
FORMAT  
  
RAND  
  
RANDBETWEEN  
  
**Zeitintelligenzfunktionen: Start- und Enddatum**  
  
DATESQTD  
  
DATESYTD  
  
DATESMTD  
  
DATESQTD  
  
DATESINPERIOD  
  
TOTALMTD  
  
TOTALQTD  
  
TOTALYTD  
  
DATESINPERIOD  
  
SAMEPERIODLASTYEAR  
  
PARALLELPERIOD  
  
**Zeitintelligenzfunktionen: Bilanzen**  
  
OPENINGBALANCEMONTH  
  
OPENINGBALANCEQUARTER  
  
OPENINGBALANCEYEAR  
  
CLOSINGBALANCEMONTH  
  
CLOSINGBALANCEQUARTER  
  
CLOSINGBALANCEYEAR  
  
**Zeitintelligenzfunktionen: vorherige und kommende Zeiträume**  
  
PREVIOUSDAY  
  
PREVIOUSMONTH  
  
PREVIOUSQUARTER  
  
PREVIOUSYEAR  
  
NEXTDAY  
  
NEXTMONTH  
  
NEXTQUARTER  
  
NEXTYEAR  
  
**Zeitintelligenzfunktionen: Zeiträume und Berechnungen im Verlauf von Zeiträumen**  
  
STARTOFMONTH  
  
STARTOFQUARTER  
  
STARTOFYEAR  
  
ENDOFMONTH  
  
ENDOFQUARTER  
  
ENDOFYEAR  
  
FIRSTDATE  
  
LASTDATE  
  
DATEADD  
  
## <a name="see-also"></a>Siehe auch  
[DirectQuery-Modus (SSAS – tabellarisch)](http://msdn.microsoft.com/45ad2965-05ec-4fb1-a164-d8060b562ea5)  
  

