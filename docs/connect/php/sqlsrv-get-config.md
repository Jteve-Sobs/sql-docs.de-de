---
title: sqlsrv_get_config | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef4f53e4ee4ae1c9022ea8bfab0ba7a66c147c08
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922757"
---
# <a name="sqlsrv_get_config"></a>sqlsrv_get_config
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt den aktuellen Wert der angegebenen Konfigurationseinstellung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### <a name="parameters"></a>Parameter  
*$setting*: Die Konfigurationseinstellung für die der Wert zurückgegeben wird. Eine Liste der konfigurierbaren Einstellungen finden Sie unter [sqlsrv_configure](../../connect/php/sqlsrv-configure.md).  
  
## <a name="return-value"></a>Rückgabewert  
Der Wert der Einstellung, angegeben durch den *$setting* -Parameter. Wenn eine ungültige Einstellung angegeben wird, wird **false** zurückgegeben und ein Fehler wird zur Fehlersammlung hinzugefügt.  
  
## <a name="remarks"></a>Bemerkungen  
Wenn **false** von **sqlsrv_get_config**zurückgegeben wird, müssen Sie [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) aufrufen, um zu bestimmen, ob ein Fehler aufgetreten ist oder ob **false** der Wert der durch den *$setting* -Parameter.  
  
## <a name="see-also"></a>Weitere Informationen  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  

[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
