---
title: Ändern der Zielwiederherstellungszeit einer Datenbank (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab366052f60d6039fcfe8060fd702d762146a304
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084142"
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a>Ändern der Zielwiederherstellungszeit einer Datenbank (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie die Zielwiederherstellungszeit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]geändert wird. Standardmäßig beträgt die Zielwiederherstellungszeit 60 Sekunden, und die Datenbank verwendet *indirekte Prüfpunkte*. Die Zielwiederherstellungszeit richtet eine Obergrenze der Wiederherstellungszeit für diese Datenbank ein.  
  
> [!NOTE]  
>  Die Obergrenze, die für eine bestimmte Datenbank durch die Wiederherstellungszeiteinstellung für das Ziel angegeben wird, könnte überschritten werden, wenn eine Transaktion mit langer Laufzeit übermäßig lange UNDO-Zeiten verursacht.  
  
-   **Vorbereitungen:**  [Beschränkungen](#Restrictions), [Sicherheit](#Security)  
  
-   **So ändern Sie die Zielwiederherstellungszeit mithilfe von:**  [SQL Server Management Studio](#SSMSProcedure) oder [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen 
  
> [!CAUTION]  
>  Im Fall einer Arbeitsauslastung für Onlinetransaktionen bei einer Datenbank, die für indirekte Prüfpunkte konfiguriert ist, kann eine Verringerung der Leistung auftreten. Indirekte Prüfpunkte stellen sicher, dass die Anzahl der modifizierten Seiten unter einem bestimmten Schwellenwert liegt, sodass die Datenbankwiederherstellung innerhalb der Zielwiederherstellungszeit abgeschlossen wird. Die Konfigurationsoption „Wiederherstellungsintervall“ ermittelt die Wiederherstellungszeit über die Anzahl der Transaktionen. Im Gegensatz dazu greifen indirekte Prüfpunkte auf die Anzahl der modifizierten Seiten zurück. Wenn für eine Datenbank, die eine große Anzahl von DML-Vorgängen empfängt, indirekte Prüfpunkte aktiviert sind, können beim Schreiben im Hintergrund leere modifizierte Puffer aggressiv auf den Datenträger geleert werden. Dadurch wird sichergestellt, dass der Zeitaufwand für die Wiederherstellung innerhalb der Zielwiederherstellungszeit der Datenbank liegt. Dies kann auf bestimmten Systemen zusätzliche E/A-Aktivitäten verursachen, die zu einem Leistungsengpass beitragen können, wenn das Datenträgersubsystem über oder nahe dem E/A-Schwellenwert arbeitet.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So ändern Sie die Zielwiederherstellungszeit**  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie diese Instanz.  
  
2.  Erweitern Sie den Container **Datenbanken**, und klicken Sie dann mit der rechten Maustaste auf die Datenbank, die geändert werden soll. Klicken Sie anschließend auf den Befehl **Eigenschaften**.  
  
3.  Klicken Sie im Dialogfeld **Datenbankeigenschaften** auf die Seite **Optionen** .  
  
4.  Geben Sie im Bereich **Wiederherstellung** im Feld **Zielwiederherstellungszeit (Sekunden)** die Anzahl von Sekunden als gewünschte Obergrenze der Wiederherstellungszeit für diese Datenbank an.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So ändern Sie die Zielwiederherstellungszeit**  
  
1.  Stellen Sie eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, auf der sich die Datenbank befindet.  
  
2.  Verwenden Sie die folgende [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-set-options.md)-Anweisung wie folgt:  
  
     TARGET_RECOVERY_TIME **=** _target_recovery_time_ { SECONDS | MINUTES }  
  
     *target_recovery_time*  
     Ab [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]ist der Standardwert gleich 1 Minute. Gibt bei einem Wert größer als 0 (der Standardwert für ältere Versionen) die Obergrenze der Wiederherstellungszeit für die angegebene Datenbank im Fall eines Absturzes an.  
  
     SECONDS  
     Gibt an, dass *target_recovery_time* die Anzahl von Sekunden darstellt.  
  
     MINUTES  
     Gibt an, dass *target_recovery_time* die Anzahl von Minuten darstellt.  
  
     Im folgenden Beispiel wird die Zielwiederherstellungszeit der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank auf `60` Sekunden festgelegt.  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankprüfpunkte &#40;SQL Server&#41;](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
