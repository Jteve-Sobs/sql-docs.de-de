---
description: Clustered-Eigenschaft (SqlService-Klasse)
title: Clustered-Eigenschaft (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Clustered Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 40b62cbdc3d3e2e7bcdd67c8c07a7794a1e70885
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463552"
---
# <a name="clustered-property-sqlservice-class"></a>Clustered-Eigenschaft (SqlService-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft den booleschen Eigenschaftswert ab, der angibt, ob der Dienst Teil einer gruppierten Instanz ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Clustered [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boleescher Wert, der angibt, ob der Dienst Teil einer gruppierten Instanz ist: **true** , wenn der Dienst Teil einer gruppierten Instanz ist, bzw. **false** , wenn der Dienst nicht Teil einer gruppierten Instanz ist.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
