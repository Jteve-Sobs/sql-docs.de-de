---
description: SetDefaults-Methode (ServerSettings-Klasse)
title: SetDefaults-Methode (ServerSettings)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: 76e4cfab-4b15-4da4-bb2f-8aac6f927f79
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3d3dcfae6dc8f4871ffc5b14ef47fb5508b7f01c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460085"
---
# <a name="setdefaults-method-serversettings-class"></a>SetDefaults-Methode (ServerSettings-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Legt alle Standardwerte für die Instanz von fest [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , wobei die Option zum Überschreiben vorhandener Daten vorhanden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [ServerSettings-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md) , das Einstellungen eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Clientinstanz darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*Overschreiteall*|Ein boolescher Wert, der angibt, ob vorhandene Werte für die Instanz von überschrieben werden sollen: true, wenn vorhandene Daten überschrieben werden sollen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , oder **false** , wenn vorhandene Daten nicht überschrieben werden sollen. **true**|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein u**Int32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird, und jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
