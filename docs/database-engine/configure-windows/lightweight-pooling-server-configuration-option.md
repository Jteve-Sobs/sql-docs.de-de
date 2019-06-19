---
title: Lightweightpooling (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default lightweight pooling
- decreasing overhead
- lightweight pooling option
- system overhead [SQL Server]
- performance [SQL Server], lightweight pooling
- context switching [SQL Server], lightweight pooling option
- excessive context switching [SQL Server]
- reducing overhead
- overhead [SQL Server]
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: ea3ef8aa6e667935ea65c619221bfbbd10199e99
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66785168"
---
# <a name="lightweight-pooling-server-configuration-option"></a>Lightweightpooling (Serverkonfigurationsoption)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Mit der Option **lightweight pooling** können Sie den Systemverarbeitungsaufwand im Zusammenhang mit häufigen Kontextumschaltungen senken, die teilweise in symmetrischen Multiprocessing-Umgebungen (SMP) auftreten. Bei häufigen Kontextumschaltungen kann die Option "Lightweightpooling" für einen besseren Durchsatz sorgen, da die Kontextumschaltungen inline ausgeführt werden, was die Anzahl der Benutzer-/Kernelringübergänge verringert.  
  
 Der Fibermodus gilt für bestimmte Situationen, in denen der Kontextwechsel von UMS-Arbeitsthreads kritische Engpässe bei der Leistung verursacht. Da dies nur selten auftritt, verbessert der Fibermodus auch nur selten die Leistung oder die Skalierbarkeit auf einem typischen System. Verbesserter Kontextwechsel in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] hat auch die Notwendigkeit des Fibermodus verringert. Es wird empfohlen, die Fibermodusplanung nicht für Routinevorgänge zu verwenden, da sie die Leistung verringern kann, indem die normalen Vorteile des Kontextwechsels unterdrückt werden, und da einige Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die den lokalen Threadspeicher (TLS) verwenden, oder Thread-eigene Objekte, z. B. Mutexe (eine Art Win32-Kernel-Objekt), im Fibermodus nicht ordnungsgemäß arbeiten können.  
  
 Wenn der Wert der Option **Lightweightpooling** auf 1 festgelegt wird, wechselt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Fibermodusplanung. Der Standardwert für diese Option ist 0.  
  
 Bei **Lightweightpooling** handelt es sich um eine erweiterte Option. Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie **Lightweightpooling** nur ändern, wenn **Erweiterte Optionen anzeigen** auf 1 festgelegt ist. Diese Einstellung wird wirksam, nachdem der Server neu gestartet wurde.  
  
> [!NOTE]  
>  Lightweightpooling wird für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP nicht unterstützt. [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] stellt eine vollständige Unterstützung für Lightweightpooling bereit.  
  
> [!NOTE]  
>  CLR (Common Language Runtime) wird beim Lightweightpooling nicht unterstützt. Deaktivieren Sie eine der beiden Optionen "CLR-fähig" oder "Lightweightpooling". Zu den Funktionen, die auf CLR basieren und nicht ordnungsgemäß im Fibermodus arbeiten, gehören der Hierarchy-Datentyp, die Replikation und die richtlinienbasierte Verwaltung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CLR-fähig (Serverkonfigurationsoption)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [CLR-fähig (Serverkonfigurationsoption)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)  
  
  
