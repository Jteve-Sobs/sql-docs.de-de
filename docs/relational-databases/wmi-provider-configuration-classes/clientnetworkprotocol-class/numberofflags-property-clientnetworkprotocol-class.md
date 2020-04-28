---
title: Numofflags-Eigenschaft (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- NumberOfFlags Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- NumberOfFlags property
ms.assetid: 7a656644-2154-419f-9787-99877f597770
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 48f81c86a823d75d501187ef953930ec92083d27
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73659125"
---
# <a name="numberofflags-property-clientnetworkprotocol-class"></a>NumberOfFlags-Eigenschaft (ClientNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft die Anzahl der Flagoptionen ab, die das von der [SetOrderValue-Methode (ClientNetworkProtocol-Klasse)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md)angegeben Clientnetzwerkprotokoll erfordert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.NumberofFlags [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , das das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **Uint32** -Wert, der die Anzahl der Flagoptionen angibt, die das Clientnetzwerkprotokoll erfordert, auf das die **OrderValue** -Eigenschaft verweist.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
