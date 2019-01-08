---
title: SQL Server-Replikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 01027aaa813cb3859dfd6d8459b7138a071c0f2d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53352973"
---
# <a name="sql-server-replication"></a>SQL Server-Replikation
  Bei der Replikation handelt es sich um eine Reihe von Technologien zum Kopieren und Verteilen von Daten und Datenbankobjekten aus einer Datenbank in eine andere und das anschließende Synchronisieren zwischen den Datenbanken, um die Konsistenz der Daten sicherzustellen. Mithilfe von Replikation können Sie Daten an verschiedene Standorte, an Remotebenutzer oder mobile Benutzer über lokale Netzwerke und WANs (Wide Area Network), über DFÜ-Verbindungen, Funkverbindungen oder über das Internet verteilen.  
  
 Die Transaktionsreplikation wird typischerweise in reinen Serverumgebungen verwendet, die einen hohen Durchsatz erfordern, und ist für die folgenden Fälle geeignet: Verbessern der Skalierbarkeit und Verfügbarkeit, Data Warehousing und Berichterstellung, Integrieren von Daten aus mehreren Standorten, Integrieren heterogener Daten und Auslagern der Batchverarbeitung. Die Mergereplikation ist in erster Linie für mobile Anwendungen oder verteilte Serveranwendungen mit möglichen Datenkonflikten konzipiert. Dazu gehören folgende häufige Szenarien: Datenaustausch mit mobilen Benutzern, Point-of-Sale-Anwendungen (POS) und Integrieren von Daten aus mehreren Standorten. Momentaufnahmereplikation wird verwendet, um das Anfangsdataset für Transaktions- und Mergereplikation bereitzustellen. Sie kann auch verwendet werden, wenn vollständige Aktualisierungen von Daten erforderlich sind. Mit diesen drei Replikationstypen stellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein leistungsfähiges und flexibles System zum Synchronisieren von Daten im gesamten Unternehmen bereit. Die Replikation in SQLCE 3.5 und SQLCE 4.0 wird unter [!INCLUDE[win8srv](../../includes/win8srv-md.md)] und [!INCLUDE[win8](../../includes/win8-md.md)]unterstützt.  
  
 Als Alternative zur Replikation können Sie Datenbanken mit Microsoft Sync Framework synchronisieren. Sync Framework schließt Komponenten und eine intuitive und flexible API ein, die es Ihnen erleichtern, zwischen SQL Server-, SQL Server Express-, SQL Server Compact- und SQL Azure-Datenbanken zu synchronisieren. Sync Framework schließt auch Klassen ein, die angepasst werden können, um zwischen einer SQL Server-Datenbank und einer beliebigen anderen Datenbank, die mit ADO.NET kompatibel ist, zu synchronisieren. Eine ausführliche Dokumentation der Sync Framework-Datenbanksynchronisierungskomponenten finden Sie unter [Synchronisieren von Datenbanken](https://go.microsoft.com/fwlink/?LinkId=209079). Eine Übersicht über Sync Framework finden Sie im [Microsoft Sync Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=209078). Einen Vergleich zwischen Sync Framework und Mergereplikation finden Sie unter [Übersicht über das Synchronisieren von Datenbanken](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)  
  
 **Durchsuchen von Inhalt nach Bereich**  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") [Neuigkeiten](what-s-new-replication.md)  
  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") [Abwärtskompatibilität](replication-backward-compatibility.md)  
  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") [Replikationsfunktionen und-Tasks](replication-features-and-tasks.md)  
  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") [technische Referenz](technical-reference-replication.md)  
  
  
