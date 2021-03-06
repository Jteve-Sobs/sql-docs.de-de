---
description: InternetTimeout-Eigenschaft (RDS)
title: InternetTimeout-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
author: rothja
ms.author: jroth
ms.openlocfilehash: 9dbc94caa6266ff2f44a07c8792ff8b6287fd61c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438922"
---
# <a name="internettimeout-property-rds"></a>InternetTimeout-Eigenschaft (RDS)
Gibt die Anzahl der Millisekunden an, die gewartet wird, bevor ein Timeout für eine Anforderung eintritt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Long** -Wert fest, der die Anzahl der Millisekunden vor dem Timeout einer Anforderung darstellt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft gilt nur für Anforderungen, die mit den HTTP-oder HTTPS-Protokollen gesendet werden.  
  
 Die Ausführung von Anforderungen in einer Umgebung mit drei Ebenen kann mehrere Minuten in Anspruch nehmen. Verwenden Sie diese Eigenschaft, um zusätzliche Zeit für Anforderungen mit langer Ausführungszeit anzugeben.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
    :::column-end:::
    :::column:::
        [DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für InternetTimeout-Eigenschaft (VB)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [InternetTimeout-Eigenschaft – Beispiel (VC++)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 

