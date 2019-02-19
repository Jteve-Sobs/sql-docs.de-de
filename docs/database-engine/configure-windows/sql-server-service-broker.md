---
title: SQL Server Service Broker | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 70487916496caa4cb2fba5a472262d22c7c123bd
ms.sourcegitcommit: c61c7b598aa61faa34cd802697adf3a224aa7dc4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "56154655"
---
# <a name="sql-server-service-broker"></a>SQL Server Service Broker
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSB](../../includes/sssb-md.md)] bietet systemeigene Unterstützung für Messaging- und Warteschlangenanwendungen in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Dies erleichtert Entwicklern das Erstellen anspruchsvoller Anwendungen, die die [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Komponenten für die Kommunikation zwischen verschiedenartigen Datenbanken verwenden. Entwickler können [!INCLUDE[ssSB](../../includes/sssb-md.md)] verwenden, um verteilte und zuverlässige Anwendungen auf einfache Weise zu erstellen.  
  
 Anwendungsentwickler, die [!INCLUDE[ssSB](../../includes/sssb-md.md)] verwenden, können Datenarbeitsauslastungen zwischen mehreren Datenbanken verteilen, ohne komplizierte Besonderheiten von Kommunikation und Messaging programmieren zu müssen. Dadurch werden die Entwicklungs- und die Testarbeit reduziert, da [!INCLUDE[ssSB](../../includes/sssb-md.md)] die Kommunikationspfade im Kontext einer Konversation behandelt. Außerdem wird die Leistung verbessert. Front-End-Datenbanken, die Websites unterstützen, können z. B. Informationen aufzeichnen und prozessintensive Tasks an die Warteschlange von Back-End-Datenbanken senden. [!INCLUDE[ssSB](../../includes/sssb-md.md)] stellt sicher, dass alle Tasks im Kontext von Transaktionen verwaltet werden, um die Zuverlässigkeit und technische Konsistenz zu gewährleisten.  
  
## <a name="where-is-the-documentation-for-service-broker"></a>Wo finde ich die Dokumentation für Service Broker?  
 Die Referenzdokumentation für [!INCLUDE[ssSB](../../includes/sssb-md.md)] ist in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Dokumentation enthalten. Diese Referenzdokumentation enthält die folgenden Abschnitte:  
  
-   [Anweisungen &#40;Transact-SQL&#41; für Datendefinitionssprache &#40;DDL&#41;](../../t-sql/statements/statements.md) für CREATE-, ALTER- und DROP-Anweisungen  
  
-   [Service Broker-Anweisungen](../../t-sql/statements/service-broker-statements.md)  
  
-   [Service Broker-Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)  
  
-   [Dynamische Verwaltungssichten in Verbindung mit Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
-   [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 Informationen zu [-Konzepten sowie Entwicklungs- und Verwaltungsaufgaben finden Sie in der](https://go.microsoft.com/fwlink/?LinkId=231312) zuvor veröffentlichten Dokumentation [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Diese Dokumentation ist aufgrund der geringen Anzahl von Änderungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssSB](../../includes/sssb-md.md)] nicht in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Dokumentation enthalten.  
  
## <a name="whats-new-in-service-broker"></a>Neues in Service Broker  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]wurden keine wesentlichen Änderungen eingeführt.  Für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]wurden die folgenden Änderungen eingeführt.  

### <a name="service-broker-and-azure-sql-database-managed-instance"></a>Service Broker und verwaltete Azure SQL-Datenbank-Instanz

- Ein instanzenübergreifender Service Broker wird nicht unterstützt. 
 - `sys.routes` – Voraussetzung: Wählen Sie die Adresse aus sys.routes. Die Adresse muss für jede Route LOCAL sein. Informationen hierzu finden Sie unter [sys.routes](../../relational-databases/system-catalog-views/sys-routes-transact-sql.md).
 - `CREATE ROUTE` – Sie können `CREATE ROUTE` mit keiner anderen `ADDRESS` als `LOCAL` verwenden. Informationen hierzu finden Sie unter [CREATE ROUTE](https://docs.microsoft.com/sql/t-sql/statements/create-route-transact-sql).
 - `ALTER ROUTE` kann `ALTER ROUTE` mit keiner anderen `ADDRESS` als `LOCAL` verwenden. Informationen hierzu finden Sie unter [ALTER ROUTE](../../t-sql/statements/alter-route-transact-sql.md).  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a>Nachrichten können an mehrere Zieldienste gesendet werden (Multicast)  
 Die Syntax der [SEND &#40;Transact-SQL&#41;](../../t-sql/statements/send-transact-sql.md)-Anweisung wurde erweitert, um mehrere Konversationshandles zu unterstützen und so die Multicastübermittlung zu ermöglichen.  
  
### <a name="queues-expose-the-message-enqueued-time"></a>Warteschlangen machen die Nachrichtenwartezeit verfügbar  
 Warteschlangen verfügen über eine neue **message_enqueue_time**-Spalte, in der angezeigt wird, wie lange eine Nachricht in der Warteschlange war.  
  
### <a name="poison-message-handling-can-be-disabled"></a>Behandlung nicht verarbeitbarer Nachrichten kann deaktiviert werden  
 Die Anweisungen [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md) und [ALTER QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-queue-transact-sql.md) bieten nun die Möglichkeit, die Behandlung von nicht verarbeitbaren Nachrichten zu aktivieren oder deaktivieren, indem die Klausel `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)` hinzugefügt wird. Die **sys.service_queues**-Katalogsicht enthält jetzt eine **is_poison_message_handling_enabled**-Spalte, in der angezeigt wird, ob die Behandlung nicht verarbeitbarer Nachrichten aktiviert oder deaktiviert ist.  
  
### <a name="always-on-support-in-service-broker"></a>AlwaysOn-Unterstützung in Service Broker  
 Weitere Informationen finden Sie unter [Service Broker mit AlwaysOn-Verfügbarkeitsgruppen (SQL Server)](../../database-engine/availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md).  
  
  

