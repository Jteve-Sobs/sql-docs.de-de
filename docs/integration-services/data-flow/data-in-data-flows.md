---
title: Daten in Datenflüssen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- comparing data
- data types [Integration Services], data flow
- parsing [Integration Services]
- string comparisons
- data flow [Integration Services], data options
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c623753cac559d9f4d38633b0d9205288cb57f84
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68049496"
---
# <a name="data-in-data-flows"></a>Daten in Datenflüssen

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stellt Datentypen bereit, die in Datenflüssen verwendet werden.  
  
## <a name="data-type-conversion"></a>Datentypkonvertierung  
 Die Quelle, die Sie einem Datenfluss hinzufügen, konvertiert die Quelldaten in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datentypen. Mit nachfolgenden Transformationen können die Daten in andere [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datentypen konvertiert werden. Je nach Datenspeichertyp, in den die Daten geladen werden, kann der endgültige [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datentyp von den Zielen in den Datentyp konvertiert werden, der für den Zieldatenspeicher erforderlich ist. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Zum Konvertieren der Daten in einen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Datentyp analysiert eine Datenflusskomponente die Daten. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stellt zwei Methoden zum Analysieren von Daten bereit: schnelle Analyse und Standardanalyse. Die meisten Datenflusskomponenten können nur die Standardanalyse verwenden. Die Flatfilequelle und die Transformation für Datenkonvertierung können jedoch die schnelle Analyse oder die Standardanalyse verwenden. Weitere Informationen finden Sie unter [Parsing Data](../../integration-services/data-flow/parsing-data.md).  
  
## <a name="data-type-comparison"></a>Datentypvergleich  
 Viele Transformationen vergleichen Datenwerte. Beispielsweise vergleicht die Transformation für das Aggregieren Werte, um Werte in Datenzeilen zu aggregieren, die Transformation zum Sortieren vergleicht Werte, um sie zu sortieren, und die Transformation für Suche vergleicht Werte mit Werten in einer separaten Verweistabelle. Um anzugeben, wie Zeichenfolgen verglichen werden sollen, enthält die Transformation Vergleichsoptionen wie z. B., ob die Groß-/Kleinschreibung ignoriert werden soll, wie Kanatypen in japanischem Text behandelt werden sollen, und ob Leerzeichen in der Zeichenfolge ignoriert werden sollen. Weitere Informationen finden Sie unter [Comparing String Data](../../integration-services/data-flow/comparing-string-data.md).  
  
 Die Ausdrucksauswertung vergleicht auch Datenwerte, wenn die Ausdrücke ausgewertet werden, die von Variablen, Rangfolgeneinschränkungen und Transformationen verwendet werden.  
  
## <a name="data-flow-troubleshooting"></a>Problembehandlung für den Datenfluss  
 Sobald Sie im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog ein Paket bereitgestellt haben, können Sie den Datenfluss im Paket während der Ausführung analysieren, um die Leistung zu überprüfen oder nach anderen Problemen zu suchen. Mit den verfügbaren Standardberichten können Sie den Paketstatus und -verlauf anzeigen, und Sie können Datenbanksichten abfragen, die ausführliche Informationen zur Paketausführung bereitstellen. Außerdem können Sie während der Ausführung dynamisch Datenabzweigungen hinzufügen und entfernen, um auf bestimmte Komponenten des Pakets abzuzielen. Weitere Informationen finden Sie unter [Debugging Data Flow](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
  
