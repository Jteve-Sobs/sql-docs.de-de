---
description: Members-Collection (ADO MD)
title: Members-Auflistung (ADO MD) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level::Members
- Members
- Position::Members
helpviewer_keywords:
- Members collection [ADO MD]
ms.assetid: 3a647cde-efdc-4394-b1b9-8cbb1b9d689f
author: rothja
ms.author: jroth
ms.openlocfilehash: a39565e51270684a5514d499c658f950fe473a1e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440872"
---
# <a name="members-collection-ado-md"></a>Members-Collection (ADO MD)
Enthält die [Element](../../../ado/reference/ado-md-api/member-object-ado-md.md) Objekte aus einer Ebene oder einer Position entlang einer Achse.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine **Members** -Auflistung wird verwendet, um die folgenden Typen von Membern zu enthalten:  
  
-   Die Elemente, die eine Ebene in einem Cube bilden. Diese sind in der **Members** -Auflistung eines [ebenenobjekts](../../../ado/reference/ado-md-api/level-object-ado-md.md) enthalten. Beispielsweise sind die vier Mitglieder der Länderebene "Kanada", "USA", "Vereinigtes Königreich [" und "](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)Deutschland".  
  
-   Die Elemente, die den untergeordneten Elementen eines bestimmten Elements in einer Hierarchie angehören. Diese Member werden von der [Children](../../../ado/reference/ado-md-api/children-property-ado-md.md) -Eigenschaft des übergeordneten **Member** -Objekts zurückgegeben. Wenn Sie z. b. dasselbe Beispiel verwenden, sind die beiden untergeordneten Elemente des Canada-Members "Kanada-Ost" und "Canada-West".  
  
-   Die Member, die eine bestimmte Position entlang einer Achse eines [Cellsets](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)definieren. Durch die Verwendung des Cellsets von der [Arbeit mit mehrdimensionalen Daten](../../../ado/guide/multidimensional/working-with-multidimensional-data.md) als Beispiel sind die beiden Member der ersten Position auf der x-Achse Valentinstag und Seattle. Diese Member sind in der **Members** -Auflistung eines [Positions](../../../ado/reference/ado-md-api/position-object-ado-md.md) Objekts enthalten.  
  
 **Members** ist eine standardmäßige ADO-Auflistung. Mit den Eigenschaften und Methoden einer Sammlung können Sie folgende Aufgaben ausführen:  
  
-   Abrufen der Anzahl von Objekten in der Auflistung mit der [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft.  
  
-   Gibt ein Objekt aus der Auflistung mit der Standard [Element](../../../ado/reference/ado-api/item-property-ado.md) Eigenschaft zurück.  
  
-   Aktualisieren Sie die Objekte in der Auflistung vom Anbieter mit der [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Eigenschaften, Methoden und Ereignisse](../../../ado/reference/ado-md-api/members-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Members-Beispiel (VBScript)](../../../ado/reference/ado-md-api/members-example-vbscript.md)   
 [Member-Objekt (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)
