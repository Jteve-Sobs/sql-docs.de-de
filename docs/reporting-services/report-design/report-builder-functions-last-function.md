---
title: Last-Funktion (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 123b78a0-d6c9-4f78-b0e7-73b21854a250
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6f6a30101e4ee1472845d11dc1ab6b7cb3d70bc5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65579540"
---
# <a name="report-builder-functions---last-function"></a>Funktionen des Berichts-Generators: Last-Funktion
  Gibt den letzten Wert im festgelegten Bereich des angegebenen Ausdrucks zurück.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Last(expression, scope)  
```  
  
#### <a name="parameters"></a>Parameter  
 *expression*  
 (**Variant** oder **Binär**) Der Ausdruck, für den die Aggregation auszuführen ist. Beispiel: `=Fields!Fieldname.Value`.  
  
 *Bereich*  
 (**Zeichenfolge**) (optional) Der Name eines Datasets, eines Datenbereichs oder einer Gruppe mit den Berichtselementen, auf die die Funktion anzuwenden ist. Wenn *scope* nicht angegeben ist, wird der aktuelle Bereich verwendet.  
  
## <a name="return-type"></a>Rückgabetyp  
 Wird durch den Typ des Ausdrucks bestimmt.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Last** -Funktion gibt den letzten Wert in einem Satz von Daten zurück, nachdem alle Sortierfunktionen und Filter im angegebenen Bereich angewendet wurden.  
  
 Die **Last** -Funktion kann nur in Gruppenfilterausdrücken mit dem aktuellen (Standard-) Bereich verwendet werden.  
  
 Sie können die **Last** -Funktion auch in einem Seitenkopf verwenden, um den letzten Wert der **ReportItems** -Sammlung für eine Seite zurückzugeben und Überschriften im Wörterbuchformat zu erstellen, die den ersten und den letzten Eintrag auf einer Seite anzeigen.  
  
 Der Wert des *scope* -Objekts muss eine Zeichenfolgenkonstante sein und darf kein Ausdruck sein. Für äußere Aggregate oder Aggregate, die keine anderen Aggregate angeben, muss das *scope* -Objekt auf den aktuellen Bereich oder einen enthaltenen Bereich verweisen. Bei Aggregaten von Aggregaten können geschachtelte Aggregate einen untergeordneten Bereich angeben.  
  
 Das*Expression* -Objekt kann Aufrufe von geschachtelten Aggregatfunktionen enthalten. Dabei gelten folgende Ausnahmen und Bedingungen:  
  
-   Das*Scope* -Objekt für geschachtelte Aggregate muss dem Bereich des äußeren Aggregats entsprechen oder darin enthalten sein. In allen eindeutigen Bereichen des Ausdrucks muss ein Bereich eine untergeordnete Beziehung zu allen anderen Bereichen haben.  
  
-   Das*Scope* -Objekt für geschachtelte Aggregate darf nicht der Name eines Datasets sein.  
  
-   Das*Expression* -Objekt darf die Funktionen **First**, **Last**, **Previous**oder **RunningValue** nicht enthalten.  
  
-   Das*Expression* -Objekt darf keine geschachtelten Aggregate enthalten, die ein *recursive*-Objekt angeben.  
  
 Weitere Informationen finden Sie in der [Aggregatfunktionsreferenz (Berichts-Generator und SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) und unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Auflistungen (Berichts-Generator und SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Weitere Informationen zu rekursiven Aggregaten finden Sie unter [Creating Recursive Hierarchy Groups (Report Builder and SSRS) (Erstellen von rekursiven Hierarchiegruppen (Berichts-Generator und SSRS))](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt die letzte Produktnummer in der `Category` -Gruppe eines Datenbereichs zurück.  
  
```  
=Last(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucksverwendungen in Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Datentypen in Ausdrücken (Berichts-Generator und SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
