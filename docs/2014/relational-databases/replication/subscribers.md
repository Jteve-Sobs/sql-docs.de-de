---
title: Abonnenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 725be263e30687a3f2ded90990e952e1cd97a185
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62629389"
---
# <a name="subscribers"></a>Abonnenten
  Geben Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - oder Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten an, die ein Abonnement für die ausgewählte Veröffentlichung erhalten.  
  
## <a name="options"></a>Optionen  
 **Abonnenten**  
 Aktivieren Sie das Kontrollkästchen im Raster, um die zugehörige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - oder Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle als einen Abonnenten für die auf der Seite **Veröffentlichung** ausgewählte Veröffentlichung zu aktivieren. Wenn der Abonnent nicht aufgeführt ist, klicken Sie auf **Abonnent hinzufügen** oder **SQL Server-Abonnenten hinzufügen**.  
  
 **Abonnementdatenbank**  
 Die in dieser Spalte angezeigten Informationen sowie die über die Spalte verfügbaren Aktionen sind vom Typ des in der **Abonnenten** -Spalte aufgeführten Abonnenten abhängig:  
  
-   Wählen Sie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten eine Abonnementdatenbank aus der Liste **Abonnementdatenbank** aus, oder erstellen Sie eine neue Datenbank, indem Sie in derselben Liste den Befehl **Neue Datenbank** auswählen.  
  
    > [!NOTE]  
    >  Wenn Sie den Verleger als einen Abonnenten aktivieren, darf die Abonnementdatenbank nicht mit der Veröffentlichungsdatenbank identisch sein.  
  
-   Bei Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten wird die Abonnementdatenbank nicht angezeigt. Geben Sie im Feld **Datenquellenname** des Dialogfelds **Nicht-SQL Server-Abonnenten hinzufügen** die Datenbank und weitere Verbindungsinformationen an. Sie rufen dieses Dialogfeld auf, in dem Sie zuerst auf **Abonnent hinzufügen** und anschließend auf **Nicht-SQL Server-Abonnenten hinzufügen**klicken.  
  
 **Abonnent hinzufügen**  
 Fügen Sie einen Server zur Liste der Server hinzu, die als Abonnenten aktiviert werden können. Diese Schaltfläche wird angezeigt, wenn alle der folgenden Bedingungen erfüllt sind:  
  
-   Die von Ihnen ausgewählte Veröffentlichung ist eine Momentaufnahme- oder Transaktionsveröffentlichung, die keine Updateabonnements unterstützt.  
  
    > [!NOTE]  
    >  Wenn die Veröffentlichung, die Sie abonnieren, über [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnements verfügt und die Veröffentlichung für Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnenten noch nicht aktiviert ist, können Sie kein Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abonnement hinzufügen.  
  
-   Das Abonnement ist ein Pushabonnement.  
  
-   Als Verleger für die ausgewählte Veröffentlichung wird [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher verwendet.  
  
 Wenn Sie auf **Abonnent hinzufügen** klicken, wird ein Menü mit zwei Optionen angezeigt: **SQL Server-Abonnenten hinzufügen...** und **Nicht-SQL Server-Abonnenten hinzufügen**. Klicken Sie auf **Nicht-SQL Server-Abonnenten hinzufügen** , um einen Oracle- oder IBM DB2-Abonnenten hinzuzufügen.  
  
 **SQL Server-Abonnenten hinzufügen**  
 Fügen Sie einen Server zur Liste der Server hinzu, die als Abonnenten aktiviert werden können. Diese Schaltfläche wird angezeigt, wenn eine oder mehrere der folgenden Bedingungen zutreffen:  
  
-   Die von Ihnen ausgewählte Veröffentlichung ist eine Mergeveröffentlichung oder eine Momentaufnahme- oder Transaktionsveröffentlichung, die Updateabonnements unterstützt.  
  
-   Das Abonnement ist ein Pullabonnement.  
  
-   Als Verleger für die ausgewählte Veröffentlichung wird eine Version vor [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]verwendet. Bei früheren Versionen wird die Schaltfläche nur angezeigt, wenn eine oder mehrere der folgenden Bedingungen zutreffen:  
  
    -   Sie sind Mitglied der festen Serverrolle **sysadmin** auf dem Verleger.  
  
    -   Der Abonnent wurde über die Seite **Abonnenten** des Dialogfelds **Verlegereigenschaften** hinzugefügt.  
  
    -   Die Veröffentlichung lässt anonyme Abonnements zu.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Pullabonnements](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [Abonnieren von Veröffentlichungen](subscribe-to-publications.md)  
  
  
