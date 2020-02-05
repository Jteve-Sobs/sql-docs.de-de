---
title: Neuer Auftragszeitplan – Eigenschaften des Auftragszeitplans
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.scheduleproperties.f1
- sql13.swb.maint.editrecurringjobsched.f1
ms.assetid: 5c0b1bc9-dd87-49cc-b0dd-75d0d922b177
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ace04d16e537e50c10e0eaa5c4fa432d1db7055f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245205"
---
# <a name="new-job-schedule---job-schedule-properties"></a>Neuer Auftragszeitplan – Eigenschaften des Auftragszeitplans
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die Eigenschaften des Zeitplans anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
**Name**  
Geben Sie einen neuen Namen für den Zeitplan ein.  
  
**Aufträge im Zeitplan**  
Zeigt die Aufträge an, die diesen Zeitplan verwenden.  
  
**Zeitplantyp**  
Wählen Sie den Zeitplantyp aus.  
  
**Aktiviert**  
Klicken Sie zum Aktivieren oder Deaktivieren des Zeitplans auf das Kontrollkästchen.  
  
## <a name="recurring-schedule-types-options"></a>Zeitplantypoptionen für wiederkehrende Aufträge  
**Tritt auf**  
Wählen Sie das Intervall aus, nach dem der Zeitplan wiederholt wird.  
  
**Wiederholen alle**  
Wählen Sie die Anzahl der Tage oder Wochen aus, die zwischen der wiederholten Ausführung des Zeitplans liegen. Bei monatlich wiederholten Zeitplänen ist diese Option nicht verfügbar.  
  
**Montag**  
Legt fest, dass der Auftrag an einem Montag ausgeführt wird. Nur bei wöchentlich wiederholten Zeitplänen verfügbar.  
  
**Dienstag**  
Legt fest, dass der Auftrag an einem Dienstag ausgeführt wird. Nur bei wöchentlich wiederholten Zeitplänen verfügbar.  
  
**Mittwoch**  
Legt fest, dass der Auftrag an einem Mittwoch ausgeführt wird. Nur bei wöchentlich wiederholten Zeitplänen verfügbar.  
  
**Donnerstag**  
Legt fest, dass der Auftrag an einem Donnerstag ausgeführt wird Nur bei wöchentlich wiederholten Zeitplänen verfügbar.  
  
**Freitag**  
Legt fest, dass der Auftrag an einem Freitag ausgeführt wird Nur bei wöchentlich wiederholten Zeitplänen verfügbar.  
  
**Samstag**  
Legt fest, dass der Auftrag an einem Samstag ausgeführt wird Nur bei wöchentlich wiederholten Zeitplänen verfügbar.  
  
**Sonntag**  
Legt fest, dass der Auftrag an einem Sonntag ausgeführt wird Nur bei wöchentlich wiederholten Zeitplänen verfügbar.  
  
**Day**  
Wählen Sie den Tag des Monats aus, an dem der Zeitplan ausgeführt werden soll. Nur bei monatlich wiederholten Zeitplänen verfügbar.  
  
**alle**  
Wählen Sie die Anzahl der Monate aus, die zwischen wiederholten Ausführungen des Zeitplans liegen sollen. Nur bei monatlich wiederholten Zeitplänen verfügbar.  
  
**Am**  
Geben Sie einen Zeitplan für den Wochentag einer bestimmten Woche des Monats an. Nur bei monatlich wiederholten Zeitplänen verfügbar.  
  
**Einmalig um**  
Legen Sie die Uhrzeit für einen täglich auszuführenden Auftrag fest.  
  
**Alle**  
Legen Sie die Anzahl von Stunden, Minuten bzw. Sekunden zwischen den Ausführungen fest.  
  
**Startdatum**  
Legt fest, ab welchem Datum dieser Zeitplan gültig ist.  
  
**Enddatum**  
Legen Sie fest, ab welchem Datum der Zeitplan nicht mehr gültig ist.  
  
**Kein Enddatum**  
Geben Sie an, dass der Zeitplan für unbestimmte Zeit gültig bleibt.  
  
## <a name="one-time-schedule-types-options"></a>Zeitplantypoptionen für einmalige Aufträge  
**Date**  
Wählen Sie das Datum aus, an dem der Auftrag ausgeführt wird.  
  
**Time**  
Wählen Sie die Uhrzeit aus, zu der der Auftrag ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
[Anlegen und Zuweisen von Zeitplänen zu Aufträgen](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Planen eines Auftrags](../../ssms/agent/schedule-a-job.md)  
  
