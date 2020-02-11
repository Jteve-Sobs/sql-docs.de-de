---
title: Ssms-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], opening
- command prompt utilities [SQL Server], sqlwb
- sqlwb utility
- Management Studio command line
- opening SQL Server Management Studio
ms.assetid: aafda520-9e2a-4e1e-b936-1b165f1684e8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: edb7ea682ebef5d99cee7a248681be80fc433312
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63127005"
---
# <a name="ssms-utility"></a>Ssms-Hilfsprogramm
  Das **SSMS**-Hilfsprogramm wird geöffnet [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Bei entsprechender Angabe stellt **Ssms** zudem eine Verbindung mit einem Server her und öffnet Abfragen, Skripts, Dateien, Projekte und Lösungen.  
  
 Sie können Dateien angeben, die Abfragen, Projekte oder Lösungen enthalten. Für Dateien, die Abfragen enthalten, wird automatisch eine Verbindung mit einem Server hergestellt, wenn Verbindungsinformationen bereitgestellt werden und der Dateityp diesem Servertyp zugeordnet ist. So wird z. B. für SQL-Dateien ein SQL-Abfrage-Editorfenster in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]und für MDX-Dateien ein MDX-Abfrage-Editorfenster in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]geöffnet. **SQL Server Projektmappen und Projekte** werden [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]in geöffnet.  
  
> [!NOTE]  
>  Das Hilfsprogramm **Ssms** führt keine Abfragen aus. Zum Ausführen von Abfragen in der Befehlszeile verwenden Sie das **sqlcmd** -Hilfsprogramm.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      Ssms  
    [scriptfile] [projectfile] [solutionfile]  
    [-Sservername] [-ddatabasename] [-Uusername] [-Ppassword]   
    [-E] [-nosplash] [-log[filename]?] [-?]  
```  
  
## <a name="arguments"></a>Argumente  
 *scriptfile*  
 Gibt eine oder mehrere zu öffnende Skriptdateien an. Der Parameter muss den vollständigen Pfad zu den Dateien enthalten.  
  
 *ProjectFile*  
 Gibt ein zu öffnendes Skriptprojekt an. Der Parameter muss den vollständigen Pfad zur Skriptprojektdatei enthalten.  
  
 *SolutionFile*  
 Gibt eine zu öffnende Lösung an. Der Parameter muss den vollständigen Pfad zur Lösungsdatei enthalten.  
  
 [**-S** _servername_]  
 Servername  
  
 [**-d** _DatabaseName_]  
 Datenbankname  
  
 [**-U** _username_]  
 Benutzername, wenn die Verbindung mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung hergestellt wird.  
  
 [**-P** _Kennwort_]  
 Kennwort, wenn die Verbindung mithilfe der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung hergestellt wird.  
  
 [**-E**]  
 Verbindung mithilfe der Windows-Authentifizierung herstellen  
  
 [**-nosplash**]  
 Verhindert, dass [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] beim Öffnen den Begrüßungsbildschirm anzeigt. Verwenden Sie diese Option, wenn Sie eine Verbindung zum Computer mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] herstellen und hierfür Terminaldienste über eine Verbindung mit begrenzter Bandbreite einsetzen. Bei diesem Argument wird die Groß- und Kleinschreibung nicht beachtet. Es kann vor oder nach anderen Argumenten angegeben werden.  
  
 [**-Log**_[fileName]?_]  
 Protokolliert die [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] -Aktivität zur Problembehandlung in der angegebenen Datei.  
  
 [**-?**]  
 Zeigt die Hilfe zur Befehlszeile an.  
  
## <a name="remarks"></a>Bemerkungen  
 Alle Schalter sind optional und werden durch Leerzeichen voneinander getrennt. Eine Ausnahme hiervon bilden Dateien, die durch Kommas getrennt werden. Wenn Sie keine Schalter angeben, wird **Ssms** Ssms [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] so geöffnet, wie es in den Einstellungen unter **Optionen** im Menü **Extras** angegeben ist. Wenn z.B. auf der Seite **Umgebung/Allgemein** unter **Beim Start** die Option **Neues Abfragefenster öffnen**angegeben ist, öffnet **Ssms** ein leeres Abfrage-Editor-Fenster.  
  
 Der Schalter **-Log** muss am Ende der Befehlszeile nach allen anderen Schaltern angezeigt werden. Das filename-Argument ist optional. Wenn ein Dateiname angegeben wird und die Datei nicht vorhanden ist, wird sie erstellt. Wenn die Datei beispielsweise aufgrund unzureichender Schreibberechtigungen nicht erstellt werden kann, wird die Datei stattdessen in den Ordner für nicht lokalisierte Anwendungsdaten (APPDATA) geschrieben (siehe unten). Wenn das filename-Argument nicht angegeben wird, werden zwei Dateien in den Ordner für nicht lokalisierte Anwendungsdaten des aktuellen Benutzers geschrieben. Der Ordner für nicht lokalisierte Anwendungsdaten in SQL Server kann anhand der APPDATA-Umgebungsvariablen ermittelt werden. Für SQL Server 2012 lautet der Ordner beispielsweise \<Systemlaufwerk>:\Users\\<Benutzername\>\AppData\Roaming\Microsoft\AppEnv\10.0\\. Die beiden Dateien erhalten standardmäßig den Namen ActivityLog.xml und ActivityLog.xsl. Die erste Datei enthält die Aktivitätsprotokolldaten, und die zweite Datei ist ein XML-Stylesheet, mit dem die XML-Datei auf bequeme Weise angezeigt werden kann. Führen Sie die folgenden Schritte aus, um die Protokolldatei in einem standardmäßigen XML-Viewer wie Internet Explorer anzuzeigen: Klicken Sie auf „Start“ und dann auf „Ausführen“. Geben Sie dann „\<Systemlaufwerk>:\Users\\<Benutzername\>\AppData\Roaming\Microsoft\AppEnv\10.0\ActivityLog.xml“ in das angezeigte Feld ein, und drücken Sie die EINGABETASTE.  
  
 Dateien, die Abfragen enthalten, fordern eine Verbindung mit einem Server an, wenn Verbindungsinformationen bereitgestellt werden und der Dateityp diesem Servertyp zugeordnet ist. So wird z. B. für SQL-Dateien ein SQL-Abfrage-Editorfenster in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]und für MDX-Dateien ein MDX-Abfrage-Editorfenster in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]geöffnet. **SQL Server Projektmappen und Projekte** werden [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]in geöffnet.  
  
 In der folgenden Tabelle werden Servertypen zu Dateierweiterungen zugeordnet.  
  
|Servertyp|Durchwahl|  
|-----------------|---------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|.sql|  
|SQL Server Analysis Services|MDX<br /><br /> .xmla|  
  
## <a name="examples"></a>Beispiele  
 Mit dem folgenden Skript wird [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] mit den Standardeinstellungen von der Eingabeaufforderung aus geöffnet.  
  
```  
Ssms  
  
```  
  
 Mit dem folgenden Skript wird [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] von der Eingabeaufforderung aus geöffnet. Es wird die Windows-Authentifizierung verwendet, im Code-Editor wird der Server `ACCTG and the database AdventureWorks2012,` ausgewählt, und der Begrüßungsbildschirm wird nicht angezeigt:  
  
```  
Ssms -E -S ACCTG -d AdventureWorks2012 -nosplash  
  
```  
  
 Mit dem folgenden Skript wird [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] von der Eingabeaufforderung aus geöffnet. Anschließend wird das Skript MonthEndQuery geöffnet.  
  
```  
Ssms "C:\Documents and Settings\username\My Documents\SQL Server Management Studio Projects\FinanceScripts\FinanceScripts\MonthEndQuery.sql"  
  
```  
  
 Mit dem folgenden Skript wird [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] von der Eingabeaufforderung aus geöffnet. Anschließend wird das Projekt NewReportsProject auf dem Computer `developer`geöffnet:  
  
```  
Ssms "\\developer\fin\ReportProj\ReportProj\NewReportProj.ssmssqlproj"  
  
```  
  
 Mit dem folgenden Skript wird [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] von der Eingabeaufforderung aus geöffnet. Anschließend wird die Lösung MonthlyReports geöffnet:  
  
```  
Ssms "C:\solutionsfolder\ReportProj\MonthlyReports.ssmssln"  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)  
  
  
