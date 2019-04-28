---
title: Ändern einer partitionsquelle, um eine andere Faktentabelle verwenden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact tables [Analysis Services]
- partitions [Analysis Services], fact tables
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f81cca9c4f7be1e0a94b9947432d1e7534994e1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62726844"
---
# <a name="change-a-partition-source-to-use-a-different-fact-table"></a>Ändern einer Partitionsquelle für die Verwendung einer anderen Faktentabelle
  Bei der Erstellung von Partitionen können Sie für Cubes unterschiedliche Faktentabellen verwenden. Die unterschiedlichen Tabellen können dabei aus einer einzelnen Datenquellensicht, aus verschiedenen Datenquellensichten oder aus verschiedenen Datenquellen stammen. Eine Datenquellensicht kann auch unterschiedliche Tabellen aus mehreren Datenquellen enthalten.  
  
 Alle Faktentabellen und Dimensionen für die Partitionen eines Cubes müssen dieselbe Struktur wie die Faktentabelle und die Dimensionen des Cubes besitzen. Unterschiedliche Faktentabellen können z. B. dieselbe Struktur besitzen, aber Daten für verschiedene Jahre oder verschiedene Produktlinien enthalten.  
  
 Eine Faktentabelle geben Sie auf der Seite **Quellinformationen angeben** des Partitions-Assistenten an. Geben Sie auf dieser Seite im Gruppenfeld Partitionsquelle neben **Suchen in**an, in welcher Datenquelle bzw. Datenquellensicht gesucht werden soll. Klicken Sie als Nächstes auf **Tabellen suchen**, und wählen Sie dann unter **Verfügbare Tabellen**die zu verwendende Tabelle aus.  
  
 Wenn Sie unterschiedliche Faktentabellen verwenden, sollten Sie sicherstellen, dass in den Partitionen keine Daten doppelt auftreten. Wenn eine Faktentabelle z. B. Transaktionen nur für das Jahr 2012 und eine andere Faktentabelle Transaktionen nur für das Jahr 2013 enthält, weisen diese Tabellen unabhängige Daten auf. Ebenso sind Faktentabellen für verschiedene Produktlinien oder verschiedene geografische Gebiete unabhängig voneinander.  
  
 Es ist möglich, aber nicht empfehlenswert, dass Sie unterschiedliche Faktentabellen verwenden, die doppelte Daten enthalten. In diesem Fall müssen Sie Filter in den Partitionen verwenden, um sicherzustellen, dass die von einer Partition verwendeten Daten nicht von einer anderen Partition verwendet werden. Weitere Informationen finden Sie unter [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Verwalten einer lokalen Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)  
  
  
