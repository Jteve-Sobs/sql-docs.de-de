---
title: STEnvelope (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STEnvelope_TSQL
- STEnvelope (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STEnvelope (geometry Data Type)
ms.assetid: 781d22e9-38df-4c23-836f-6dd0bdef49c5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: de184826e93903629679c273b226cb1e143f850e
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68042068"
---
# <a name="stenvelope-geometry-data-type"></a>STEnvelope (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt das minimale, an den Achsen ausgerichtete umschließende Rechteck der Instanz zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
STEnvelope ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird mithilfe von `STGeomFromText()` eine `LineString`-Instanz aus (0,0) bis (2,3) erstellt und `STEnvelope()` verwendet, um das umschließende Rechteck der `LineString`-Instanz zurückzugeben.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 3)', 0);  
SELECT @g.STEnvelope().ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

