---
title: SELECT FROM &lt;Modell&gt;. INHALT (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 63cd10aaddfb0a22f8942e48007d36f8e634b233
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67906737"
---
# <a name="select-from-ltmodelgtcontent-dmx"></a>SELECT FROM &lt;Modell&gt;. INHALT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt das Miningmodell-Schemarowset für das angegebene Data Mining-Modell zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CONTENT   
[WHERE <condition expression>]  
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argumente  
 *n*  
 Optional. Eine ganze Zahl, die angibt, wie viele Zeilen zurückgegeben werden sollen.  
  
 *Liste mit Ausdrücken*  
 Eine durch Trennzeichen getrennte Liste mit Spalten, die aus dem Schemarowset des Inhalts abgeleitet wurden.  
  
 *model*  
 Ein Modellbezeichner.  
  
 *Bedingungsausdruck*  
 Dies ist optional. Eine Bedingung, die die Werte einschränkt, die für die Spaltenliste zurückgegeben werden.  
  
 *expression*  
 Dies ist optional. Ein Ausdruck, der einen Skalarwert zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **SELECT FROM**  _\<Modell >_ **. Inhalt** -Anweisung gibt Inhalt, der für jeden Algorithmus spezifischen zurück. Angenommen, Sie möchten die Beschreibungen aller Regeln eines Modells für Zuordnungsregeln in einer benutzerdefinierten Anwendung verwenden. Sie können eine **SELECT FROM \<Modell >. Inhalt** Anweisung zum Zurückgeben von Werten in der NODE_RULE-Spalte des Modells.  
  
 In der folgenden Tabelle sind die im Miningmodellinhalt enthaltenen Spalten aufgeführt.  
  
> [!NOTE]  
>  Algorithmen können die Spalten unterschiedlich auswerten, um den Inhalt richtig darzustellen. Eine Beschreibung der für jeden Algorithmus und Tipps zur Interpretation und Abfrage für jeden Modelltyp Inhalt des Miningmodells Inhalt des Miningmodells, finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md).  
  
|CONTENT-Rowsetspalte|Beschreibung|  
|---------------------------|-----------------|  
|MODEL_CATALOG|Ein Katalogname. NULL, wenn der Anbieter Kataloge nicht unterstützt.|  
|MODEL_SCHEMA|Ein nicht qualifizierter Schemaname. NULL, wenn der Anbieter Schemas nicht unterstützt.|  
|MODEL_NAME|Ein Modellname. Diese Spalte darf keinen NULL-Wert enthalten.|  
|ATTRIBUTE_NAME|Der Name des Attributs, das dem Knoten entspricht.|  
|NODE_NAME|Der Name des Knotens.|  
|NODE_UNIQUE_NAME|Der eindeutige Name des Knotens innerhalb des Modells.|  
|NODE_TYPE|Eine ganze Zahl, die den Typ des Knotens darstellt. .|  
|NODE_GUID|Der GUID (Globally Unique Identifier) des Knotens. NULL, wenn es keinen GUID gibt.|  
|NODE_CAPTION|Eine Bezeichnung oder Beschriftung, die dem Knoten zugeordnet ist. Wird hauptsächlich für Anzeigezwecke verwendet. Ist keine Beschriftung vorhanden, wird NODE_NAME zurückgegeben.|  
|CHILDREN_CARDINALITY|Die Anzahl der untergeordneten Elemente des Knotens.|  
|PARENT_UNIQUE_NAME|Der eindeutige Name des dem Knoten übergeordneten Elements.|  
|NODE_DESCRIPTION|Eine Beschreibung des Knotens.|  
|NODE_RULE|Ein XML-Fragment, das die im Knoten eingebettete Regel darstellt. Das Format der XML-Zeichenfolge basiert auf dem PMML-Standard.|  
|MARGINAL_RULE|Ein XML-Fragment, das den Pfad vom übergeordneten Element zum Knoten beschreibt.|  
|NODE_PROBABILITY|Die Wahrscheinlichkeit des in dem Knoten endenden Pfads.|  
|MARGINAL_PROBABILITY|Die Wahrscheinlichkeit für das Erreichen des Knotens vom übergeordneten Knoten aus.|  
|NODE_DISTRIBUTION|Eine Tabelle, die Statistiken enthält, die die Verteilung der Werte in dem Knoten beschreibt.|  
|NODE_SUPPORT|Die Anzahl von Fällen im Unterstützungswert dieses Knotens.|  
  
## <a name="examples"></a>Beispiele  
 Der folgende Code gibt die ID des übergeordneten Knotens des Entscheidungsstrukturmodells zurück, das der Targeted Mailing-Miningstruktur hinzugefügt wurde.  
  
```  
SELECT MODEL_NAME, NODE_NAME FROM [TM Decision Tree].CONTENT  
WHERE NODE_TYPE = 1  
```  
  
 Erwartete Ergebnisse:  
  
|MODEL_NAME|NODE_NAME|  
|-----------------|----------------|  
|TM_DecisionTree|0|  
  
 Die folgende Abfrage verwendet die **IsDescendant** Funktion, um die unmittelbar untergeordneten Elemente des Knotens zurückzugeben, die in der vorherigen Abfrage zurückgegeben wurde.  
  
> [!NOTE]  
>  Da der Wert von NODE_NAME eine Zeichenfolge ist, können keine untergeordneten select-Anweisung zurückzugebenden die NODE_ID als Argument an die **IsDescendant** Funktion.  
  
```  
SELECT NODE_NAME, NODETYPE, NODE_CAPTION   
FROM [TM Decision Tree].CONTENT  
WHERE ISDESCENDANT('0')  
```  
  
 Erwartete Ergebnisse:  
  
 Da das Modell ein Entscheidungsstrukturmodell ist, enthalten die nachfolgenden Elemente des übergeordneten Knotens des Modells einen einzelnen Knoten für Randstatistik, einen Knoten, der das vorhersagbare Attribut darstellt, und mehrere Knoten, die Eingabeattribute und Werte enthalten. Weitere Informationen finden Sie unter [Miningmodellinhalt von Entscheidungsstrukturmodellen &#40;Analysis Services – Data Mining&#41;](../analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).  
  
## <a name="using-the-flattened-keyword"></a>Verwenden des FLATTENED-Schlüsselworts  
 Der Miningmodellinhalt enthält in geschachtelten Tabellenspalten häufig interessante Informationen über das Modell. Mithilfe des FLATTENED-Schlüsselworts können Sie Daten aus geschachtelten Tabellen abrufen, ohne einen Anbieter zu benötigen, der hierarchische Rowsets unterstützt.  
  
 Die folgende Abfrage gibt einen einzelnen Knoten zurück, den Knoten für Randstatistik (NODE_TYPE = 26) aus einem Naïve Bayes-Modell. Dieser Knoten enthält eine geschachtelte Tabelle in der NODE_DISTRIBUTION-Spalte. Als Ergebnis wird die geschachtelte Tabellenspalte vereinfacht, und es wird für jede Zeile in der geschachtelten Tabelle eine Zeile zurückgegeben. Der Wert der skalaren Spalte MODEL_NAME wird für jede Zeile in der geschachtelten Tabelle wiederholt.  
  
 Beachten Sie, dass für jede Spalte in der geschachtelten Tabelle eine neue Spalte zurückgegeben wird, wenn Sie nur den Namen der geschachtelten Tabellenspalte festlegen. Standardmäßig wird der Name der geschachtelten Tabelle dem Namen einer jeden geschachtelten Tabellenspalte vorangestellt.  
  
```  
SELECT FLATTENED MODEL_NAME, NODE_DISTRIBUTION  
FROM [TM_NaiveBayes].CONTENT  
WHERE NODE_TYPE = 26  
```  
  
 Beispielergebnisse:  
  
|MODEL_NAME|NODE_DISTRIBUTION.ATTRIBUTE_NAME|NODE_DISTRIBUTION.ATTRIBUTE_VALUE|NODE_DISTRIBUTION.SUPPORT|NODE_DISTRIBUTION.PROBABILITY|NODE_DISTRIBUTION.VARIANCE|NODE_DISTRIBUTION.VALUETYPE|  
|-----------------|----------------------------------------|-----------------------------------------|--------------------------------|------------------------------------|---------------------------------|----------------------------------|  
|TM_NaiveBayes|Bike Buyer|Missing|0|0|0|1|  
|TM_NaiveBayes|Bike Buyer|0|6556|0.506685215240745|0||  
|TM_NaiveBayes|Bike Buyer|1|6383|0.493314784759255|0||  
  
 Im folgenden Beispiel wird erläutert, wie mithilfe der untergeordneten SELECT-Anweisung nur einige der Spalten aus der geschachtelten Tabelle zurückgegeben werden. Sie können die Anzeige durch Aliasing des Tabellennamens der geschachtelten Tabelle wie dargestellt vereinfachen.  
  
```  
SELECT MODEL_NAME,   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT] AS t  
FROM NODE_DISTRIBUTION)   
FROM TM_NaiveBayes.CONTENT  
WHERE NODE_TYPE = 26  
```  
  
 Beispielergebnisse:  
  
|MODEL_NAME|T.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|  
|-----------------|-----------------------|------------------------|---------------|  
|TM_NaiveBayes|Bike Buyer|Missing|0|  
|TM_NaiveBayes|Bike Buyer|0|6556|  
|TM_NaiveBayes|Bike Buyer|1|6383|  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
