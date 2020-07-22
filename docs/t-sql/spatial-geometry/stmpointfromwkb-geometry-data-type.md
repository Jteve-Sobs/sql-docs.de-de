---
title: STMPointFromWKB (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STMPointFromWKB (geometry Data Type)
- STMPointFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMPointFromWKB (geometry Data Type)
ms.assetid: 01d4117f-01a0-4bc3-8762-7382a1cdbd6c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f538896347f5ca9148b422d992450314a6cde50f
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552795"
---
# <a name="stmpointfromwkb-geometry-data-type"></a>STMPointFromWKB (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt eine **geometryMultiPoint**-Instanz von einer OGC-WKB-Darstellung (Open Geospatial Consortium, Well-Known Binary) zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STMPointFromWKB ( 'WKB_multipoint' , SRID )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *WKB_multipoint*  
 Die WKB-Darstellung der **geometryMultiPoint**-Instanz, die zurückgegeben werden soll. *WKB_multipoint* ist ein **varbinary(max)** -Ausdruck.  
  
 *SRID*  
 Ein **int**-Ausdruck, der die SRID (Spatial Reference ID) der **geometryMultiPoint**-Instanz darstellt, die zurückgegeben werden soll.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 OGC-Typ: **MultiPoint**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode löst eine **FormatException** aus, wenn die Eingabe nicht korrekt formatiert ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STMPointFromWKB()` verwendet, um eine `geometry`-Instanz zu erstellen.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STMPointFromWKB(0x010400000002000000010100000000000000000059400000000000005940010100000000000000000069400000000000006940, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Statische geometry-Methoden des OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

