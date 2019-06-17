---
title: Erstellen einer OLAP-Miningstruktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 21cbdc9d-d33c-4026-b9ef-1be2bd92b3b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: adf29f6f73020ddc265072b3b9f3f67042200506
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66085251"
---
# <a name="create-an-olap-mining-structure"></a>Erstellen einer OLAP-Miningstruktur
  Die Erstellung eines Data Mining-Modells auf Grundlage eines OLAP-Cubes oder eines anderen mehrdimensionalen Datenspeichers bietet zahlreiche Vorteile. Eine OLAP-Lösung enthält bereits umfangreiche Datenmengen, die gut organisiert, bereinigt und ordnungsgemäß formatiert sind. Die Komplexität der Daten ist jedoch so hoch, dass Benutzer wahrscheinlich kaum sinnvolle Muster mittels Ad-hoc-Untersuchungen erkennen können. Data Mining bietet die Möglichkeit, neue Korrelationen zu ermitteln und wertvolle Einblicke bereitzustellen.  
  
 In diesem Thema wird beschrieben, wie Sie eine OLAP-Miningstruktur auf Grundlage einer Dimension und verwandter Measures in einer vorhandenen mehrdimensionalen Lösung erstellen.  
  
 [Anforderungen](#bkmk_Reqs)  
  
 [Übersicht über den OLAP Data Mining-Prozess](#bkmk_Overview)  
  
 [Szenarien für die Verwendung von Data Mining in OLAP-Lösungen](#bkmk_OLAP_Scenarios)  
  
 [Filter](#bkmk_Filters)  
  
 [Verwenden von geschachtelten Tabellen](#bkmk_Nested)  
  
 [Data Mining-Dimensionen](#bkmk_DMDimension)  
  
##  <a name="bkmk_Reqs"></a> Anforderungen für OLAP-Miningstrukturen und -Miningmodelle  
 Wenn Sie ein OLAP-Miningmodell entwerfen, ist die Datenquelle bereits in der Datenbank vorhanden, die zum Erstellen des Cubes verwendet wurde. Sie können keine Verbindung mit einem Remotecube herstellen und Data Mining-Objekte erstellen. Die Cubeobjekte müssen innerhalb der gleichen Lösung wie die Datenbank und die Miningstruktur verfügbar sein, die Sie erstellen.  
  
 Wenn Sie die ursprünglichen Projektdateien nicht haben oder diese nicht ändern möchte, können Sie die Option **Von Server importieren (mehrdimensional und Data Mining)** Visual Studio verwenden, um eine Kopie der Metadaten- und Lösungsobjekte abzurufen. Sie können dann das Bereitstellungsziel ändern, die Datenquellen bearbeiten und mit den Cubeobjekten arbeiten, ohne dass sich dies auf die vorhandenen Objekte auswirkt.  
  
 Weitere Informationen finden Sie unter [Importieren eines Data Mining-Projekts mithilfe des Analysis Services-Import-Assistenten](import-a-data-mining-project-using-the-analysis-services-import-wizard.md).  
  
##  <a name="bkmk_Overview"></a> Übersicht über den OLAP Data Mining-Prozess  
 Starten Sie den Data Mining-Assistenten, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Miningstrukturen** klicken und  **Neue Miningstruktur**auswählen. Der Assistent führt Sie zum Erstellen der Struktur für eine neue Struktur und ein neues Modell durch folgende Schritte:  
  
1.  **Definitionsmethode auswählen**: Hier wählen Sie einen Datenquellentyp aus, und wählen Sie **aus vorhandenem Cube**.  
  
    > [!NOTE]  
    >  Der OLAP-Cube, den Sie als Quelle verwenden, muss sich in der gleichen Datenbank wie die Miningstruktur befinden (siehe oben). Sie können außerdem keinen Cube verwenden, der vom PowerPivot für Excel-Add-In als Data Mining-Quelle erstellt wurde.  
  
2.  **Erstellen von Datamining-Struktur**: Bestimmen Sie, ob Sie nur eine Struktur erstellen oder eine Struktur mit einem Miningmodell.  
  
     Sie müssen des weiteren zum Analysieren der Daten einen geeigneten Algorithmus auswählen. Hinweise darauf, welcher Algorithmus am besten für bestimmte Aufgaben geeignet ist, finden Sie unter HYPERLINK "ms-help://SQL111033/as_1devconc/html/ed1fc83b-b98c-437e-bf53-4ff001b92d64.htm" Data Mining-Algorithmen (Analysis Services - Data Mining).  
  
3.  **Wählen Sie die Quellcubedimension**: Dieser Schritt ist identisch mit der Auswahl einer Datenquelle. Sie müssen eine einzelne Dimension auswählen, die die wichtigsten Daten zum Trainieren des Modells enthält. Sie können später Daten aus anderen Dimensionen hinzufügen oder die Dimension filtern.  
  
4.  **Fallschlüssel auswählen**: Innerhalb der Dimension, die Sie soeben ausgewählt haben, wählen Sie ein Attribut (Spalte), als der eindeutige Bezeichner für die Falldaten verwendet werden.  
  
     In der Regel wird eine Spalte vorab ausgewählt, Sie können die Spalte jedoch ändern, wenn mehrere Schlüssel vorhanden sind.  
  
5.  **Auswählen von Spalten auf Fallebene**: Hier wählen Sie die Attribute aus der ausgewählten Dimension und die zugehörigen Measures, die für die Analyse relevant sind. Dieser Schritt entspricht der Auswahl von Spalten aus einer Tabelle.  
  
     Der Assistent schließt automatisch alle Measures, die mit Attributen aus der ausgewählten Dimension erstellt wurden, für die Überprüfung und Auswahl ein.  
  
     Beispielsweise wird der Cube enthält, ein Measure, das Frachtkosten basierend auf dem geografischen Standort des Kunden wird berechnet, und Sie die Customer-Dimension als Hauptdatenquelle für die Modellierung ausgewählt haben, das Measure als Kandidat für vorgeschlagen werden dem Modell hinzufügen. Fügen Sie nicht zu viele Measures hinzu, die direkt auf Attributen basieren. Es besteht bereits eine implizite Beziehung zwischen den Spalten, wie in der Measureformel definiert, und die Stärke dieser (erwarteten) Korrelation kann andere Beziehungen verdecken, die Sie andernfalls erkennen würden.  
  
6.  **Geben Sie die Verwendung der Miningmodellspalte**: Für jedes Attribut oder Measure, das Sie der Struktur hinzugefügt haben, müssen Sie angeben, ob das Attribut für Vorhersagen zur Verfügung, oder als Eingabe verwendet werden soll. Wenn Sie keine dieser Optionen auswählen, werden die Daten zwar verarbeitet, aber nicht für die Analyse verwendet. Sie sind jedoch als Hintergrunddaten verfügbar, falls Sie später Drillthrough aktivieren.  
  
7.  **Hinzufügen von geschachtelten Tabellen**: Klicken Sie auf diese Option, um verwandte Tabellen hinzuzufügen. Im Dialogfeld **Wählen Sie eine Measuregruppendimension aus** können Sie von unter den Dimensionen, die sich auf die aktuelle Dimension beziehen, eine einzelne Dimension auswählen.  
  
     Anschließend definieren Sie im Dialogfeld **Schlüssel der geschachtelten Tabelle auswählen** , wie sich die neue Dimension auf die Dimension bezieht, die die Falldaten enthält.  
  
     Wählen Sie im Dialogfeld **Geschachtelte Tabellenspalten auswählen** die Attribute und Measures aus der neuen Dimension aus, die Sie in der Analyse verwenden möchten. Sie müssen außerdem angeben, ob das geschachtelte Attribut für Vorhersagen verwendet wird.  
  
     Nachdem Sie alle geschachtelten Attribute hinzugefügt haben, die Sie benötigen, kehren Sie zur Seite **Verwendung der Miningmodellspalte angeben**zurück, und klicken Sie auf **Weiter**.  
  
8.  **Angeben von Spalten Inhalt und Datentyp**: Sie haben nun alle Daten, die für die Analyse verwendet werden, und müssen angeben hinzugefügt der *Datentyp* und *Inhaltstyp* für jedes Attribut.  
  
     In einem OLAP-Modell besteht keine Möglichkeit, Datentypen automatisch zu erkennen, da der Datentyp bereits von der mehrdimensionalen Lösung definiert wird und nicht geändert werden kann. Schlüssel werden auch automatisch identifiziert. Weitere Informationen finden Sie unter [Datentypen &#40;Data Mining&#41;](data-types-data-mining.md).  
  
     Der *Inhaltstyp* , den Sie für jede im Modell verwendete Spalte auswählen, teilt den Algorithmus mit, wie die Daten verarbeitet werden sollen. Weitere Informationen finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](content-types-data-mining.md).  
  
9. **Aufteilen des Quellcubes**: Hier können Sie Filter definieren, in einem Cube nur eine Teilmenge der Daten auszuwählen und präzisere werden Modelle zu trainieren.  
  
     Sie filtern einen Cube, indem Sie die Dimension, nach der gefiltert wird, und die Hierarchieebene, die die gewünschten Kriterien enthält, auswählen und dann Bedingung eingeben, die als Filter verwendet werden soll.  
  
10. **Erstellen eines Testsatzes**: Auf dieser Seite können Sie den Assistenten mitteilen, wie viele Daten zum Testen des Modells reserviert werden soll. Wenn die Daten mehrere Modelle unterstützen, empfiehlt es sich, ein zurückgehaltenes Dataset zu erstellen, sodass alle Modelle basierend auf den gleichen Daten getestet werden können.  
  
     Weitere Informationen finden Sie unter [Tests und Überprüfung &#40;Data Mining&#41;](testing-and-validation-data-mining.md).  
  
11. **Der Assistent**: Auf dieser Seite geben einen Namen, um die neue Miningstruktur und das zugeordnete Miningmodell, und speichern die Struktur und Modell.  
  
     Auf dieser Seite können Sie außerdem die folgenden Optionen festlegen:  
  
    -   **Drillthrough zulassen**  
  
    -   **Miningmodelldimension erstellen**  
  
    -   **Cube mithilfe der Miningmodelldimension erstellen**  
  
     Weitere Informationen zu diesen Optionen finden Sie weiter unten in diesem Thema im Abschnitt [Grundlegendes zu Data Mining-Dimensionen und Drillthrough](#bkmk_DMDimension).  
  
 Zu diesem Zeitpunkt sind die Miningstruktur und das zugeordnete Modell nur Metadaten. Sie müssen beide verarbeiten, um Ergebnisse zu erhalten.  
  
##  <a name="bkmk_OLAP_Scenarios"></a> Szenarien für die Verwendung von Data Mining mit OLAP-Daten  
 OLAP-Cubes enthalten häufig zahlreiche Elemente und Dimensionen, sodass es schwierig sein kann, zu entscheiden, wo mit dem Data Mining begonnen werden soll. Um die Muster in den Cubes leichter zu identifizieren, identifizieren Sie normalerweise zuerst eine Dimension von Interesse und durchsuchen dann Muster, die mit dieser Dimension verknüpft sind. In der folgenden Tabelle werden mehrere allgemeine Data Mining-Aufgaben von OLAP aufgelistet, Beispielszenarien zur Anwendung der einzelnen Aufgaben beschrieben und der Data Mining-Algorithmus zum Verwenden für die jeweilige Aufgabe identifiziert.  
  
|Aufgabe|Beispielszenario|Algorithmus|  
|----------|---------------------|---------------|  
|Gruppieren Sie Elemente in Clustern|Segmentieren Sie eine Kundendimension auf Basis der Kundenelementeigenschaften, der Produkte, die die Kunden kaufen, und des Geldbetrags, den die Kunden ausgeben.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering-Algorithmus|  
|Finden Sie interessante oder ungewöhnliche Elemente|Identifizieren Sie interessante oder ungewöhnliche Läden in einer Speicherdimension, basierend auf Nettoumsatz, Gewinn, Ort und Größe des Ladens.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus|  
|Finden Sie interessante oder ungewöhnliche Zellen|Identifizieren Sie Umsätze in Läden, die nicht den allgemeinen Trends im Verlauf der Zeit entsprechen.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series-Algorithmus|  
|Suchen von Korrelationen|Identifizieren Sie Faktoren im Zusammenhang mit Serverausfallzeiten, einschließlich Bereich, Computertyp, Betriebssystem oder Kaufdatum.|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes-Algorithmus|  
  
##  <a name="bkmk_Filters"></a> Segmentieren einen Cube im Vergleich. Filtern von Modellen  
 Das Aufteilen des Cubes in Slices, während Sie ein Modell erstellen, entspricht dem Erstellen eines Filters für ein relationales Miningmodell. In einem relationalen Modell wird der Filter für die Datenquelle als WHERE-Klausel in einer SQL-Anweisung definiert. In einem Cube verwenden Sie den Editor, um Filteranweisungen mit MDX zu erstellen.  
  
 Ein Cube kann beispielsweise Informationen zu Produktkäufen weltweit enthalten. Für eine Marketingkampagne möchten Sie jedoch ein Modell auf Grundlage der Analyse weiblicher Kunden über 30 erstellen, die in Großbritannien leben.  
  
 In diesem Szenario würden Sie zwei Filter erstellen:  
  
-   Für den ersten Filter, Sie würden die Geography-Dimension auswählen, wählen Sie die Hierarchie für die Region, und dann die **Filterausdruck** Liste aus, um den möglichen Werten "Großbritannien" auswählen.  
  
-   Für den zweiten Filter würden Sie die Customer-Dimension auswählen, wählen Sie das Gender-Attribut, und wählen "Frau" aus der Liste der Attributwerte enthalten.  
  
 Nachdem die Miningstruktur erstellt wurde, können Sie sowohl die Definition der Cubedaten als auch die Filterkriterien ändern. Weitere Informationen finden Sie unter [Filtern des Quellcubes für eine Miningstruktur](../filter-the-source-cube-for-a-mining-structure.md).  
  
 Sowohl die Registerkarte **Miningstruktur** als auch die Registerkarte **Miningmodell** enthalten eine Option, mit der Sie einer vorhandenen Miningstruktur einen Filter hinzufügen können. Klicken Sie hierzu auf **Cubeslice definieren**. Das Dialogfeld **Cube in Slices aufteilen** hilft Ihnen, durch das Auswählen eines Werts aus Dropdownlisten einen gültigen MDX-Filterausdruck zu erstellen.  
  
> [!WARNING]  
>  Beachten Sie, dass die Schnittstelle zum Entwerfen und Durchsuchen von Cubes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]geändert wurde. Weitere Informationen finden Sie unter [Durchsuchen von Daten und Metadaten in Cube](../multidimensional-models/browse-data-and-metadata-in-cube.md).  
  
 Sie können dem Cube so viele Filter hinzufügen, wie notwendig sind, um die für das Miningmodell erforderlichen Daten zurückzugeben. Sie können zudem Slices für einzelne Cubeslices definieren. Beispiel: Wenn Ihre Struktur zwei geschachtelte Tabellen enthält, die auf Produkten basieren, können Sie eine Tabelle am Segment für März 2004 und die andere am Segment für April 2004 in Slices teilen. Mit dem resultierenden Modell lassen sich dann, basierend auf den Verkaufszahlen für März, Vorhersagen für die Verkäufe im April tätigen.  
  
##  <a name="bkmk_Nested"></a> Verwenden von geschachtelten Tabellen in einem OLAP-Miningmodell  
 Als Sie mithilfe des Data Mining-Assistenten ein Modell auf Grundlage von Cubedaten erstellen, können Sie geschachtelte Tabellen hinzufügen, indem Sie die Namen verwandter Dimensionen angeben und die Attribute oder Measures, auswählen, die dem Modell hinzugefügt werden sollen.  
  
 Wenn zum Beispiel die für Falldaten verwendete Hauptdimension „Customer“ ist, können Sie „Products“ als verwandte Dimension hinzufügen, da Sie davon ausgehen können, dass ein Kunde im Laufe der Zeit mehrere Produkte bestellt hat und der Cube jeden Kunden über die Reihenfolgenfaktentabellen mit verschiedenen Produkten verknüpft.  
  
 Sie fügen geschachtelte Tabellen auf der Seite **Verwendung der Miningmodellspalte angeben** des Assistenten hinzu, indem Sie auf **Geschachtelte Tabellen hinzufügen**klicken. Ein Dialogfeld wird geöffnet, das Sie durch Prozess, zur Auswahl verwandter Dimension sowie aller Measures führt. Die Falldimensionen und geschachtelten Dimensionen müssen durch einen Fremdschlüssel verknüpft sein, und Measures müssen eines der Attribute verwenden, die bereits in der Falltabelle oder geschachtelten Tabellen enthalten sind. Leider können diese Einschränkungen wirklich nicht viel ausrichten, um den Bereich einzugrenzen, damit Sie achten müssen, wählen Sie nur die Attribute, die für die Modellierung hilfreich sind.  
  
 Sie müssen für jedes Attribut oder Measure, das Sie der geschachtelten Tabelle hinzufügen, angeben, ob das geschachtelte Attribut für Vorhersagen verwendet wird. Wählen Sie hierzu im Dialogfeld **Geschachtelte Tabellenspalten auswählen** die Option **Vorhersagbar** oder **Eingabe** aus. Wenn Sie keine dieser Optionen auswählen, werden die Daten der Miningstruktur hinzugefügt, aber werden nicht für die Analyse verwendet.  
  
 Für jedes Attribut und Measure müssen Sie außerdem angeben, ob das Attribut diskret, diskretisiert oder kontinuierlich ist. Der Assistent wählt auf Grundlage des Datentyps des Attributs einen Standardwert aus, Sie können diese jedoch abhängig von den Algorithmusanforderungen ändern. Wenn Sie einen Inhaltstyp auswählen, die nicht mit dem Algorithmus kompatibel ist. Sie haben ausgewählt (angenommen, Sie verwenden einen kontinuierlichen numerischen Typ mit einem Naïve Bayes-Modell), wenn Sie versuchen, das Modell verarbeiten, erhalten Sie keine Fehlermeldung angezeigt.  
  
 Nachdem Sie diese Optionen festgelegt haben, fügt der Assistent die geschachtelte Tabelle der Falltabelle hinzu. Der Standardname der geschachtelten Tabelle ist der Name der geschachtelten Dimension. Sie können jedoch die geschachtelte Tabelle und die darin befindlichen Spalten umbenennen. Wiederholen Sie diesen Prozess, um der Miningstruktur mehrere geschachtelte Tabellen hinzuzufügen.  
  
 Die Möglichkeit, geschachtelte Tabellendaten wie diese zu verwenden, ist eine besonders leistungsstarke Funktion von SQL Server Data Mining. In einem Cube bestehen nahezu unbegrenzte Möglichkeiten, verwandte Datenteilmengen zu verwenden.  
  
##  <a name="bkmk_DMDimension"></a> Grundlegendes zu Data Mining-Dimensionen und Drillthrough  
 Beim Durchsuchen des Modells können Sie mithilfe der Option **Drillthrough zulassen**Abfragen in den zugrunde liegenden Cubedaten ausführen. Die Daten sind nicht in der neuen Data Mining-Dimension enthalten, aber die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank kann mithilfe der Datenbindungen Informationen aus dem Quellcube abrufen.  
  
 Mit der Option **Miningmodelldimension erstellen**können Sie eine neue Dimension innerhalb des vorhandenen Cubes generieren, die die vom Algorithmus ermittelten Muster enthält. Die Hierarchie innerhalb der neuen Dimension wird zu einem Großteil durch den Modelltyp bestimmt. Die Darstellung eines Clusteringmodells ist beispielsweise recht flach. Dabei befindet sich der Knoten "(Alle)" auf der ersten Hierarchieebene und die einzelnen Cluster in der nächsten Ebene. Im Gegensatz dazu kann die Dimension, die für ein Entscheidungsstrukturmodell erstellt wird, über eine sehr tiefe Hierarchie verfügen und die Verzweigung der Struktur darstellen.  
  
 Die Option **Cube mithilfe der Miningmodelldimension erstellen**versetzt Sie in die Lage, die neue Data Mining-Dimension in einen neuen Cube zu exportieren. Alle Objekte, die für ein Drillthrough der Data Mining-Dimension erforderlich sind, werden automatisch eingeschlossen.  
  
> [!WARNING]  
>  Die Erstellung von Data Mining-Dimensionen wird nur von den folgenden Modelltypen unterstützt: Modelle auf Grundlage des Microsoft Clustering-Algorithmus, des Microsoft Decision Trees-Algorithmus oder des Microsoft Associations-Algorithmus.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningstrukturspalten](mining-structure-columns.md)   
 [Miningmodellspalten](mining-model-columns.md)   
 [Miningmodelleigenschaften](mining-model-properties.md)   
 [Eigenschaften für Miningstrukturen und Strukturspalten](properties-for-mining-structure-and-structure-columns.md)  
  
  
