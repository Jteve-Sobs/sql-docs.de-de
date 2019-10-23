---
title: Verbindung mit SQL Server zum Löschen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b28d1c4cb3f17ae5a22e98735730a94ae186885
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71298894"
---
# <a name="connection-to-sql-server-for-delete"></a>Verbindung zu SQL Server zum Löschen

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Wenn eine Anmeldung ohne Datenbankrolle, die über die Schreibberechtigung für die MSXDBCDC-Datenbank verfügt (z.B. die Rolle **db_owner**), versucht, eine Oracle CDC-Instanz zu löschen, wird das Dialogfeld „Verbindung mit SQL Server herstellen“ angezeigt.  
  
 In diesem Dialogfeld müssen Sie die Anmeldeinformationen für eine Anmeldung eingeben, die über die Schreibberechtigung für die MSXDBCDC-Datenbank verfügt, z.B. die Datenbankrolle **db_owner** zum Löschen der Oracle CDC-Instanz.  
  
 Geben Sie im Dialogfeld Verbindung mit SQL Server herstellen die folgenden Informationen ein.  
  
 **Servername**  
 Geben Sie den Namen des Servers ein, auf dem sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
 **Authentifizierung**  
 Wählen Sie eine der folgenden Optionen aus:  
  
-   **Windows-Authentifizierung**  
  
-   **SQL Server-Authentifizierung**: Wenn Sie diese Option auswählen, müssen Sie den **Benutzernamen** und das **Kennwort** für den Benutzer von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eingeben, mit dem Sie eine Verbindung herstellen.  
  
 **Optionen**  
 Klicken Sie auf den Pfeil, um die verfügbaren Optionen anzuzeigen, die konfiguriert werden sollen. Sie können für diese Optionen auch die Standardwerte unverändert lassen. Verfügbare Optionen:  
  
-   **Verbindungstimeout**: Geben Sie den Zeitraum (in Sekunden) ein, wie lange das Programm auf die Herstellung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindung warten soll, bevor ein Timeoutfehler eintritt. Der Standardwert lautet **15**.  
  
-   **Ausführungstimeout**: Geben Sie den Zeitraum (in Sekunden) ein, wie lange das Programm auf die Beendigung der SQL-Befehlsausführung warten soll, bevor ein Timeoutfehler eintritt. Der Standardwert ist **30**.  
  
-   **Verbindung verschlüsseln**: Aktivieren Sie **Verbindung verschlüsseln**, um sicherzustellen, dass die hergestellte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindung verschlüsselt wird, um Datenschutz zu gewährleisten.  
  
-   **Erweitert**: Klicken Sie auf **Erweitert** , und geben Sie ggf. zusätzliche Verbindungseigenschaften in das Dialogfeld „Erweiterte Verbindungseigenschaften“ ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Für SQL Server-Verbindung erforderliche Berechtigungen für den CDC Service](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
