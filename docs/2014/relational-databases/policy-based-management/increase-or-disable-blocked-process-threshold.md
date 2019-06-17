---
title: Erhöhen oder Deaktivieren des Schwellenwerts für blockierte Prozesse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 694c5676a5d55fe4fca227d9042ff4f1a9e9d618
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62704969"
---
# <a name="increase-or-disable-blocked-process-threshold"></a>Erhöhen oder Deaktivieren des Schwellenwerts für blockierte Prozesse
  Diese Regel überprüft, ob die Option Schwellenwert für blockierte Prozesse auf 0 (deaktiviert) oder auf einen Wert größer oder gleich 5 (Sekunden) festgelegt ist. Ein Festlegen der Option Schwellenwert für blockierte Prozesse auf einen Wert von 1 bis 4 kann dazu führen, dass die Deadlocküberwachung permanent ausgeführt wird. Die Werte 1 bis 4 sollten nur bei der Problembehandlung und niemals langfristig oder in einer Produktionsumgebung ohne Unterstützung des Kundendiensts und -supports von [!INCLUDE[msCoName](../../includes/msconame-md.md)] verwendet werden.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Um dieses Problem zu lösen, legen Sie die Option Schwellenwert für blockierte Prozesse auf den Wert 5 (Sekunden) oder höher fest, oder deaktivieren Sie den Schwellenwert für blockierte Prozesse, indem Sie den Wert auf 0 (null) festlegen. Führen Sie die folgende Anweisung aus, um den Schwellenwert für blockierte Prozesse auf den Wert `5` Sekunden festzulegen:  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Schwellenwert für blockierte Prozesse (Serverkonfigurationsoption)](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
