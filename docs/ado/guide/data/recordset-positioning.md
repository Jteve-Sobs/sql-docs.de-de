---
title: Positionieren von Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f37f69b64e4a1a7fd55fb24a0c85d515971d4e72
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910445"
---
# <a name="recordset-positioning"></a>Positionieren von Recordsets
Verwenden der **AbsolutePosition** -Eigenschaft zum Verschieben auf einen Datensatz, basierend auf der Ordnungsposition in der **Recordset** -Objekt, oder um die Ordinalposition des aktuellen Datensatzes zu bestimmen. Der Anbieter muss die entsprechende Funktionalität für diese Eigenschaft zur Verfügung stehen unterstützen.  
  
 **AbsolutePosition** ist 1-basiert und entspricht 1, wenn der aktuelle Datensatz den ersten Datensatz in ist die **Recordset**. Wie bereits erwähnt, erhalten Sie die Gesamtzahl der Datensätze in der **Recordset** -Objekt aus der **RecordCount** Eigenschaft.  
  
 Beim Festlegen der **AbsolutePosition** -Eigenschaft, auch wenn es zu einem Datensatz im aktuellen Cache ist ADO lädt den Cache mit einer neuen Gruppe von Datensätzen, die mit dem angegebenen Datensatz ab. Die **CacheSize** Eigenschaft bestimmt die Größe dieser Gruppe.  
  
> [!NOTE]
>  Verwenden Sie nicht die **AbsolutePosition** -Eigenschaft, wie ein Ersatzzeichen Datensatznummer. Die Position eines bestimmten Datensatzes geändert wird, wenn Sie einen vorherigen Datensatz zu löschen. Gibt es auch ist nicht garantiert, dass ein bestimmter Datensatz die gleiche hat **AbsolutePosition** Wenn die **Recordset** Objekts erneut abgefragt oder geöffnet wird. Lesezeichen sind das empfohlene Verfahren zurückzukehren, klicken Sie auf einer bestimmten Position und sind die einzige Möglichkeit der Positionierung für alle Arten von **Recordset** Objekte.
