---
title: Lernprogramm zu Datamining-Grundlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d434df95a26485d4d7795d3ab960b8d2457b8ff6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63185574"
---
# <a name="basic-data-mining-tutorial"></a>Lernprogramm zu Data Mining-Grundlagen
  Willkommen beim [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Lernprogramm zu Data Mining-Grundlagen. [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Stellt eine integrierte Umgebung für Datamining-Modelle erstellen und Vorhersagen bereit. In diesem Lernprogramm führen Sie ein Szenario für eine zielgerichtete Mailingkampagne aus, indem Sie Computerlernverfahren verwenden, um das Kaufverhalten von Kunden zu analysieren und vorherzusagen. Im Lernprogramm wird die Verwendung von drei der wichtigsten Data Mining-Algorithmen veranschaulicht: Clustering, Entscheidungsstrukturen und Naive Bayes. Sie erfahren außerdem, wie Ergebnisse mit den Miningmodell-Viewern analysiert und Vorhersagen und Genauigkeitsdiagramme mit den in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]enthaltenen Data Mining-Tools erstellt werden. In allen Beispielen wird das fiktive Unternehmen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]verwendet.  
  
 Wenn Sie mit den Datamining-Tools vertraut sind, es wird empfohlen, dass Sie auch Abschließen der [Data Mining-Lernprogramm für fortgeschrittene &#40;Analysis Services – Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md). In den Lektionen wird die Verwendung von Vorhersagen, Warenkorbanalysen, Zeitreihen, Zuordnungsmodellen, geschachtelten Tabellen und Sequence Clustering veranschaulicht.  
  
## <a name="tutorial-scenario"></a>Lernprogrammszenario  
 In diesem Lernprogramm sind Sie Mitarbeiter von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] , der beauftragt wurde, anhand ihrer bisherigen Käufe mehr über die Kunden des Unternehmens zu erfahren und mithilfe dieser historischen Daten Vorhersagen zu treffen, die für das Marketing verwendet werden können. Das Unternehmen hat noch nie zuvor Data Mining ausgeführt. Daher müssen Sie eigens für das Data Mining eine neue Datenbank anlegen und mehrere Data Mining-Modelle einrichten.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie Sie verschiedene Typen von Computerlernmethoden entwickeln und verwenden. Sie lernen außerdem, wie Sie eine Kopie eines Miningmodells erstellen und einen Filter auf die Eingabedaten anwenden, um unterschiedliche Ergebnisse zu erhalten. Anschließend können Sie die Ergebnisse beider Modelle mit einem Prognosegütediagramm vergleichen. Zum Schluss rufen Sie mit der Drillthroughfunktion weitere Daten aus der zugrunde liegenden Miningstruktur ab.  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datamining umfasst die folgenden Features, mit denen Sie ganz einfach entwickeln und vergleichen Sie mehrere Vorhersagemodelle und klicken Sie dann die Ergebnisse entsprechende Maßnahmen ergreifen:  
  
-   *Zurückhaltungstestsätze*– Beim Erstellen einer Miningstruktur können Sie nun die darin enthaltenen Daten in Trainings- und Testsätze aufteilen. Auf diese Weise können Sie Modelle an ähnlichen Datasets testen und die Genauigkeit verwandter Modelle testen.  
  
-   *Miningmodellfilter*– Sie können nun Filter an ein Miningmodell anfügen und diese beim Trainieren und Testen anwenden. Dies erleichtert die Erstellung verwandter Modelle für unterschiedliche Teilmengen der Daten.  
  
-   *Drillthrough zu Strukturfällen und Strukturspalten* – Sie können nun einfach von allgemeinen Mustern im Miningmodell zu aussagekräftigen Details in der Datenquelle wechseln.  
  
 Dieses Lernprogramm ist in die folgenden Lektionen aufgeteilt:  
  
 [Lektion 1: Vorbereiten der Analysis Services-Datenbank &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 In dieser Lektion lernen Sie, wie Sie eine neue [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank anlegen, eine Datenquelle und Datenquellensicht hinzufügen und die neue Datenbank für die Verwendung von Data Mining vorbereiten.  
  
 [Lektion 2: Erstellen einer Targeted Mailing-Struktur &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 In dieser Lektion erfahren Sie, wie Sie eine Miningmodellstruktur anlegen, die in einem Targeted Mailing-Szenario verwendet werden kann.  
  
 [Lektion 3: Hinzufügen und Verarbeiten von Modellen](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 In dieser Lektion erfahren Sie, wie einer Struktur Modelle hinzugefügt werden. Die Modelle, die Sie erstellen, werden mit den folgenden Algorithmen erstellt:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes  
  
 [Lektion 4: Untersuchen der Targeted Mailing-Modelle &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 In dieser Lektion lernen Sie, die Ergebnisse der einzelnen Modelle mit Viewern zu untersuchen und zu interpretieren.  
  
 [Lesson 5: Testen von Modellen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 In dieser Lektion erstellen Sie eine Kopie des Targeted Mailing-Modells, fügen einen Miningmodellfilter hinzu, um die Trainingsdaten auf eine bestimmte Kundengruppe zu beschränken und bewerten anschließend die Verwendbarkeit des Modells.  
  
 [Lektion 6: Erstellen und Verwenden von Vorhersagen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 In der Abschlusslektion des Lernprogramms zu Data Mining-Grundlagen sagen Sie anhand des Modells voraus, welche Kunden am wahrscheinlichsten ein Fahrrad kaufen werden. Danach führen Sie einen Drillthrough zu den zugrunde liegenden Fällen durch, um die Kontaktinformationen abzurufen.  
  
## <a name="requirements"></a>Anforderungen  
 Stellen Sie sicher, dass Folgendes installiert ist:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] im mehrdimensionalen Modus  
  
-   Die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank.  
  
 Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht zusammen mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]installiert. Um die offiziellen Beispieldatenbanken für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu installieren, rufen Sie die Seite [Microsoft SQL-Beispieldatenbanken](https://go.microsoft.com/fwlink/?LinkId=88417) auf und wählen Sie [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]aus.  
  
> [!NOTE]  
>  Wenn Sie ein Lernprogramm durcharbeiten, Sie finden es vielleicht einfacher zwischen den einzelnen Schritten hin und her verschoben wird, wenn Sie beim Hinzufügen der **nächsten Thema** und **Vorheriges Thema** in der Symbolleiste der Dokumentanzeige die Schaltflächen.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Projektmappen](../../2014/analysis-services/data-mining/data-mining-solutions.md)   
 [Miningmodelltasks und Anweisungen](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Das Erstellen und Abfragen von Datamining-Modellen mit DMX: Lernprogramme &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  
