---
title: StartMode-Eigenschaft (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 31d2a413aa606bc6b7065126668fdeabdfacd7b1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73660872"
---
# <a name="startmode-property-sqlservice-class"></a>StartMode-Eigenschaft (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Startmodus des Dienstes ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der den Modus des Diensts angibt.  
  
 Folgende Werte sind möglich:  
  
 Start  
 Wert = 0. Dienst wurde durch das Betriebssystemladeprogramm gestartet. Diese Option ist nur für Treiberdienste gültig.  
  
 System  
 Wert = 1. Der Dienst wurde von der **IoInitSystem** -Methode gestartet. Diese Option ist nur für Treiberdienste gültig.  
  
 Automatisch  
 Wert = 2. Der Dienst soll während des Systemstarts automatisch vom Dienstkontroll-Manager gestartet werden.  
  
 Manuell  
 Wert = 3. Der Dienst, der vom Computer-Manager gestartet werden soll, wenn ein Prozess die **StartService** -Methode aufruft.  
  
 Disabled  
 Wert = 4. Der Dienst kann nicht gestartet werden.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
