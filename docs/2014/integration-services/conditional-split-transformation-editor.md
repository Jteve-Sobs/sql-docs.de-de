---
title: Transformations-Editor für bedingtes Teilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 405d20ce5711f3e3378b0037b6d4c1f753a8f09c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434917"
---
# <a name="conditional-split-transformation-editor"></a>Transformations-Editor für bedingtes Teilen
  Mithilfe des Dialogfelds **Transformations-Editor für bedingtes Teilen** können Sie Ausdrücke erstellen, die Reihenfolge festlegen, in der Ausdrücke ausgewertet werden, und die Ausgaben des bedingten Teilens benennen. Dieses Dialogfeld schließt Funktionen und Operatoren für mathematische Berechnungen, Zeichenfolgen und Datum/Uhrzeit ein, die Sie für das Erstellen von Ausdrücken verwenden können. Die erste Bedingung, bei der die Auswertung den Wert TRUE ergibt, bestimmt die Ausgabe, an die eine Zeile geleitet wird.  
  
> [!NOTE]  
>  Die Transformation für bedingtes Teilen leitet jede Eingabezeile an nur eine Ausgabe. Wenn Sie mehrere Bedingungen eingeben, wird jede Zeile durch die Transformation an die erste Ausgabe gesendet, bei der die Bedingung erfüllt ist (TRUE). Dadurch bleiben alle folgenden Bedingungen für diese Zeile unberücksichtigt. Wenn mehrere Bedingungen aufeinander folgend ausgewertet werden sollen, dann müssen Sie mehrere Transformationen für bedingtes Teilen im Datenfluss miteinander verketten.  
  
 Weitere Informationen zur Transformation für bedingtes Teilen finden Sie unter [Transformation für bedingtes Teilen](data-flow/transformations/conditional-split-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Bestellung**  
 Wählen Sie eine Zeile aus, und verwenden Sie die Pfeiltasten auf der rechten Seite, um die Reihenfolge zu ändern, in der die Ausdrücke ausgewertet werden.  
  
 **Ausgabename**  
 Geben Sie einen Ausgabenamen an. Standardwert ist eine nummerierte Liste aus Fällen; Sie können jedoch einen eindeutigen, beschreibenden Namen auswählen.  
  
 **Bedingung**  
 Geben Sie einen Ausdruck ein, oder erstellen Sie einen, indem Sie aus der Liste der verfügbaren Spalten, Variablen, Funktionen und Operatoren die entsprechenden Teile ziehen.  
  
 Der Wert dieser Eigenschaft kann mithilfe eines Eigenschaftsausdrucks angegeben werden.  
  
 **Verwandte Themen:**  [Integration Services-Ausdrücke &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md), [Operatoren &#40;SSIS-Ausdruck&#41;](expressions/operators-ssis-expression.md) und [Funktionen &#40;SSIS-Ausdruck&#41;](expressions/functions-ssis-expression.md)  
  
 **Standardausgabename**  
 Geben Sie einen Namen für die Standardausgabe ein, oder verwenden Sie den Standardnamen.  
  
 **Fehlerausgabe konfigurieren**  
 Geben Sie mithilfe des Dialogfelds [Fehlerausgabe konfigurieren](../../2014/integration-services/configure-error-output.md) an, wie Fehler behandelt werden sollen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Teilen eines Datasets mithilfe der Transformation für bedingtes Teilen](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
