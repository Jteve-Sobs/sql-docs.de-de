---
title: PredictTimeSeries (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d8562661e313aea59dfb233dbc5b2194b582c2d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62659173"
---
# <a name="predicttimeseries-dmx"></a>PredictTimeSeries (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt vorhergesagte Zukunftswerte für Zeitreihendaten zurück. Zeitreihendaten sind kontinuierlich und können in einer geschachtelten Tabelle oder in einer Falltabelle gespeichert werden. Die **PredictTimeSeries** Funktion immer eine geschachtelte Tabelle zurückgibt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PredictTimeSeries(<table column reference>)  
PredictTimeSeries(<table column reference>, n)  
PredictTimeSeries(<table column reference>, n-start, n-end)  
PredictTimeSeries(<scalar column reference>)  
PredictTimeSeries(<scalar column reference>, n)  
PredictTimeSeries(<scalar column reference>, n-start, n-end)  
PredictTimeSeries(<table column reference>, n, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<table column reference>, n-start, n-end, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<scalar column reference>, n, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
PredictTimeSeries(<scalar column reference>, n-start, n-end, REPLACE_MODEL_CASES | EXTEND_MODEL_CASES) PREDICTION JOIN <source query>  
```  
  
## <a name="arguments"></a>Argumente  
 *\<Tabellenreferenz für die Spalte >* ,  *\<skalare Spalte auf >*  
 Gibt den Namen der vorherzusagenden Spalte an. Die Spalte kann entweder Skalar- oder Tabellendaten enthalten.  
  
 *n*  
 Gibt die Anzahl der nächsten vorherzusagenden Schritte an. Wenn ein Wert nicht angegeben wird, für die *n*, der Standardwert ist 1.  
  
 *n* darf nicht 0 sein. Die Funktion gibt einen Fehler zurück, wenn Sie nicht wenigstens eine Vorhersage machen.  
  
 *n-start, n-end*  
 Gibt einen Bereich von Zeitreihenschritten an.  
  
 *für die ersten n* muss eine ganze Zahl sein und darf nicht 0 sein.  
  
 *n-Ende-* muss eine ganze Zahl größer sein als *für die ersten n*.  
  
 *\<Quellabfrage >*  
 Definiert die externen Daten, die für Vorhersagen verwendet werden.  
  
 REPLACE_MODEL_CASES | EXTEND_MODEL_CASES  
 Gibt an, wie neue Daten verarbeitet werden.  
  
 REPLACE_MODEL_CASES gibt an, dass die Datenpunkte im Modell durch neue Daten ersetzt werden sollen. Vorhersagen basieren jedoch auf den Mustern im vorhandenen Miningmodell.  
  
 EXTEND_MODEL_CASES gibt an, dass die neuen Daten dem ursprünglichen Trainingsdataset hinzugefügt werden sollen. Zukünftige Vorhersagen werden erst nach Verwendung der neuen Dateien basierend auf dem zusammengesetzten Dataset getroffen.  
  
 Diese Argumente können nur verwendet werden, wenn neue Daten mit einer PREDICTION JOIN-Anweisung hinzugefügt werden. Wenn Sie eine PREDICTION JOIN-Abfrage verwenden und kein Argument angeben, lautet der Standardwert EXTEND_MODEL_CASES.  
  
## <a name="return-type"></a>Rückgabetyp  
 Ein \< *Tabellenausdruck*>.  
  
## <a name="remarks"></a>Hinweise  
 Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus unterstützt keine Vergangenheitsvorhersage, wenn Sie die PREDICTION JOIN-Anweisung zum Hinzufügen neuer Daten verwenden.  
  
 In einer PREDICTION JOIN-Anweisung beginnt die Vorhersage stets mit dem Zeitschritt unmittelbar nach dem Ende der ursprünglichen Trainingsreihe. Dies gilt auch dann, wenn Sie neue Daten hinzufügen. Aus diesem Grund die *n* Parameter und *für die ersten n* Parameterwerte müssen eine ganze Zahl größer als 0 sein.  
  
> [!NOTE]  
>  Die Länge der neuen Daten beeinflusst den Ausgangspunkt für die Vorhersage nicht. Wenn Sie daher neue Daten hinzufügen und außerdem neue Vorhersagen vornehmen möchten, stellen Sie sicher, dass Sie entweder den Ausgangspunkt für die Vorhersage auf einen Wert größer als die Länge der neuen Daten festlegen oder den Endpunkt der Vorhersage um die Länge der neuen Daten erweitern.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen wird veranschaulicht, wie Vorhersagen aufgrund eines vorhandenen Zeitreihenmodells getroffen werden:  
  
-   Im ersten Beispiel wird gezeigt, wie eine festgelegte Anzahl von Vorhersagen auf Grundlage des aktuellen Modells getroffen wird.  
  
-   Im zweiten Beispiel wird gezeigt, wie Sie mit dem REPLACE_MODEL_CASES-Parameter die Muster im angegebenen Modell auf einen neuen Satz Daten anwenden.  
  
-   Im dritten Beispiel wird gezeigt, wie Sie mit dem EXTEND_MODEL_CASES-Parameter ein Miningmodell mit neuen Daten aktualisieren.  
  
 Weitere Informationen zum Arbeiten mit zeitreihenmodellen finden Sie unter dem Datamining-Lernprogramm [Lektion 2: Erstellen eines Planungserstellungsszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41; ](https://msdn.microsoft.com/library/9a988156-c900-4c22-97fa-f6b0c1aea9e2) und [Zeit DMX-Lernprogramm für Zeitreihenvorhersagen](https://msdn.microsoft.com/library/38ea7c03-4754-4e71-896a-f68cc2c98ce2).  
  
> [!NOTE]  
>  Ihr Modell liefert ggf. andere Ergebnisse. Die Ergebnisse der nachfolgenden Beispiele dienen lediglich zum Veranschaulichen des Ergebnisformats.  
  
### <a name="example-1-predicting-a-number-of-time-slices"></a>Beispiel 1: Vorhersagen einer Anzahl von Zeitscheiben  
 Im folgenden Beispiel wird die **PredictTimeSeries** -Funktion zum Zurückgeben einer Vorhersage für die nächsten drei Zeitschritte und Ergebnisse werden auf die Reihe m200 in den Regionen Europa und Pazifik beschränkt. In diesem speziellen Modell wird ist das vorhersagbare Attribut-Menge, daher müssen Sie verwenden `[Quantity]` als erstes Argument an die PredictTimeSeries-Funktion.  
  
```  
SELECT FLATTENED  
    [Forecasting].[Model Region],  
    PredictTimeSeries([Forecasting].[Quantity],3)AS t   
FROM  
    [Forecasting]  
WHERE [Model Region] = 'M200 Europe'  
OR [Model Region] = 'M200 Pacific'  
```  
  
 Erwartete Ergebnisse:  
  
|Model Region|t.$TIME|t.Quantity|  
|------------------|-------------|----------------|  
|M200 Europe|7/25/2008 12:00:00 AM|121|  
|M200 Europe|8/25/2008 12:00:00 AM|142|  
|M200 Europe|9/25/2008 12:00:00 AM|152|  
|M200 Pacific|7/25/2008 12:00:00 AM|46|  
|M200 Pacific|8/25/2008 12:00:00 AM|44|  
|M200 Pacific|9/25/2008 12:00:00 AM|42|  
  
 In diesem Beispiel wurde das FLATTENED-Schlüsselwort verwendet, um die Ergebnisse übersichtlicher wiederzugeben.  Wenn Sie das FLATTENED-Schlüsselwort nicht verwenden und stattdessen ein hierarchisches Rowset zurückgeben, gibt diese Abfrage zwei Spalten zurück. Die erste Spalte enthält den Wert für [ModelRegion] und die zweite Spalte enthält eine geschachtelte Tabelle mit zwei Spalten: $TIME für die vorhergesagten Zeitscheiben und Quantity für die vorhergesagten Werte.  
  
### <a name="example-2-adding-new-data-and-using-replacemodelcases"></a>Beispiel 2: Neue Daten hinzufügen und Verwenden von REPLACE_MODEL_CASES  
 Angenommen Sie stellen fest, dass die Daten für eine bestimmte Region falsch waren. Sie möchten aber die Muster im Modell verwenden und die Vorhersagen entsprechend den neuen Daten anpassen. Oder Sie stellen fest, dass eine andere Region zuverlässigere Trends liefert, und möchten das zuverlässigste Modell auf Daten aus einer anderen Region anwenden.  
  
 In solchen Szenarien können Sie den REPLACE_MODEL_CASES-Parameter verwenden und einen neuen Satz Daten angeben, der als Vergangenheitsdaten verwendet werden soll. Auf diese Weise basieren die Projektionen auf den Mustern im angegebenen Modell, werden jedoch nahtlos am Ende der neuen Datenpunkte fortgesetzt. Eine vollständige Exemplarische Vorgehensweise dieses Szenarios finden Sie unter [erweiterte Zeitreihenvorhersagen &#40;Data Mining Tutorial für fortgeschrittene&#41;](https://msdn.microsoft.com/library/b614ebdb-07ca-44af-a0ff-893364bd4b71).  
  
 Die folgende PREDICTION JOIN-Abfrage veranschaulicht die Syntax zum Ersetzen von Daten und Treffen neuer Vorhersagen. Im Beispiel wird für die Ersetzungsdaten der Wert der Spalten Amount und Quantity abgerufen und jeweils mit zwei multipliziert:  
  
```  
SELECT [Forecasting].[Model Region],  
    PredictTimeSeries([Forecasting].[Quantity], 3, REPLACE_MODEL_CASES)   
FROM  
    [Forecasting]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT [ModelRegion],   
    ([Quantity] * 2) as Quantity,  
    ([Amount] * 2) as Amount,  
      [ReportingDate]  
    FROM [dbo].vTimeSeries  
    WHERE ModelRegion = N''M200 Pacific''  
    ') AS t  
ON  
  [Forecasting].[Model Region] = t.[ Model Region] AND  
[Forecasting].[Reporting Date] = t.[ReportingDate] AND  
[Forecasting].[Quantity] = t.[Quantity] AND  
[Forecasting].[Amount] = t.[Amount]  
```  
  
 Die folgenden Tabellen vergleichen die Ergebnisse der Vorhersage.  
  
 Ursprüngliche Vorhersagen:  
  
||||  
|-|-|-|  
|M200 Pacific|7/25/2008 12:00:00 AM|46|  
|M200 Pacific|8/25/2008 12:00:00 AM|44|  
|M200 Pacific|9/25/2008 12:00:00 AM|42|  
  
 Aktualisierte Vorhersagen ausgibt:  
  
||||  
|-|-|-|  
|M200 Pacific|7/25/2008 12:00:00 AM|91|  
|M200 Pacific|8/25/2008 12:00:00 AM|89|  
|M200 Pacific|9/25/2008 12:00:00 AM|84|  
  
### <a name="example-3-adding-new-data-and-using-extendmodelcases"></a>Beispiel 3: Neue Daten hinzufügen und Verwenden von EXTEND_MODEL_CASES  
 Beispiel 3 veranschaulicht die Verwendung von der *EXTEND_MODEL_CASES* Option aus, um neue Daten bereitstellen, die an das Ende einer vorhandenen Datenreihe hinzugefügt wird. Statt die vorhandenen Datenpunkte zu ersetzen, werden die neuen Daten dem Modell hinzugefügt.  
  
 Im folgenden Beispiel werden die neuen Daten in der SELECT-Anweisung bereitgestellt, die auf NATURAL PREDICTION JOIN folgt. Sie können mit dieser Syntax mehrere Zeilen mit neuen Eingaben bereitstellen, jede neue Zeile muss jedoch einen eindeutigen Zeitstempel aufweisen:  
  
```  
SELECT [Model Region],  
    PredictTimeSeries([Forecasting].[Quantity], 5, EXTEND_MODEL_CASES)   
FROM  
    [Forecasting]  
NATURAL PREDICTION JOIN  
    (SELECT  
        1 as [Reporting Date],  
        10 as [Quantity],  
        'M200 Europe' AS [Model Region]  
    UNION SELECT   
        2 as [Reporting Date],  
        15 as [Quantity],  
        'M200 Europe' AS [Model Region]  
) AS T  
WHERE ([Model Region] = 'M200 Europe'  
 OR [Model Region] = 'M200 Pacific')  
```  
  
 Da die Abfrage verwendet die *EXTEND_MODEL_CASES* Option [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] führt die folgenden Aktionen für die Vorhersagen:  
  
-   Die Gesamtgröße der Trainingsfälle wird erhöht, indem die beiden neuen Datenmonate zum Modell hinzugefügt werden.  
  
-   Am Ende der vorherigen Falldaten werden die Vorhersagen gestartet. Daher stellen die ersten zwei Vorhersagen die neuen tatsächlichen Umsatzdaten dar, die Sie soeben zum Modell hinzugefügt haben.  
  
-   Es werden neue Vorhersagen für die verbleibenden drei Zeitscheiben auf Grundlage des neu erweiterten Modells zurückgegeben.  
  
 Die folgende Tabelle führt die Abfrageergebnisse von Beispiel 2 auf. Beachten Sie, dass die ersten zwei für M200 Europe zurückgegebenen Werte exakt mit den neuen Werten übereinstimmen, die Sie angegeben haben. Dieses Verhalten ist entwurfsbedingt. Wenn Sie die Vorsagen erst nach dem Ende der neuen Daten starten möchten, müssen Sie einen Anfangs- und Endzeitschritt angeben. Ein Beispiel dazu, finden Sie unter [Lektion 5: Erweitern des Zeitreihenmodells modellieren](https://msdn.microsoft.com/library/7aad4946-c903-4e25-88b9-b087c20cb67d).  
  
 Beachten Sie außerdem, dass für die Region Pazifik keine neuen Daten angegeben wurden. Deshalb gibt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] neue Vorhersagen für alle fünf Zeitscheiben zurück.  
  
 Menge: M200 Europe. EXTEND_MODEL_CASES:  
  
|$TIME|Quantity|  
|-----------|--------------|  
|7/25/2008 0:00|10|  
|8/25/2008 0:00|15|  
|9/25/2008 0:00|72|  
|10/25/2008 0:00|69|  
|11/25/2008 0:00|68|  
  
 Menge:  M200 Pacific. EXTEND_MODEL_CASES:  
  
|$TIME|Quantity|  
|-----------|--------------|  
|7/25/2008 0:00|46|  
|8/25/2008 0:00|44|  
|9/25/2008 0:00|42|  
|10/25/2008 0:00|42|  
|11/25/2008 0:00|38|  
  
## <a name="example-4-returning-statistics-in-a-time-series-prediction"></a>Beispiel 4: Zurückgeben der Statistik in einer Zeitreihenvorhersage  
 Die **PredictTimeSeries** -Funktion nicht unterstützt *INCLUDE_STATISTICS* als Parameter. Mit der folgenden Abfrage kann jedoch die Vorhersagestatistik für eine Zeitreihenabfrage zurückgegeben werden. Diese Methode kann auch mit Modellen verwendet werden, in denen geschachtelte Tabellenspalten enthalten sind.  
  
 In diesem speziellen Modell wird ist das vorhersagbare Attribut-Menge, daher müssen Sie verwenden `[Quantity]` als erstes Argument an die PredictTimeSeries-Funktion. Wenn Ihr Modell ein anderes vorhersagbares Attribut verwendet, können Sie den Spaltennamen durch einen anderen ersetzen.  
  
```  
SELECT FLATTENED [Model Region],  
(SELECT   
     $Time,  
     [Quantity] as [PREDICTION],   
     PredictVariance([Quantity]) AS [VARIANCE],  
     PredictStdev([Quantity]) AS [STDEV]  
FROM  
      PredictTimeSeries([Quantity], 3) AS t  
) AS t  
FROM Forecasting  
WHERE [Model Region] = 'M200 Europe'  
OR [Model Region] = 'M200 North America'  
```  
  
 Beispielergebnisse:  
  
|Model Region|t.$TIME|t.PREDICTION|t.VARIANCE|t.STDEV|  
|------------------|-------------|------------------|----------------|-------------|  
|M200 Europe|7/25/2008 12:00:00 AM|121|11.6050581415597|3.40661975300439|  
|M200 Europe|8/25/2008 12:00:00 AM|142|10.678201866621|3.26775180615374|  
|M200 Europe|9/25/2008 12:00:00 AM|152|9.86897842568614|3.14149302493037|  
|M200 North America|7/25/2008 12:00:00 AM|163|1.20434529288162|1.20434529288162|  
|M200 North America|8/25/2008 12:00:00 AM|178|1.65031343900634|1.65031343900634|  
|M200 North America|9/25/2008 12:00:00 AM|156|1.68969399185442|1.68969399185442|  
  
> [!NOTE]  
>  In diesem Beispiel wurde das FLATTENED-Schlüsselwort verwendet, um die Ergebnisse in der Tabelle übersichtlicher darzustellen. Wenn Ihr Anbieter jedoch hierarchische Rowsets unterstützt, können Sie das FLATTENED-Schlüsselwort auslassen. Bei Auslassung des FLATTENED-Schlüsselworts gibt die Abfrage zwei Spalten zurück. Die erste Spalte enthält den Wert, der die `[Model Region]`-Datenreihen angibt, und die zweite Spalte enthält die geschachtelte Tabelle mit der Statistik.  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Abfragebeispiel Zeitreihenmodell](../analysis-services/data-mining/time-series-model-query-examples.md)   
 [Predict &#40;DMX&#41;](../dmx/predict-dmx.md)  
  
  
