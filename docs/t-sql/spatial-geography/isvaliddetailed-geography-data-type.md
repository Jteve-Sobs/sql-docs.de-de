---
title: IsValidDetailed (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsValidDetailed_TSQL
- IsValidDetailed
dev_langs:
- TSQL
helpviewer_keywords:
- IsValidDetailed geography
ms.assetid: f5f0b753-c825-43ce-987d-98655d8d8702
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f6db4d1090d464a7b2783b3494c0b478060faf7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47698718"
---
# <a name="isvaliddetailed-geography-data-type"></a>IsValidDetailed (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt eine Meldung zurück, die Informationen zur Identifizierung von Problemen mit einem räumlichen Objekt enthält, das nicht gültig ist. Wenn das Objekt nicht gültig ist, wird nur der erste Fehler zurückgegeben. Wenn das Objekt gültig ist, wird der Wert 24400 zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.IsValidDetailed()  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **nvarchar(max)**  
  
 CLR-Rückgabetyp: **string**  
  
## <a name="remarks"></a>Remarks  
 Die folgende Tabelle enthält mögliche Rückgabewerte:  
  
|Rückgabewert|Beschreibung|  
|------------------|-----------------|  
|24400|Gültig|  
|24401|Ungültig, die Ursache ist unbekannt.|  
|24402|Ungültig, weil der Punkt {0} ein isolierter Punkt ist, der für diesen Objekttyp ungültig ist.|  
|24403|Ungültig, weil sich ein Polygonkantenpaar überlappt.|  
|24404|Ungültig, weil eine Überschneidung von Polygonring {0} mit sich selbst oder einem anderen Ring vorliegt.|  
|24405|Ungültig, weil eine Überschneidung eines Polygonrings mit sich selbst oder einem anderen Ring vorliegt.|  
|24406|Ungültig, weil die Kurve {0} zu einem Punkt degeneriert wird.|  
|24407|Ungültig, weil der Polygonring {0} auf eine Linie an Punkt {1} reduziert wird.|  
|24408|Ungültig, weil der Polygonring {0} nicht geschlossen ist.|  
|24409|Ungültig, weil sich ein Teil des Polygonrings {0} im Inneren eines Polygons befindet.|  
|24410|Ungültig, weil der Ring {0} der erste Ring in einem Polygon, aber nicht dessen äußerer Ring ist.|  
|24411|Ungültig, weil der Ring {0} außerhalb des äußeren Rings {1} des zugehörigen Polygons liegt.|  
|24412|Ungültig, weil das Innere eines Polygons mit den Ringen {0} und {1} unverbunden ist.|  
|24413|Ungültig aufgrund von zwei überlappenden Kanten in Kurve {0}.|  
|24414|Ungültig, weil sich eine Kante der Kurve {0} und eine Kante der Kurve {1} überschneiden.|  
|24415|Ungültig, weil ein Polygon über eine ungültige Ringstruktur verfügt.|  
|24416|Ungültig, weil die Kante, die an Punkt {1} beginnt, in Kurve {0} entweder eine Linie oder ein degenerierter Bogen mit entgegengesetzten Endpunkten ist.|  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel für ein ungültiges räumliches Objekt wird veranschaulicht, wie sich die **IsValidDetailed()**-Methoden verhalten.  
  
```sql  
DECLARE @p GEOGRAPHY = 'Polygon((2 2, 4 4, 4 2, 2 4, 2 2))'  
SELECT @p.IsValidDetailed()  
--Returns: 24409: Not valid because some portion of polygon ring (1) lies in the interior of a polygon.  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
