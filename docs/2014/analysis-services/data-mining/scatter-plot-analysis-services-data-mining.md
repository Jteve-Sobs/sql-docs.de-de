---
title: Punkt Diagramm (Analysis Services-Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- charts [Analysis Services]
- mining models [Analysis Services], validating
- scatter charts
- regression algorithms [Analysis Services]
ms.assetid: 166812ec-fd1c-47c8-88db-d5041142be91
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1ea37a9aecda0b3fbb6d61f7ba14a82f368c95aa
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175177"
---
# <a name="scatter-plot-analysis-services---data-mining"></a>Punktdiagramm (Analysis Services &ndash; Data Mining)
  Ein *Punktdiagramm* stellt die Istwerte in den Daten im Vergleich zu den vom Modell vorhergesagten Werten grafisch dar. Das Punktdiagramm zeigt die Istwerte auf der X-Achse und die vorhergesagten Werte auf der Y-Achse an. Es wird auch eine Linie dargestellt, die die perfekte Vorhersage darstellt, bei der der vorhergesagte Wert exakt mit dem Istwert übereinstimmt. Der Abstand eines Punkts von dieser Ideallinie (die in einem 45°-Winkel verläuft) gibt an, wie gut oder schlecht die Vorhersage war.

## <a name="understanding-the-scatter-plot"></a>Grundlegendes zum Punktdiagramm
 Betrachten Sie beispielsweise ein Modell, in dem die Marketingabteilung den Tagesumsatz anhand der Anzahl von Klicks auf einen Link, der in einer Werbe-E-Mail gesendet wird, vorhersagt. Da die Anzahl der Klicks und die Verkaufsmenge kontinuierliche numerische Werte sind, können Sie die Anzahl der Klicks als unabhängige Variable und die Verkaufsmenge als abhängige Variable grafisch darstellen. Dabei kennzeichnet die gerade Linie die erwartete lineare Beziehung, und die Punkte um diese Linie zeigen, inwieweit die tatsächlichen Daten vom Erwartungswert abweichen. Mit dieser Analyse können Sie unmittelbar erkennen, wie stark ein Ergebnissatz mit einer bestimmten Eingabe korreliert und wie groß die Abweichung vom Idealmodell ist.

## <a name="interpreting-the-results"></a>Interpretieren der Ergebnisse
 Das folgende Diagramm zeigt ein Beispiel für ein Punktdiagramm, das für das zuvor beschriebene Szenario erstellt wurde.

 ![Beispiel eines Punktdiagramms für lineare Regression](../media/scatterplot-callctr.gif "Beispiel eines Punktdiagramms für lineare Regression")

 Sie können mit der Maus auf jeden Punkt um die Linie zeigen, um die vorhergesagten Werte und die Istwerte als QuickInfo anzuzeigen. Es gibt keine **Mininglegende** für ein Punktdiagramm, das Diagramm selbst enthält jedoch eine Legende, in der die mit dem Modell verbundenen Ergebnisse angezeigt werden. Weitere Informationen zur Interpretation des Ergebnisses finden Sie unter [Miningmodellinhalt von linearen Regressionsmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).

 Sie können die visuelle Darstellung des Diagramms in die Zwischenablage kopieren, wobei jedoch nicht die zugrunde liegenden Daten oder die Formel kopiert werden. Wenn Sie die Regressionsformel für die Linie anzeigen möchten, können Sie für das Modell eine Inhaltsabfrage durchführen. Weitere Informationen finden Sie unter [Beispiele für lineare Regressionsmodellabfrage](linear-regression-model-query-examples.md).

## <a name="restrictions-on-scatter-plots"></a>Einschränkungen bei Punktdiagrammen
 Ein Punktdiagramm kann nur erstellt werden, wenn das Modell, das Sie auf der Registerkarte **Eingabeauswahl** auswählen, ein kontinuierliches vorhersagbares Attribut enthält. Sie müssen keine zusätzliche Auswahl treffen. Der Diagrammtyp des Punktdiagramms wird automatisch auf der Registerkarte **Prognosegütediagramm** auf Grundlage des Modells und Attributtyps angezeigt.

 Zeitreihenmodelle sagen zwar fortlaufende Nummern vorher, Sie können die Genauigkeit eines Zeitreihenmodells jedoch nicht mit einem Punktdiagramm messen. Sie können hierfür aber andere Methoden verwenden, z. B. das Reservieren eines Teiles der Vergangenheitsdaten. Weitere Informationen finden Sie unter [Abfragebeispiel Zeitreihenmodell](time-series-model-query-examples.md).

## <a name="related-content"></a>Verwandte Inhalte
 Die folgenden Themen enthalten weitere Informationen zum Erstellen und Verwenden von Punktdiagrammen und zugehörigen Genauigkeitsdiagrammen.

|Themen|Links|
|------------|-----------|
|Bietet eine exemplarische Vorgehensweise zum Erstellen eines Prognosegütediagramms für das Targeted Mailing-Modell.|[Lernprogramm zu Data Mining-Grundlagen](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [Testen der Genauigkeit mit Lift Charts &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|
|Erläutert verwandte Diagrammtypen.|[Lift Chart &#40;Analysis Services-Data Mining-&#41;](lift-chart-analysis-services-data-mining.md)<br /><br /> [Gewinn Diagramm &#40;Analysis Services-Data Mining-&#41;](profit-chart-analysis-services-data-mining.md)<br /><br /> [Klassifizierungs Matrix &#40;Analysis Services Data Mining-&#41;](classification-matrix-analysis-services-data-mining.md)|
|Beschreibt die Verwendungsmöglichkeiten für die Kreuzvalidierung bei Miningmodellen und Miningstrukturen.|[Übergreifende Überprüfung &#40;Analysis Services Data Mining-&#41;](cross-validation-analysis-services-data-mining.md)|
|Beschreibt Schritte zum Erstellen von Prognosegütediagrammen und anderen Genauigkeitsdiagrammen.|[Test-und validierungsaufgaben und Anleitungen &#40;Data Mining-&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)|

## <a name="see-also"></a>Weitere Informationen
 [Testen und validieren &#40;Data Mining-&#41;](testing-and-validation-data-mining.md)


