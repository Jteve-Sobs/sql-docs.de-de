---
title: STInteriorRingN (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STInteriorRingN_TSQL
- STInteriorRingN (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STInteriorRingN (geometry Data Type)
ms.assetid: 47310f9f-2cdb-41e0-a6da-7c3cfbf139ac
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 8e6908f612018978e234dd50074ae8eaf1998ed5
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65938876"
---
# <a name="stinteriorringn-geometry-data-type"></a>STInteriorRingN (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt den angegebenen inneren Ring einer **Polygongeometry**-Instanz zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STInteriorRingN ( expression )  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein **int**-Ausdruck zwischen 1 und der Anzahl der inneren Ringe in der **geometry**-Instanz.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC)-Typ: **LineString**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt **null** zurück, wenn die **geometry** -Instanz kein Polygon ist. Diese Methode löst außerdem eine **ArgumentOutOfRangeException** aus, wenn der Ausdruck größer als die Anzahl der Ringe ist. Die Anzahl der Ringe kann mithilfe von `STNumInteriorRing``()` zurückgegeben werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Polygon`-Instanz erstellt und dann mithilfe von `STInteriorRingN()` der innere Ring des Polygons als **LineString** zurückgegeben.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STInteriorRingN(1).ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

