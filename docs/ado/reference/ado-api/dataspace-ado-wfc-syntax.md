---
title: DataSpace (ADO / WFC-Syntax) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 569944991c029c091f0f17be4e5d943a893333a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67919190"
---
# <a name="dataspace-ado---wfc-syntax"></a>DataSpace (ADO/WFC-Syntax)
Die **CreateObject** Methode der **DataSpace** Klasse gibt sowohl ein Geschäftsobjekt zum Verarbeiten von Clientanforderungen für die Anwendung (*progid*) und das Kommunikationsprotokoll und Server (*Verbindung*). **CreateObject** gibt ein [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) -Objekt, das den Server darstellt.  
  
## <a name="package-commswfcdata"></a>Paket com.ms.wfc.data  
  
### <a name="constructor"></a>Konstruktor  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>Methoden  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>Eigenschaften  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)
