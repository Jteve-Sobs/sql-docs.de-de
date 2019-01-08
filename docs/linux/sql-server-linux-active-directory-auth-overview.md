---
title: Active Directory-Authentifizierung für SQL Server unter Linux
titleSuffix: SQL Server
description: Dieser Artikel enthält eine Übersicht über Active Directory-Authentifizierung für SQL Server unter Linux.
author: rothja
ms.date: 02/23/2018
ms.author: jroth
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: fcc2148119634c7114d72f67b2c7143fa7d47724
ms.sourcegitcommit: de8ef246a74c935c5098713f14e9dd06c4733713
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160399"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Active Directory-Authentifizierung für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel enthält eine Übersicht über Active Directory (AD)-Authentifizierung für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux. AD-Authentifizierung ist auch bekannt als integrierte Authentifizierung in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

## <a name="ad-authentication-overview"></a>Übersicht über AD-Authentifizierung

AD-Authentifizierung ermöglicht die Domäne eingebundene Clients unter Windows oder Linux zu authentifizieren [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit ihren Domänenanmeldeinformationen und das Kerberos-Protokoll.

AD-Authentifizierung hat die folgenden Vorteile gegenüber [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentifizierung:

- Benutzer authentifizieren über einmaliges Anmelden, ohne Aufforderung zur Kennworteingabe angezeigt.   
- Erstellen von Anmeldungen für AD-Gruppen, Sie verwalten den Zugriff und Berechtigungen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mithilfe von Active Directory-Gruppenmitgliedschaften.  
- Jeder Benutzer hat innerhalb Ihres Unternehmens, eine einzelne Identität, sodass Sie keine zum Nachverfolgen der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Anmeldenamen entsprechen, für welche Personen.   
- AD ermöglicht Ihnen, eine zentralisierte Kennwortrichtlinie in Ihrem Unternehmen zu erzwingen.   

## <a name="configuration-steps"></a>Konfigurationsschritte

Um Active Directory-Authentifizierung verwenden zu können, müssen Sie einen AD-Domänencontroller (Windows) in Ihrem Netzwerk verfügen.

Die Details zum Konfigurieren von AD-Authentifizierung finden Sie im Tutorial [Lernprogramm: Verwenden von Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md). Die folgende Liste enthält eine Zusammenfassung mit einem Link zu jedem Abschnitt des Tutorials:

1. [Einen SQL Server-Host zu einer Active Directory-Domäne beitreten](sql-server-linux-active-directory-authentication.md#join).
1. [Erstellen Sie einen AD-Benutzer für SQL Server, und legen Sie den ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser).
1. [Konfigurieren Sie die SQL Server-Dienst mit Schlüsseltabellen](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Erstellen von AD-basierten SQL Server-Anmeldungen in Transact-SQL](sql-server-linux-active-directory-authentication.md#createsqllogins).
1. [Verbinden mit SQL Server mit AD-Authentifizierung](sql-server-linux-active-directory-authentication.md#connect).

## <a name="known-issues"></a>Bekannte Probleme

- Zu diesem Zeitpunkt ist die einzige Authentifizierungsmethode für den datenbankspiegelungs-Endpunkt unterstützt Zertifikat. WINDOWS-Authentifizierungsmethode wird in einer zukünftigen Version aktiviert.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Implementieren von Active Directory-Authentifizierung für SQL Server unter Linux finden Sie unter [Lernprogramm: Verwenden von Active Directory-Authentifizierung mit SQL Server unter Linux](sql-server-linux-active-directory-authentication.md).
