---
title: Erstellen im Bereich einer Sitzung, benannte Mengen (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- CREATE SET statement
- session-scoped named sets [MDX]
ms.assetid: b751e1e4-6d4c-4d36-a28d-ffdaaee0f1c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 96b34d8b3fd2dce31f604c50a7431b993a29beca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62699584"
---
# <a name="creating-session-scoped-named-sets-mdx"></a>Erstellen benannter Mengen im Bereich einer Sitzung (MDX)
  Zum Erstellen einer benannten Menge, die während einer gesamten MDX-Sitzung (Multidimensional Expressions) verfügbar ist, verwenden Sie die [CREATE SET](/sql/mdx/mdx-data-definition-create-set)-Anweisung. Eine benannte Menge, die mit der CREATE SET-Anweisung erstellt wurde, wird erst entfernt, nachdem die MDX-Sitzung geschlossen wurde.  
  
 Wie in diesem Thema erläutert wird, ist die Syntax des WITH-Schlüsselworts unkompliziert und einfach zu verwenden.  
  
> [!NOTE]  
>  Weitere Informationen zu benannten Mengen finden Sie unter [Erstellen von benannten Mengen in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).  
  
## <a name="create-set-syntax"></a>Syntax von CREATE SET  
 Die CREATE SET-Anweisung hat folgende Syntax:  
  
```  
CREATE SESSION SET [CURRENTCUBE. | <cube name>.]<Set Identifier> AS <Set Expression>  
```  
  
 In der Syntax von CREATE SET enthält der `cube name` -Parameter den Namen des Cubes, der die Elemente für die benannte Menge enthält. Wenn der `cube name` -Parameter nicht angegeben ist, wird der aktuelle Cube als der Cube verwendet, der die Elemente für die benannte Menge enthält. Außerdem enthält der `Set_Identifier` -Parameter den Alias für die benannte Menge, und der `Set_Expression` -Parameter enthält den Mengenausdruck, auf den der Alias der benannten Menge verweist.  
  
## <a name="create-set-example"></a>Beispiel zu CREATE SET  
 Im folgenden Beispiel wird die CREATE SET-Anweisung dazu verwendet, die benannte Menge `SetCities_2_3` aus dem Store-Cube zu erstellen. Die Elemente der benannten Menge `SetCities_2_3` sind die Geschäfte in City 2 und City 3.  
  
```  
create Session set [Store].[SetCities_2_3] as  
{[Data Stores].[ByLocation].[State].&[CA].&[City 02],  
[Data Stores].[ByLocation].[State].&[NH].&[City 03]}  
```  
  
 Dadurch, dass die benannte Menge `SetCities_2_3` mit der CREATE SET-Anweisung erstellt wurde, bleibt die benannte Menge für die Dauer der aktuellen Sitzung verfügbar. Das folgende Beispiel ist eine gültige Abfrage, die die Elemente City 2 sowie City 3 zurückgibt und jederzeit ausgeführt werden kann, nachdem Sie die benannte Menge `SetCities_2_3` erstellt und bis Sie die Sitzung geschlossen haben.  
  
```  
select SetCities_2_3 on 0 from [Store]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen benannter Mengen im Bereich einer Abfrage &#40;MDX&#41;](mdx-named-sets-creating-query-scoped-named-sets.md)  
  
  
