---
title: Veröffentlichungen mit Oracle (Übersicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d9d3a6f0860a8c0aff0a24b1acd6018163d5686
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "75548412"
---
# <a name="oracle-publishing-overview"></a>Oracle Publishing Overview  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] können Sie Oracle-Verleger in Ihre Replikationstopologie einbinden (ab Oracle Version 9i). Verlegerserver können auf einem beliebigen von Oracle unterstützten Hardware- und Betriebssystem bereitgestellt werden. Die Funktion basiert auf der viel benutzten Momentaufnahme- und Transaktionsreplikation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und bietet eine ähnliche Leistung und Benutzerfreundlichkeit.  
  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt die folgenden heterogenen Szenarien für die Transaktions- und Momentaufnahmereplikation:  
  
-   Veröffentlichen von Daten aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an Nicht-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Abonnenten.  

-   Beim Veröffentlichen von Daten an und von Oracle bestehen folgende Einschränkungen:  

  |       | 2016 oder früher |2017 oder höher |
  |-------|-------|--------|
  |Replikation von Oracle |Wird nur für Oracle 10g oder früher unterstützt |Wird nur für Oracle 10g oder früher unterstützt |
  |Replikation zu Oracle |Bis Oracle 12c |Nicht unterstützt |


 Die heterogene Replikation an Nicht-SQL Server-Abonnenten ist veraltet. Das Veröffentlichen mit Oracle ist veraltet. Um Daten zu verschieben, erstellen Sie Lösungen mit Change Data Capture und [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  

  
## <a name="snapshot-replication-for-oracle"></a>Momentaufnahmereplikation für Oracle  
 Oracle-Momentaufnahmeveröffentlichungen werden auf ähnliche Weise implementiert wie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Momentaufnahmeveröffentlichungen. Wenn der Momentaufnahme-Agent für eine Oracle-Veröffentlichung ausgeführt wird, stellt er eine Verbindung mit dem Oracle-Verleger her und verarbeitet die einzelnen Tabellen in der Veröffentlichung. Bei der Verarbeitung der einzelnen Tabellen ruft der Agent die Tabellenzeilen ab und erstellt Schemaskripts, die dann in der Momentaufnahmefreigabe der Veröffentlichung gespeichert werden. Der gesamte Datensatz wird jedes Mal erstellt, wenn der Momentaufnahme-Agent ausgeführt wird. Demzufolge werden den Oracle-Tabellen keine Änderungsprotokollierungstrigger hinzugefügt (wie es bei der Transaktionsreplikation der Fall ist). Die Momentaufnahmereplikation stellt eine praktische Möglichkeit zur Datenmigration dar, bei der das Verlegersystem nur minimal beeinträchtigt wird.  
  
## <a name="transactional-replication-for-oracle"></a>Transaktionsreplikation für Oracle  
 Transaktionsreplikationen bei Oracle werden mithilfe der Architektur für die Transaktionsveröffentlichung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]implementiert. Änderungen werden jedoch über eine Kombination aus Datenbanktriggern auf der Oracle-Datenbank und Protokolllese-Agents verfolgt. Abonnenten einer Oracle-Transaktionsveröffentlichung werden automatisch mithilfe der Momentaufnahmereplikation initialisiert. Nachfolgende Änderungen werden protokolliert und über den Protokolllese-Agent an die Abonnenten geliefert.  
  
 Wenn eine Oracle-Veröffentlichung erstellt wird, werden Trigger und Nachverfolgungstabellen für jede veröffentlichte Tabelle innerhalb der Oracle-Datenbank erstellt. Wenn Datenänderungen an den veröffentlichten Tabellen vorgenommen wurden, werden die Datenbanktrigger in den Tabellen ausgelöst und Informationen in die Replikations-Nachverfolgungstabelle für jede geänderte Zeile eingefügt. Der Protokolllese-Agent auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verleger verschiebt anschließend die Informationen bezüglich der Datenänderungen von den Nachverfolgungstabellen in die Verteilungsdatenbank auf dem Verleger. Schließlich verschiebt der Verteilungs-Agent, wie bei der standardmäßigen Transaktionsreplikation, Änderungen vom Verleger auf die Abonnenten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren eines Oracle-Verlegers](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Begriffe im Zusammenhang mit dem Veröffentlichen von Oracle-Daten](../../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Heterogene Datenbankreplikation](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  
