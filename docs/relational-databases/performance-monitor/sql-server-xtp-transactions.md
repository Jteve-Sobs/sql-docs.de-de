---
title: SQL Server-XTP-Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3a7c1572e752801a8e1e122202ea8bd0e2677545
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030689"
---
# <a name="sql-server-xtp-transactions"></a>SQL Server-XTP-Transaktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Das Leistungsobjekt „SQL Server-XTP-Transaktionen“ enthält Leistungsindikatoren, die sich auf Transaktionen im Zusammenhang mit In-Memory-OLTP in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]beziehen.  
  
 In dieser Tabelle werden die Leistungsindikatoren für **SQL Server-XTP-Transaktionen** beschrieben.  
  
|Leistungsindikator|und Beschreibung|  
|-------------|-----------------|  
|**Abbruchweitergaben/s**|Die durchschnittliche Anzahl der Transaktionen, für die pro Sekunde aufgrund eines Commitabhängigkeits-Rollbacks ein Rollback durchgeführt wurde.|  
|**Übernommene Commitabhängigkeiten/s**|Die durchschnittliche Anzahl der Commitabhängigkeiten, die pro Sekunde von Transaktionen übernommen werden.|  
|**Vorbereitete schreibgeschützte Transaktionen/s**|Die Anzahl der schreibgeschützten Transaktionen, die pro Sekunde für die Commitverarbeitung vorbereitet wurden.|  
|**Sicherungspunktaktualisierungen/s**|Die durchschnittliche Häufigkeit pro Sekunde, mit der ein Sicherungspunkt aktualisiert wurde. Eine Sicherungspunktaktualisierung erfolgt, wenn ein vorhandener Sicherungspunkt auf den aktuellen Punkt in der Lebensdauer der Transaktion zurückgesetzt wird.|  
|**Sicherungspunkt-Rollbacks/s**|Die durchschnittliche Häufigkeit, mit der für eine Transaktion pro Sekunde ein Rollback auf einen Sicherungspunkt ausgeführt wurde.|  
|**Erstellte Sicherungspunkte/s**|Die durchschnittliche Anzahl der pro Sekunde erstellten Sicherungspunkte.|  
|**Transaktionsüberprüfungsfehler/s**|Die durchschnittliche Anzahl der Transaktionen mit fehlgeschlagener Überprüfungsverarbeitung (pro Sekunde).|  
|**Vom Benutzer abgebrochene Transaktionen/s**|Die durchschnittliche Anzahl der Transaktionen, die pro Sekunde vom Benutzer abgebrochen wurden.|  
|**Abgebrochene Transaktionen/s**|Die durchschnittliche Anzahl der Transaktionen, die pro Sekunde vom Benutzer und vom System abgebrochen wurden.|  
|**Erstellte Transaktionen/s**|Die durchschnittliche Anzahl der pro Sekunde im System erstellten Transaktionen.<br /><br /> XTP-Transaktionen werden anders als datenträgerbasierte Transaktionen gezählt (wie aus Datenbanken:Transaktionen/Sekunde ersichtlich). Beispielsweise zählt Erstellte Transaktionen/s schreibgeschützte Transaktionen, Datenbanken:Transaktionen/Sekunde hingegen nicht.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Leistungsindikatoren für SQL Server XTP &#40;In-Memory OLTP&#41;](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
