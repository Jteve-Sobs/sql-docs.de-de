---
title: Eigenschaften eines neuen Auftragsschritts (Seite „Allgemein“)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.stepgeneral.f1
ms.assetid: 8d1885ba-4386-4528-8f2b-68c16852720c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 44b333c1865046f779581265fb49186810f8944c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731400"
---
# <a name="job-step-properties---new-job-step-general-page"></a>Auftragsschritt-Eigenschaften – Neuer Auftragsschritt (Seite „Allgemein“)

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die Eigenschaften eines Auftragsschritts für den [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent abrufen und ändern oder einen neuen Auftragsschritt definieren.  
  
Erweitern Sie im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent, klicken Sie mit der rechten Maustaste auf **Aufträge**, klicken Sie auf **Neuer Auftrag**, wählen Sie die Seite **Schritte** aus, und klicken Sie auf **Neu**, um zu dieser Seite zu navigieren. Sie können auch zu dieser Seite navigieren, indem Sie mit der rechten Maustaste auf einen Auftrag im Objekt-Explorer klicken, auf **Eigenschaften**klicken, die Seite **Schritte** auswählen, und auf **Neu**, **Einfügen**oder **Bearbeiten**klicken.  
  
## <a name="options"></a>Tastatur  
**Schrittname**  
Legt den Namen des Auftrags fest.  
  
**Typ**  
Legt das durch den Auftrag verwendete Subsystem fest. Basierend auf dem von Ihnen ausgewählten Subsystem ändern sich die für das Definieren des Auftragsschritts angezeigten Optionen.  
  
**Ausführen als**  
Legt das Proxykonto für den Auftragsschritt fest. Mitglieder der festen Serverrolle „sysadmin“ können auch das **SQL-Agent-Dienstkonto**angeben.  
  
**Datenbank**  
Legt die Datenbank fest, in der der Auftragsschritt ausgeführt wird. Diese Option ist nicht für alle Auftragsschritttypen verfügbar.  
  
**Befehl**  
Legt den durch den Auftrag ausgeführten Befehl fest.  
  
## <a name="options-for-transact-sql-job-steps"></a>Optionen für Transact-SQL-Auftragsschritte  
**Öffnen**  
Lädt den Befehl aus einer Datei.  
  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den ausgewählten Text in die Zwischenablage.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
**Analysieren**  
Überprüft die Syntax des Befehls.  
  
## <a name="options-for-activex-script-job-steps"></a>Optionen für Auftragsschritte von ActiveX-Skript  
  
> [!IMPORTANT]
> Das ActiveX Scripting-Subsystem wird in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus dem [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.  
  
**VBScript**  
Gibt [!INCLUDE[msCoName](../../includes/msconame_md.md)] VBScript als Sprache für die Auftragsschritte an.  
  
**JScript**  
Gibt JScript als Sprache für die Auftragsschritte an.  
  
**Andere**  
Geben Sie den Namen der Sprache für Auftragsschritte ein, die in einer anderen Skriptsprache geschrieben wurden.  
  
**Öffnen**  
Lädt den Befehl aus einer Datei.  
  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Optionen für Auftragsschritte des Betriebssystems (CmdExec)  
**Prozessexitcode eines erfolgreichen Befehls**  
Geben Sie den Exitcode ein, den der Befehl zurückgibt, um einen Erfolg zu melden.  
  
**Öffnen**  
Lädt den Befehl aus einer Datei.  
  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-powershell-job-steps"></a>Optionen für PowerShell-Auftragsschritte  
**Öffnen**  
Lädt das Skript aus einer Datei.  
  
**Alles markieren**  
Markiert den Text des Skripts.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-distributor-job-steps"></a>Optionen für Replikationsverteiler-Auftragsschritte  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-merge-job-steps"></a>Optionen für Replikationsmerge-Auftragsschritte  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Optionen für Auftragsschritte des Replikation-Warteschlangenlesers  
**Datenbank**  
Die Datenbank, die für den Auftragsschritt verwendet werden soll.  
  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-snapshot-job-steps"></a>Optionen für Replikationsmomentaufnahme-Auftragsschritte  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-transaction-log-reader-job-steps"></a>Optionen für Auftragsschritte des Replikationstransaktionsprotokoll-Lesers  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-sql-server-analysis-services-command-job-steps"></a>Optionen für Auftragsschritte von SQL Server Analysis Services-Befehlen  
**Server**  
Wählt den Server aus, auf dem der Auftragsschritt ausgeführt wird.  
  
**Öffnen**  
Lädt den Befehl aus einer Datei.  
  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-sql-server-analysis-services-query-job-steps"></a>Optionen für Auftragsschritte von SQL Server Analysis Services-Abfragen  
**Server**  
Wählt den Server aus, auf dem der Auftragsschritt ausgeführt wird.  
  
**Datenbank**  
Die Datenbank, die für den Auftragsschritt verwendet werden soll.  
  
**Öffnen**  
Lädt den Befehl aus einer Datei.  
  
**Alles markieren**  
Markiert den Text des Befehls.  
  
**Copy**  
Kopiert den markierten Text.  
  
**Einfügen**  
Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-integration-services-package-execution-job-steps"></a>Optionen für Auftragsschritte von Integration Services-Paketausführungen  
  
### <a name="general-tab"></a>Registerkarte Allgemein  
Gibt den Speicherort des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis_md.md)])-Pakets an, und welche Authentifizierungsmethode verwendet werden soll. Die folgenden Optionen sind verfügbar, wenn Sie diese Registerkarte auswählen.  
  
**Paketquelle**  
Gibt den Speicherort des [!INCLUDE[ssIS](../../includes/ssis_md.md)] -Pakets an. Wählen Sie eine der folgenden Optionen aus:  
  
-   **SQL Server**  
  
-   **Dateisystem**  
  
-   **SSIS-Paketspeicher**  
  
**Server**  
Geben Sie den Namen des Servers ein, auf dem das [!INCLUDE[ssIS](../../includes/ssis_md.md)] -Paket gespeichert ist. Diese Option ist nur verfügbar, wenn **SQL Server** oder **SSIS-Paketspeicher** für **Paketquelle**angegeben ist.  
  
**Windows-Authentifizierung verwenden**  
Für Anmeldungen bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows-Authentifizierung verwendet.  
  
**SQL Server-Authentifizierung verwenden**  
Für Anmeldungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet. Wenn diese Authentifizierungsmethode ausgewählt wurde, geben Sie entsprechend **Benutzername** und **Kennwort**ein.  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung wird aus Gründen der Abwärtskompatibilität bereitgestellt. Aus Sicherheitsgründen sollte möglichst die Windows-Authentifizierung verwendet werden.  
  
**Paket**  
Geben Sie den Speicherort des Pakets ein.  
  
> [!IMPORTANT]  
> Klicken Sie für kennwortgeschützte [!INCLUDE[ssIS](../../includes/ssis_md.md)] -Pakete auf die Registerkarte **Konfigurationen** , um das Kennwort im Dialogfeld **Paketkennwort** einzugeben. Andernfalls erzeugt der Auftrag des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, der das kennwortgeschützte Paket ausführt, einen Fehler.  
  
### <a name="configurations-tab"></a>Registerkarte Konfigurationen  
Gibt Konfigurationsoptionen für das [!INCLUDE[ssIS](../../includes/ssis_md.md)] -Paket an. Wenn Sie diese Registerkarte auswählen, sind die folgenden Optionen verfügbar.  
  
**Konfigurationsdateien**  
Führt die Konfigurationsdateien für das Paket in einer Liste auf.  
  
**Add (Hinzufügen)**  
Fügt eine Konfigurationsdatei für das Paket hinzu.  
  
**Remove**  
Entfernt eine Konfigurationsdatei für das Paket.  
  
**Nach oben**  
Verschiebt die ausgewählte Konfigurationsdatei nach oben.  
  
**Nach unten**  
Verschiebt die ausgewählte Konfigurationsdatei nach unten.  
  
### <a name="command-files-tab"></a>Registerkarte Befehlsdateien  
Wählt Befehlsdateien für das Paket aus. Befehlsdateien werden entsprechend ihrer Reihenfolge in der Liste verarbeitet. Die folgenden Optionen sind verfügbar, wenn Sie diese Registerkarte auswählen.  
  
**Befehlsdateien**  
Führt die Befehlsdateien für das Paket in einer Liste auf.  
  
**Add (Hinzufügen)**  
Fügt eine Befehlsdatei hinzu.  
  
**Remove**  
Entfernt die ausgewählte Befehlsdatei.  
  
**Nach oben**  
Verschiebt die ausgewählte Befehlsdatei nach oben.  
  
**Nach unten**  
Verschiebt die ausgewählte Befehlsdatei nach unten.  
  
### <a name="data-sources-tab"></a>Registerkarte Datenquellen  
Zeigt die im Paket angegebenen Datenquellen auf dieser Registerkarte an.  
  
**Verbindungs-Manager**  
Zeigt den Namen der Datenquelle an.  
  
**Beschreibung**  
Zeigt die Beschreibung der Datenquelle an.  
  
**Verbindungszeichenfolge**  
Zeigt die Verbindungszeichenfolge für die Datenquelle an.  
  
### <a name="execution-options-tab"></a>Registerkarte Ausführungsoptionen  
Zeigt die Ausführungsoptionen für das Paket auf dieser Registerkarte an oder ändert die Werte.  
  
**Paket bei Überprüfungswarnungen fehlschlagen lassen**  
Wählen Sie diese Option aus, wenn die Paketausführung bei Überprüfungswarnungen fehlschlagen soll.  
  
**Paket ohne Ausführung überprüfen**  
Wählen Sie diese Option für den Auftragsschritt aus, wenn das Paket überprüft, nicht jedoch ausgeführt werden soll.  
  
**Maximale Anzahl von gleichzeitig ausführbaren Dateien**  
Die maximale Anzahl der gleichzeitig ausführbaren Dateien.  
  
**Paketprüfpunkte aktivieren**  
Wählen Sie diese Option für den Auftragsschritt aus, wenn Paketprüfpunkte verwendet werden sollen.  
  
**Prüfpunktdatei**  
Geben Sie den Namen der Prüfpunktdatei des Pakets ein.  
  
**...**  
Sucht nach der Prüfpunktdatei des Pakets.  
  
**Neustartoptionen überschreiben**  
Wenn Sie diese Option auswählen, können Sie für diesen Auftragsschritt Neustartoptionen angeben, die von den im Paket angegebenen Optionen abweichen.  
  
**Neustartoption**  
Wählt die Aktion aus, die bei einem Neustart des Pakets durchgeführt werden soll.  
  
### <a name="logging-tab"></a>Registerkarte Protokollierung  
Zeigt die Protokollanbieter für das Paket auf dieser Registerkarte an oder ändert diese.  
  
**Protokollanbieter**  
Wählt die ClassID für den Protokollanbieter aus.  
  
**Konfigurationszeichenfolge**  
Geben Sie die Konfigurationszeichenfolge für den Protokollanbieter ein.  
  
**Remove**  
Entfernt den Protokollanbieter.  
  
### <a name="set-values-tab"></a>Registerkarte Werte festlegen  
Zeigt die Eigenschaftswerte für das Paket auf dieser Registerkarte an oder ändert die Werte.  
  
**Eigenschaftspfad**  
Zeigt einen Pfad für die Eigenschaft an oder ändert diese.  
  
**Wert**  
Zeigt einen Wert für die Eigenschaft an oder ändert diesen.  
  
**Remove**  
Entfernt die Eigenschaft.  
  
### <a name="verification-tab"></a>Registerkarte Überprüfung  
Wählt die Überprüfungsoptionen für den Auftragsschritt auf dieser Registerkarte aus.  
  
**Nur signierte Pakete ausführen**  
Führt nur Pakete aus, die signiert wurden. Bei Auswahl dieser Option schlägt der Auftragsschritt fehlt, wenn das Paket nicht signiert ist.  
  
**Paketbuild überprüfen**  
Führt nur Pakete aus, die eine bestimmte Buildnummer besitzen. Bei Auswahl dieser Option schlägt der Auftragsschritt fehl, wenn das Paket nicht die angegebene Buildnummer besitzt.  
  
**Build**  
Geben Sie die Buildnummer des Pakets ein.  
  
**Paket-ID überprüfen**  
Führt nur Pakete aus, die eine bestimmte ID besitzen. Bei Auswahl dieser Option schlägt der Auftragsschritt fehl, wenn das Paket nicht die angegebene ID besitzt.  
  
**Paket-ID**  
Geben Sie die Paket-ID ein.  
  
**Versions-ID überprüfen**  
Führt nur Pakete mit einer bestimmten Versions-ID aus. Bei Auswahl dieser Option schlägt der Auftragsschritt fehl, wenn das Paket nicht die angegebene Versions-ID besitzt.  
  
**Versions-ID**  
Geben Sie die Versions-ID ein.  
  
### <a name="command-line-tab"></a>Registerkarte Befehlszeile  
Gibt die Befehlszeilenoptionen für das Paket an. Wenn Sie diese Registerkarte auswählen, sind die folgenden Optionen verfügbar.  
  
**Die ursprünglichen Optionen wiederherstellen**  
Verwendet die in diesem Dialogfeld festgelegten Befehlszeilenoptionen.  
  
**Befehlszeile manuell bearbeiten**  
Gibt die Optionen im Befehlszeilenfenster an.  
  
**Befehlszeile**  
Geben Sie die für dieses Paket zu verwendenden Befehlszeilenoptionen ein.  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwalten von Auftragsschritten](../../ssms/agent/manage-job-steps.md)  
[Aufträge des SQL Server-Agents für Pakete](../../integration-services/packages/sql-server-agent-jobs-for-packages.md)  
[Verwalten der Replikations-Agents](../../relational-databases/replication/agents/replication-agent-administration.md)  
  
