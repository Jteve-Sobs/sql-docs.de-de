---
title: STBoundary (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 2f99cc9931a136d7b3d3919687e5e5b8ffee269c
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555993"
---
# <a name="stboundary-geometry-data-type"></a>STBoundary (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt die Begrenzung einer **geometry**-Instanz zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STBoundary ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="remarks"></a>Bemerkungen  
 `STBoundary()` gibt eine leere **GeometryCollection** zurück, wenn de Endpunkte für eine **LineString**-, **CircularString**- oder **CompoundCurve**-Instanz gleich sein.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>A. Verwenden von STBoundary() in einer LINESTRING-Instanz mit verschiedenen Endpunkten  
 Im folgenden Beispiel wird eine `LineString``geometry`-Instanz erstellt. `STBoundary()` gibt die Begrenzung zum `LineString` zurück.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STBoundary().ToString();  
```  
  
### <a name="b-using-stboundary-on-a-linestring-instance-with-the-same-endpoints"></a>B. Verwenden von STBoundary() in einer LINESTRING-Instanz mit übereinstimmenden Endpunkten  
 Im folgenden Beispiel wird eine gültige `LineString`-Instanz mit den gleichen Endpunkten erstellt. `STBoundary()` gibt eine leere `GeometryCollection` zurück.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, -2 2, 0 0)', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
### <a name="c-using-stboundary-on-a-curvepolygon-instance"></a>C. Verwenden von STBoundary() in einer CurvePolygon-Instanz  
 Im folgenden Beispiel wird `STBoundary()` in einer `CurvePolygon`-Instanz verwendet. `STBoundary()` gibt eine `CircularString`-Instanz zurück.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(0 0, 2 2, 0 2, -2 2, 0 0))', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
