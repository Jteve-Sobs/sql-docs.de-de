---
title: Bandbreite für Volltextbenachrichtigung (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Option „ft notify bandwidth“. Sie erfahren, wie diese Option sich auf die Anzahl der Puffer auswirkt, die SQL Server im Pool der kleinen Arbeitsspeicherpuffer speichert.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: cb6bf13a1f8e71f419350946d156f2504274b6d0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772468"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>Bandbreite für Volltextbenachrichtigung (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Mit der **ft notify bandwidth** -Option können Sie angeben, bis zu welcher Größe der Pool mit geringem Arbeitsspeicher anwachsen kann. Kleine Arbeitsspeicherpuffer sind 64 KB groß. Der Parameterwert *max* gibt die maximale Anzahl von Puffern an, die der Volltextspeicher-Manager in einem kleinen Pufferpool verwalten soll. Wenn der **max** -Wert null beträgt, besteht keine obere Grenze für die Anzahl der Puffer in einem Pool mit geringem Arbeitsspeicher.  
  
 Durch den Parameter **min** wird die minimale Anzahl von Speicherpuffern angegeben, die in einem Pool mit geringem Arbeitsspeicher verwaltet werden müssen. Auf Anforderung vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Speicher-Manager werden alle zusätzlichen Pufferpools freigegeben, die Mindestzahl an Puffern wird jedoch beibehalten. Ist der angegebene **min** -Wert jedoch gleich null, werden alle Speicherpuffer freigegeben.  
  
 Unter bestimmten Umständen ist die Pufferanzahl, die aktuell zugeordnet ist, geringer als der durch den Parameter **min** angegebene Wert.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Bandbreite für Volltextdurchforstung (Serverkonfigurationsoption)](../../database-engine/configure-windows/ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
