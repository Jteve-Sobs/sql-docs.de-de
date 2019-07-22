---
title: Dienstkonten (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9c0fb67d173ed0f4ade469c5233a7fdff59dd1a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68025254"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Dienstkonten (Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Geben Sie bei Verwendung der Windows-Authentifizierung die Dienstkonten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]an, wenn die Serverinstanzen verschiedene Konten verwenden. Diese Dienstkonten müssen alle Domänenkonten (in derselben oder vertrauenswürdigen Domäne) sein.  
  
 Wenn alle Serverinstanzen das gleiche Domänenkonto oder die zertifikatbasierte Authentifizierung verwenden, lassen Sie die Felder leer. Klicken Sie einfach auf **Fertig stellen**, und der Assistent konfiguriert automatisch die Konten auf Basis des Kontos des aktuellen Assistenten.  
  
> [!IMPORTANT]  
>  Wenn die Endpunkte für die Datenbankspiegelung der Serverinstanzen für die Verwendung von Zertifikaten konfiguriert sind, müssen Sie die Felder für die Dienstkonten leer lassen.  
  
 **So konfigurieren Sie die Datenbankspiegelung mithilfe von SQL Server Management Studio**  
  
-   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [Starten des Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>enthalten  
 **Prinzipal**  
 Geben Sie das Dienstkonto der Prinzipalserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *DOMÄNENNAME*\\*Benutzername*  
  
 **Spiegel**  
 Geben Sie das Dienstkonto der Spiegelserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *DOMÄNENNAME*\\*Benutzername*  
  
 **Zeuge**  
 Geben Sie das Dienstkonto der Zeugenserverinstanz an. Geben Sie den Domänennamen in Großbuchstaben ein:  
  
 *DOMÄNENNAME*\\*Benutzername*  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankeigenschaften &#40;Seite „Wird gespiegelt“&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Starten des Datenbankspiegelungs-Monitors &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Einrichten von Anmeldekonten für die Datenbankspiegelung oder Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
