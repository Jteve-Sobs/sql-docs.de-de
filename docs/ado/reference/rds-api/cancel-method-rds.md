---
description: Cancel-Methode (RDS)
title: Cancel-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Cancel method [RDS]
ms.assetid: 560b5b3d-fba9-4275-8920-9c3e186134f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 68a7e5139be0cc317341bda05a171e0969411540
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439252"
---
# <a name="cancel-method-rds"></a>Cancel-Methode (RDS)
Bricht die Ausführung eines ausstehenden asynchronen Methoden Aufrufes ab.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RDS.DataControl.Cancel  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie **Abbrechen**aufrufen, wird "read [ystate](../../../ado/reference/rds-api/readystate-property-rds.md) " automatisch auf " **adkreadystateloaded**" festgelegt, und das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ist leer.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cancel-Methode (Beispiel) (VBScript)](../../../ado/reference/rds-api/cancel-method-example-vbscript.md)   
 [Cancel-Methode (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate-Methode (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [ExecuteOptions-Eigenschaft (RDS)](../../../ado/reference/rds-api/executeoptions-property-rds.md)


