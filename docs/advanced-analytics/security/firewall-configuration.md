---
title: Konfiguration der Firewall für SQL Server Machine Learning Services | Microsoft-Dokumentation
description: Informationen zum Konfigurieren der Firewall für SQL Server-Machine Learning-Dienste.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: d2bf36ea9a7c7a0b193dc4613f6a36f58e66014a
ms.sourcegitcommit: 13d98701ecd681f0bce9ca5c6456e593dfd1c471
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2018
ms.locfileid: "49419055"
---
# <a name="firewall-configuration-for-sql-server-machine-learning-services"></a>Konfiguration der Firewall für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel enthält Überlegungen zur Firewall-Konfiguration, die der Administrator oder Architekt berücksichtigen sollten, wenn mithilfe von Machine Learning-Dienste.

## <a name="default-firewall-rules"></a>Standard-Firewall-Regeln

SQL Server-Setup deaktiviert standardmäßig die ausgehende Verbindungen durch Erstellen von Firewallregeln.

Diese Regeln basieren in SQL Server 2016 und 2017 auf lokale Benutzerkonten, die eingerichtet, in denen eine ausgehende Regel für hat **SQLRUserGroup** , der Netzwerkzugriff Membern verweigert (jedes workerkonto wurde aufgeführt als lokale Prinzip unterliegen die Regel. Weitere Informationen zu SQLRUserGroup, finden Sie unter [Sicherheit: Übersicht für das Extensibility Framework in SQL Server Machine Learning Services](../../advanced-analytics/concepts/security.md#sqlrusergroup).

In SQL Server-2019, als Teil der Umstieg auf AppContainers, es gibt neue Firewallregeln, die auf Grundlage der AppContainer-SIDs: eine für jede der 20 AppContainers von SQL Server-Setup erstellt. Benennungskonventionen für Name der Firewallregel sind **in SQL Server-Instanz MSSQLSERVER Blockieren des Netzwerkzugriffs für AppContainer-00**, wobei 00 die Anzahl von App-Container (00-20, in der Standardeinstellung ist), und MSSQLSERVER der Name des SQL ist- Server-Instanz.

> [!Note]
> Wenn Netzwerkaufrufe erforderlich sind, können Sie ausgehenden Regeln in der Windows-Firewall deaktivieren.

## <a name="restrict-network-access"></a>Einschränken des Netzwerkzugriffs auf

In einer Standardinstallation wird eine Windows-Firewall-Regel verwendet, um alle ausgehenden Netzwerkzugriffe durch externe-laufzeitprozesse zu blockieren. Firewallregeln sollten erstellt werden, um zu verhindern, dass der externe-Laufzeitprozessen Pakete herunterzuladen oder andere Netzwerke aufzurufen, die potenziell böswillig sein können.

Wenn Sie ein anderes Firewallprogramm verwenden, können Sie auch die Regeln zum Blockieren von ausgehende Netzwerkverbindungen für externe Laufzeiten, indem Sie Regeln für den lokalen Benutzerkonten oder für die durch den benutzerkontenpool dargestellte Gruppe festlegen erstellen.

Es wird dringend empfohlen, dass das Aktivieren der Windows-Firewall (oder eine andere Firewall Ihrer Wahl), um uneingeschränkten Netzwerkzugriff durch die Laufzeiten von R oder Python zu verhindern.

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren Sie Windows-Firewall für eingehende Verbindungen](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)