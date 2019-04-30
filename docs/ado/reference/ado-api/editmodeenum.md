---
title: EditModeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34583128e3da1bec00003fe194d3387783815275
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181099"
---
# <a name="editmodeenum"></a>EditModeEnum
Gibt den Bearbeitungsstatus eines Datensatzes an.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|Gibt an, dass keine Bearbeitungsvorgang ausgeführt wird.|  
|**adEditInProgress**|1|Gibt an, dass die Daten im aktuellen Datensatz geändert, aber nicht gespeichert wurde.|  
|**adEditAdd**|2|Gibt an, dass die [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) Methode aufgerufen wurde, und der aktuelle Datensatz in der Kopierpuffer ist ein neuer Datensatz, der nicht in der Datenbank gespeichert wurde.|  
|**adEditDelete**|4|Gibt an, dass der aktuelle Datensatz gelöscht wurde.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>Gilt für  
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)
