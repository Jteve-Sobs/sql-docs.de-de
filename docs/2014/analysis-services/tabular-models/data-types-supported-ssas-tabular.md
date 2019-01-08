---
title: Datentypen unterstützt (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 92993f7b-7243-4aec-906d-0b0379798242
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ed99b26641b6d87fa6fe3bf07f47c21eacb96d89
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52405475"
---
# <a name="data-types-supported-ssas-tabular"></a>Unterstützte Datentypen (SSAS – tabellarisch)
  In diesem Artikel werden die Datentypen erläutert, die in tabellarischen Modellen verwendet werden können, und die implizite Konvertierung von Datentypen bei der Berechnung oder Verwendung von Daten in einer Data Analysis Expressions (DAX)-Formel beschrieben.  
  
 Dieser Artikel enthält folgende Abschnitte:  
  
-   [In tabellarischen Modellen verwendete Datentypen](#bkmk_data_types)  
  
-   [Implizite und explizite Datentypkonvertierungen in DAX-Formeln](#bkmk_implicit)  
  
-   [Behandeln von Leerzeichen, leeren Zeichenfolgen und Nullwerten](#bkmk_hand_blanks)  
  
##  <a name="bkmk_data_types"></a> In tabellarischen Modellen verwendete Datentypen  
 Die folgenden Datentypen werden unterstützt. Wenn Sie Daten importieren oder einen Wert in einer Formel verwenden, werden die Daten in einen der folgenden Datentypen konvertiert, auch wenn die ursprüngliche Datenquelle einen anderen Datentyp enthält. Werte, die sich aus Formeln ergeben, verwenden ebenfalls diese Datentypen.  
  
 Im Allgemeinen werden diese Datentypen implementiert, um genaue Berechnungen in berechneten Spalten zu ermöglichen. Die gleichen Einschränkungen gelten aus Konsistenzgründen auch für den Rest der Daten in Modellen.  
  
 Formate für Zahlen, Währungen, Datumsangaben und Uhrzeiten sollten dem Format des Gebietsschemas auf dem Client folgen, der für die Arbeit mit den Modelldaten verwendet wird. Sie können die Formatierungsoptionen im Modell verwenden, um die Darstellung des Werts zu bestimmen.  
  
||||  
|-|-|-|  
|Datentyp im Modell|Datentyp in DAX|Description|  
|Ganze Zahl|Ein ganzzahliger 64-Bit-Wert (acht Byte) <sup>1, 2</sup>|Zahlen ohne Dezimalstellen. Ganze Zahlen können positiv oder negativ sein, aber müssen ganze Zahlen zwischen -9 223 372 036 854 775 808 (-2^63) und 9 223 372 036 854 775 807 (2^63-1) sein.|  
|Decimal Number|Eine reelle 64-Bit-Zahl (acht Byte) <sup>1, 2</sup>|Reelle Zahlen sind Zahlen, die Dezimalstellen aufweisen können. Reelle Zahlen decken viele Werte ab:<br /><br /> Negative Werte von -1,79E +308 bis -2,23E -308<br /><br /> Null (0)<br /><br /> Positive Werte von 2,23E -308 bis -1,79E +308<br /><br /> Die Anzahl der relevanten Stellen wird jedoch auf siebzehn Dezimalstellen beschränkt.|  
|Boolean|Boolean|Entweder ein True oder ein False-Wert.|  
|Textmodus|Zeichenfolge|Eine Unicodezeichen-Datenzeichenfolge. Dies können Zeichenfolgen, Zahlen oder Datumsangaben im Textformat sein.|  
|date|Date/Time|Datumsangaben und Uhrzeiten in einer akzeptierten Form für die Darstellung von Datum und Uhrzeit.<br /><br /> Gültig sind alle Datumsangaben nach dem 1. März 1900.|  
|Währung|Währung|Der Währungsdatentyp lässt Werte zwischen -922 337 203 685 477,5808 und 922 337 203 685 477,5807 mit vier Dezimalstellen unveränderlicher Genauigkeit zu.|  
|Nicht zutreffend|Leer|Ein leerer Datentyp in DAX, der SQL-NULLEN darstellt und ersetzt. Sie können mit der BLANK-Funktion ein Leerzeichen erstellen und mit der logischen ISBLANK-Funktion nach Leerzeichen suchen.|  
  
 <sup>1</sup> DAX-Formeln unterstützen keine Datentypen, die kleiner als die in der Tabelle aufgeführt sind.  
  
 <sup>2</sup> , wenn Sie versuchen, Daten zu importieren, sehr große numerische Werte enthält, kann der Importvorgang mit folgendem Fehler fehlschlagen:  
  
 In-Memory-Datenbank-Fehler: Die "\<Spaltenname >" Spalte der '\<Tabellenname > "Tabelle enthält einen Wert" 1. 7976931348623157E + 308", dies wird nicht unterstützt. Der Vorgang wurde abgebrochen.  
  
 Dieser Fehler tritt auf, da der Modell-Designer diesen Wert zur Darstellung von Nullen verwendet. Die Werte in der folgenden Liste sind zum vorherigen erwähnten Nullwert synonym:  
  
||  
|-|  
|Wert|  
|9223372036854775807|  
|-9223372036854775808|  
|1,7976931348623158e+308|  
|2,2250738585072014e-308|  
  
 Sie sollten den Wert aus den Daten entfernen und erneut importieren.  
  
> [!NOTE]  
>  Sie können keine Elemente aus einer **varchar(max)** -Spalte importieren, die eine Zeichenfolgenlänge von mehr als 131.072 Zeichen enthält.  
  
### <a name="table-data-type"></a>Table-Datentyp  
 Außerdem verwendet DAX einen *table* -Datentyp. Dieser Datentyp wird von DAX in vielen Funktionen verwendet, z. B. in Aggregationen und Zeitintelligenzberechnungen. Einige Funktionen erfordern einen Verweis auf eine Tabelle, während andere Funktionen eine Tabelle zurückgeben, die als Eingabe für andere Funktionen verwendet werden kann. In einigen Funktionen, die eine Tabelle als Eingabe erfordern, können Sie einen Ausdruck angeben, der eine Tabelle ergibt. Bei einigen Funktionen ist ein Verweis auf eine Basistabelle erforderlich. Informationen zu den Anforderungen bestimmter Funktionen finden Sie in der [DAX-Funktionsreferenz](https://msdn.microsoft.com/library/ee634396.aspx).  
  
##  <a name="bkmk_implicit"></a> Implizite und explizite Datentypkonvertierungen in DAX-Formeln  
 Jede DAX-Funktion verfügt über bestimmte Anforderungen im Hinblick auf die Datentypen, die als Eingaben und Ausgaben verwendet werden. Einige Funktionen erfordern z. B. ganze Zahlen für einige Argumente und Daten für andere, während für andere Funktionen Text oder Tabellen erforderlich sind.  
  
 Wenn die Daten in der Spalte, die Sie als Argument angeben, nicht mit dem erforderlichen Datentyp kompatibel sind, gibt DAX in vielen Fällen einen Fehler zurück. Sofern möglich, versucht DAX die Daten jedoch implizit in den erforderlichen Datentyp zu konvertieren. Zum Beispiel:  
  
-   Sie können eine Zahl ist, z. B. "123", als Zeichenfolge eingeben. DAX analysiert die Zeichenfolge und versucht, diese als Zahlendatentyp anzugeben.  
  
-   Sie können TRUE + 1 hinzufügen und als Ergebnis 2 abrufen, da TRUE implizit in die Zahl 1 konvertiert wird und der Vorgang 1+1 ausgeführt wird.  
  
-   Wenn Sie Werte in zwei Spalten hinzufügen und ein Wert als Text ("12") und der andere als Zahl (12) dargestellt wird, konvertiert DAX die Zeichenfolge implizit in eine Zahl und addiert diese dann zu einem Ergebnis in numerischer Form. Vom folgenden Ausdruck wird 44 zurückgegeben: = "22" + 22  
  
-   Wenn Sie zwei Zahlen verketten möchten, stellt das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Add-In sie als Zeichenfolgen dar und verkettet sie dann. Vom folgenden Ausdruck wird "1234" zurückgegeben: = 12 & 34  
  
 In der folgenden Tabelle werden die impliziten Datentypkonvertierungen zusammengefasst, die in Formeln ausgeführt werden. Im Allgemeinen verhält sich der Designer für semantische Modelle wie Microsoft Excel und führt implizite Konvertierungen aus, wann immer dies möglich und bei dem betreffenden Vorgang erforderlich ist.  
  
### <a name="table-of-implicit-data-conversions"></a>Tabelle mit impliziten Datenkonvertierungen  
 Der ausgeführte Konvertierungstyp wird vom Operator bestimmt, der die erforderlichen Werte umwandelt, bevor der entsprechende Vorgang ausgeführt wird. In diesen Tabellen sind die Operatoren aufgeführt. Außerdem wird die Konvertierung angegeben, die bei den einzelnen Datentypen in der Spalte ausgeführt wird, wenn er dem Datentyp in der überschneidenden Zeile zugeordnet wird.  
  
> [!NOTE]  
>  Textdatentypen sind in diesen Tabellen nicht enthalten. Wenn eine Zahl wie in einem Textformat dargestellt wird, versucht der Modell-Designer in einigen Fällen, den Zahlentyp zu bestimmen und ihn als Zahl anzugeben.  
  
#### <a name="addition-"></a>Addition (+)  
  
||||||  
|-|-|-|-|-|  
|Operator (+)|INTEGER|Währung|real|Date/Time|  
|INTEGER|INTEGER|Währung|real|Date/Time|  
|CURRENCY|CURRENCY|CURRENCY|real|Date/Time|  
|real|real|real|real|Date/Time|  
|Date/Time|Date/Time|Date/Time|Date/Time|Date/Time|  
  
 Wenn beispielsweise eine reelle Zahl bei einer Addition in Verbindung mit Währungsdaten verwendet wird, werden beide Werte in REAL konvertiert, und das Ergebnis wird als REAL zurückgegeben.  
  
#### <a name="subtraction--"></a>Subtraktion (-)  
 In der folgenden Tabelle ist die Zeilenüberschrift der Minuend (linke Seite), und die Spaltenüberschrift ist der Subtrahend (rechte Seite).  
  
||||||  
|-|-|-|-|-|  
|Operator (-)|INTEGER|Währung|real|Date/Time|  
|INTEGER|INTEGER|Währung|real|real|  
|CURRENCY|CURRENCY|CURRENCY|real|real|  
|real|real|real|real|real|  
|Date/Time|Date/Time|Date/Time|Date/Time|Date/Time|  
  
 Wenn beispielsweise ein Datum bei einer Subtraktion mit einem beliebigen anderen Datentyp verwendet wird, werden beide Werte in Datumsangaben konvertiert, und der Rückgabewert ist ebenfalls ein Datum.  
  
> [!NOTE]  
>  Tabellarische Modelle unterstützen auch den unären Operator "-" (negativ). Dieser Operator ändert den Datentyp des Operanden jedoch nicht.  
  
#### <a name="multiplication-"></a>Multiplikation (*)  
  
||||||  
|-|-|-|-|-|  
|Operator (*)|INTEGER|Währung|real|Date/Time|  
|INTEGER|INTEGER|Währung|real|INTEGER|  
|CURRENCY|CURRENCY|real|CURRENCY|CURRENCY|  
|real|real|CURRENCY|real|real|  
  
 Wenn beispielsweise eine ganze Zahl bei einer Multiplikation mit einer reellen Zahl kombiniert wird, werden beide Zahlen in reelle Zahlen konvertiert, und der Rückgabewert ist ebenfalls REAL.  
  
#### <a name="division-"></a>Division (/)  
 In der folgenden Tabelle ist die Zeilenüberschrift der Zähler, und die Spaltenüberschrift ist der Nenner.  
  
||||||  
|-|-|-|-|-|  
|Operator (/)<br /><br /> (Zeile/Spalte)|INTEGER|Währung|real|Date/Time|  
|INTEGER|real|CURRENCY|real|real|  
|CURRENCY|CURRENCY|real|CURRENCY|real|  
|real|real|real|real|real|  
|Date/Time|real|real|real|real|  
  
 Wenn beispielsweise eine ganze Zahl bei einer Division mit einem Währungswert kombiniert wird, werden beide Werte in reelle Zahlen konvertiert, und das Ergebnis ist ebenfalls ein reeller Wert.  
  
#### <a name="comparison-operators"></a>Vergleichsoperatoren  
 In Vergleichsausdrücken werden boolesche Werte als größer als Zeichenfolgenwerte betrachtet, und Zeichenfolgenwerte werden als größer als numerische Werte oder Datums-/Uhrzeitwerte betrachtet. Zahlen- und Datums-/Uhrzeitwerte werden als gleichrangig betrachtet. Für boolesche Werte oder Zeichenfolgenwerte werden keine impliziten Konvertierungen ausgeführt. BLANK oder ein leerer Wert wird abhängig vom Datentyp des anderen verglichenen Werts in 0/""/false konvertiert.  
  
 Die folgenden DAX-Ausdrücke veranschaulichen dieses Verhalten:  
  
 `=IF(FALSE()>"true","Expression is true", "Expression is false")`, gibt `"Expression is true"`  
  
 `=IF("12">12,"Expression is true", "Expression is false")`, gibt `"Expression is true"`  
  
 `=IF("12"=12,"Expression is true", "Expression is false")`, gibt `"Expression is false"`  
  
 Konvertierungen werden gemäß der folgenden Tabelle implizit für numerische oder Datums-/Uhrzeittypen ausgeführt:  
  
||||||  
|-|-|-|-|-|  
|Vergleichsoperator|INTEGER|Währung|real|Date/Time|  
|INTEGER|INTEGER|Währung|real|real|  
|CURRENCY|CURRENCY|CURRENCY|real|real|  
|real|real|real|real|real|  
|Date/Time|real|real|real|Date/Time|  
  
##  <a name="bkmk_hand_blanks"></a> Behandeln von Leerzeichen, leeren Zeichenfolgen und Nullwerten  
 DAX behandelt Nullwerte (0), Null und leere Zeichenfolgen anders als Microsoft Excel und SQL Server. In diesem Abschnitt werden die Unterschiede beschrieben, und es wird erläutert, wie diese Datentypen behandelt werden.  
  
 Dabei ist wichtig zu beachten, dass ein leerer Wert, eine leere Zelle oder ein fehlender Wert alle durch den gleichen neuen Werttyp (BLANK) dargestellt werden. Wie Leerzeichen in Vorgängen gehandhabt werden (z. B. Hinzufügen oder Verketten), hängt von der jeweiligen Funktion ab. Sie können auch Leerzeichen mit der BLANK-Funktion generieren oder mit der ISBLANK-Funktion nach Leerzeichen suchen. Datenbank-NULLEN werden innerhalb eines Semantikmodells nicht unterstützt, und NULLEN werden implizit in Leerzeichen konvertiert, wenn in einer DAX-Formel auf eine Spalte mit einem Nullwert verwiesen wird.  
  
### <a name="defining-blanks-nulls-and-empty-strings"></a>Definieren von Leerzeichen, NULLEN und leeren Zeichenfolgen  
 In der folgenden Tabelle werden die Unterschiede zwischen DAX und Microsoft Excel in Bezug auf die Behandlung von Leerzeichen zusammengefasst.  
  
||||  
|-|-|-|  
|expression|DAX|Excel|  
|BLANK + BLANK|BLANK|0 (Null)|  
|BLANK +5|5|5|  
|BLANK * 5|BLANK|0 (Null)|  
|5/BLANK|Unendlich|Fehler|  
|0/BLANK|NaN|Fehler|  
|BLANK/BLANK|Leer|Fehler|  
|FALSE OR BLANK|FALSE|FALSE|  
|FALSE AND BLANK|FALSE|FALSE|  
|TRUE OR BLANK|TRUE|TRUE|  
|TRUE AND BLANK|FALSE|TRUE|  
|BLANK OR BLANK|BLANK|Fehler|  
|BLANK AND BLANK|BLANK|Fehler|  
  
 Informationen zur Behandlung von Leerzeichen durch eine bestimmte Funktion oder einen Operator finden Sie in den einzelnen Themen zu den verschiedenen DAX-Funktionen im Abschnitt [DAX-Funktionsreferenz](https://msdn.microsoft.com/library/ee634396.aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen &#40;SSAS – tabellarisch&#41;](../data-sources-ssas-tabular.md)   
 [Importieren von Daten &#40;SSAS – tabellarisch&#41;](../import-data-ssas-tabular.md)  
  
  
