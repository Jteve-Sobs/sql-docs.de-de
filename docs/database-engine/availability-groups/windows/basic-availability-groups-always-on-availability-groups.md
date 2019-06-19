---
title: Basisverfügbarkeitsgruppen für einzelne Datenbanken
description: 'In diesem Artikel werden die Unterschiede zwischen einer regulären Always On-Verfügbarkeitsgruppe und einer Always On-Basisverfügbarkeitsgruppe sowie die Konfiguration einer Basisverfügbarkeitsgruppe beschrieben. '
ms.custom: seodec18
ms.date: 02/01/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 285adbc7-ac9b-40f6-b4a9-3f1591d3b632
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 302359d2b5c03a114590e096e89d2299426673e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796688"
---
# <a name="basic-always-on-availability-groups-for-a-single-database"></a>Always On-Basisverfügbarkeitsgruppen für einzelne Datenbanken
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Always On-Basis-Verfügbarkeitsgruppen stellen eine Hochverfügbarkeitslösung für SQL Server 2016 und SQL Server 2017 Standard Edition zur Verfügung. Eine Basis-Verfügbarkeitsgruppe unterstützt eine Failoverumgebung für eine einzelne Datenbank. Sie wird mit Enterprise Edition erstellt und verwaltet, ähnlich wie traditionelle (erweiterte) [AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md). Die Unterschiede und Einschränkungen zwischen und für Basis-Verfügbarkeitsgruppen werden in diesem Dokument zusammengefasst.  
  
## <a name="features"></a>Funktionen  
 AlwaysOn-Basis-Verfügbarkeitsgruppen ersetzen das veraltete Feature „Datenbankspiegelung“ und bieten ein ähnliches Level an Featureunterstützung. Basis-Verfügbarkeitsgruppen ermöglichen einer primären Datenbank, ein einzelnes Replikat beizubehalten. Dieses Replikat kann entweder den synchronen Commit-Modus oder den asynchronen Commit-Modus verwenden. Weitere Informationen zu Verfügbarkeitsmodi finden Sie unter [Verfügbarkeitsmodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md). Das sekundäre Replikat bleibt inaktiv, es sei denn, es muss ein Failover durchgeführt werden. Dieses Failover kehrt die primären und sekundären Rollenzuweisungen, und verursacht damit, dass das sekundäre Replikat zur primären aktiven Datenbank wird. Weitere Informationen zum Failover finden Sie unter [Failover und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md). Basis-Verfügbarkeitsgruppen können in einer Hybridumgebung arbeiten, die die lokale und die Microsoft Azure-Umgebung umfasst.  
  
## <a name="limitations"></a>Einschränkungen  
 Basis-Verfügbarkeitsgruppen verwenden eine Teilmenge der Funktionen verglichen mit erweiterten Verfügbarkeitsgruppen auf SQL Server 2016 Enterprise Edition. Basis-Verfügbarkeitsgruppen beinhalten die folgenden Einschränkungen:  
  
- Beschränkung auf zwei Replikate (primäres und sekundäres) Einfache Verfügbarkeitsgruppen für SQL Server 2017 unter Linux unterstützen nur die zusätzliche Konfiguration eines einzigen Replikats.
  
- Kein Lesezugriff auf das sekundäre Replikat.  
  
- Keine Sicherung auf das sekundäre Replikat.  

- Keine Integritätsüberprüfungen der sekundären Replikate 

- Keine Unterstützung für Replikate, die auf Servern gehostet werden, die eine Version von SQL Server vor SQL Server 2016 Community Technology Preview 3 (CTP3) ausführen.  

- Unterstützung für eine Verfügbarkeitsdatenbank.  
  
- Basis-Verfügbarkeitsgruppen können nicht zu erweiterten Verfügbarkeitsgruppen upgegradet werden. Die Gruppe muss gelöscht und erneut einer Gruppe hinzugefügt werden, die nur Server enthält, die SQL Server 2016 Enterprise Edition ausführen.  
  
- Basis-Verfügbarkeitsgruppen werden nur für Standard Editions-Server unterstützt. 

- Grundlegende Verfügbarkeitsgruppen können nicht Teil einer verteilten Verfügbarkeitsgruppe sein. 
  
## <a name="configuration"></a>Konfiguration  
 Eine Basis-AlwaysOn-Verfügbarkeitsgruppe kann auf zwei beliebigen SQL Server 2016 Standard Edition-Servern erstellt werden. Wenn Sie eine Basis-Verfügbarkeitsgruppe erstellen, müssen Sie beide Replikate während der Erstellung angeben.  
  
 Verwenden Sie den Transact-SQL-Befehl **CREATE AVAILABILITY GROUP** um eine Basis-Verfügbarkeitsgruppe zu erstellen, und geben Sie die Option **WITH BASIC** an, (der Standard ist **ADVANCED**). Sie können die grundlegende Verfügbarkeitsgruppe ebenfalls über die Benutzeroberfläche in SQL Server Management Studio ab Version 17.8 erstellen. Weitere Informationen finden Sie unter [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md). 
  
> [!NOTE]  
>  Die Einschränkungen von Basis-Verfügbarkeitsgruppen gelten für den Befehl **CREATE AVAILABILITY GROUP** wenn **WITH BASIC** angegeben ist. Beispielsweise erhalten Sie einen Fehler, wenn Sie versuchen, eine Basis-Verfügbarkeitsgruppe zu erstellen, die Lesezugriff zulässt. Andere Einschränkungen gelten in der gleichen Weise. Weitere Informationen finden Sie im Abschnitt „Einschränkungen“ dieses Themas.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
