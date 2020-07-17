---
title: Einrichten von FILESTREAM auf einem Failovercluster | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie FILESTREAM auf einem Failovercluster in SQL Server einrichten und welche Optionen Sie aktivieren müssen, bevor Sie dies einrichten.
ms.custom: ''
ms.date: 08/26/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58ea828b434abbaaa939df25b9f6c59d26e3d144
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765477"
---
# <a name="set-up-filestream-on-a-failover-cluster"></a>Einrichten von FILESTREAM auf einem Failovercluster
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema erfahren Sie, wie Sie FILESTREAM auf einem Failovercluster aktivieren. Zur Durchführung dieser Prozedur müssen Sie mit [Failoverclustering](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) vertraut sein, und FILESTREAM muss aktiviert sein. Informationen zum Aktivieren von FILESTREAM finden Sie unter [Aktivieren und Konfigurieren von FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md).  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a>So richten Sie FILESTREAM auf einem Failovercluster ein  
  
1.  Richten Sie den primären Knoten für den Failovercluster ein.  
  
     Aktivieren Sie anschließend mit dem **SQL Server-Konfigurations-Manager**FILESTREAM auf dem primären Knoten. Hierdurch werden die Einstellungen aktiviert, die Windows-Administratorrechte erfordern. Wenn Remotezugriff erforderlich ist, wählen Sie **Streamingzugriff von Remoteclients auf FILESTREAM-Daten zulassen**. Hierdurch wird eine geclusterte Dateifreigaberessource erstellt.  
  
2.  Richten Sie einen passiven Knoten ein.  
  
     Aktivieren Sie anschließend mit dem **SQL Server-Konfigurations-Manager**FILESTREAM auf dem passiven Knoten. Der unter **Windows-Freigabename** angegebene Name muss auf allen Knoten im Cluster einheitlich sein.  
  
3.  Wiederholen Sie Schritt 2, um weitere passive Knoten hinzuzufügen.  
  
4.  Nachdem Sie alle Knoten hinzugefügt haben, schließen Sie den Prozess ab, indem Sie die gespeicherte Prozedur sp_configure auf jeder Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausführen.  
  
5.  Wiederholen Sie die Schritte 2, 3 und 4, um dem Cluster weitere Knoten hinzuzufügen und diese zu aktivieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Erstellen eines neuen SQL Server-Failoverclusters &#40;Setup&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)   
 [Entfernen einer SQL Server-Failoverclusterinstanz &#40;Setup&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)   
 [Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
