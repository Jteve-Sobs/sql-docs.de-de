---
title: Konfigurieren und Anzeigen von SharePoint-Protokolldateien und-Diagnoseprotokollierung (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 85f62d29-cdc6-45b3-be1f-ff1182939858
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2f05edb30344b63781a89540ade8de4743bb715e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071845"
---
# <a name="configure-and-view-sharepoint-log-files--and-diagnostic-logging-powerpivot-for-sharepoint"></a>Konfigurieren und Anzeigen der SharePoint-Protokolldateien und -Diagnoseprotokollierung (PowerPivot für SharePoint)
  
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Server-Vorgänge, Ereignisse und Meldungen werden in SharePoint-Protokolldateien aufgezeichnet. Verwenden Sie die Informationen in diesem Thema, um Protokolliergrade zu konfigurieren und Protokolldatei-Informationen anzuzeigen. Sie können steuern, welche [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Serverereignisse in einer Datei protokolliert werden. Sie können auch den Schweregrad von Meldungen steuern, die protokolliert werden. Weitere Informationen finden Sie unter [Konfigurieren der Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
 Inhalte dieses Themas:  
  
-   [Speicherort der Protokolldatei](#bkmk_filelocation)  
  
-   [Ändern der Diagnose Protokollierungs Grade für einzelne Ereignis Kategorien](#bkmk_modifyloglevels)  
  
-   [Anzeigen von SharePoint-Protokolldateien](#bkmk_how2viewlogfiles)  
  
##  <a name="bkmk_filelocation"></a>Speicherort der Protokolldatei  
 Standardmäßig werden SharePoint-Protokolldateien am folgenden Speicherort gespeichert:  
  
 `C:\Program files\Common Files\Microsoft Shared\Web Server Extensions\14\LOGS`  
  
 Der Ordner LOGS enthält Protokolldateien (`.log`), Datendateien (`.txt`) und Verwendungsdateien (`.usage`). Die Dateinamenskonvention für ein SharePoint-Ablaufverfolgungsprotokoll ist der von einem Datum und einem Zeitstempel gefolgte Servername. SharePoint-Ablaufverfolgungsprotokolle werden in regelmäßigen Abständen erstellt, sowie immer dann, wenn ein IISRESET erfolgt. Im Allgemeinen gibt es viele Ablaufverfolgungsprotokolle innerhalb eines 24 Stundenzeitraums.  
  
##  <a name="bkmk_modifyloglevels"></a>Ändern der Diagnose Protokollierungs Grade für einzelne Ereignis Kategorien  
 Standardmäßig wird die ULS-Protokollierung von PowerPivot-Ereignissen auf *Medium*festgelegt. Diese Einstellung ist für SQL Server 2012 neu. Wenn Sie einen Server von der vorherigen Version aktualisieren, könnte der Protokolliergrad immer noch auf *Ausführlich*festgelegt sein, der Standardebene in SQL Server 2008 R2. Wenn Sie daran gewöhnt sind, die ULS-Protokolle für die PowerPivot-Serverauslastung anzuzeigen, werden Sie feststellen, dass aufgrund der Änderung weniger Informationen über die PowerPivot-Servervorgänge zur Verfügung stehen.  
  
 eingeordnet. Abgesehen von Ausnahmen vom Typ *Hoch*sind alle PowerPivot-Meldungen der Kategorie Ausführlich zuzuordnen. Wenn Sie Einträge für routinemäßige Servervorgänge, beispielsweise Verbindungen, Anforderungen oder Abfrageerstellung, protokollieren möchten, müssen Sie den Protokolliergrad auf Ausführlich festlegen.  
  
 So ändern Sie diagnostische Protokolliergrade für einzelne Ereigniskategorien:  
  
1.  Klicken Sie in der SharePoint-Zentraladministration auf **Überwachung**.  
  
2.  Klicken Sie auf **Diagnoseprotokollierung konfigurieren**.  
  
3.  Führen Sie einen Bildlauf zu **PowerPivot-Dienst**durch.  
  
4.  Erweitern Sie die Kategorie, und wählen Sie einzelne Kategorien aus:  
  
     **Anwendungsseitenanforderung** gibt Ereignisse an, die von der Dienst Anwendung ausgelöst [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] werden, wenn ein zum Laden einer Power Pivot-Datenquelle und zum kommunizieren mit anderen Servern in der Farm gesucht wird.  
  
     Bei der **Anforderungs Verarbeitung** werden Ereignisse angegeben, die durch Abfrage Anforderungen für eine Power Pivot-Datenbank ausgelöst werden, die auf einem Server in der Farm geladen wird.  
  
     **Verwendung** gibt ein Ereignis im Zusammenhang mit der Power Pivot-Verwendungs Datensammlung an.  
  
5.  Wählen Sie unter Unwichtigstes, im Ereignisprotokoll aufzuzeichnendes Ereignis die Option **Keine** aus, um die Ereignisprotokollierung für die Kategorie zu deaktivieren, oder **Fehler** , um die Protokollierung auf Fehler zu beschränken.  
  
6.  Wählen Sie **Ausführlich** aus, um alle Ereignisse zum Ereignisprotokoll zu protokollieren.  
  
7.  Wählen Sie unter Unwichtigstes, im Ablaufverfolgungsprotokoll aufzuzeichnendes Ereignis die Option **Keine** aus, um die Ablaufverfolgung für die Kategorie zu deaktivieren, oder **Fehler** , um die Ablaufverfolgung auf Fehler zu beschränken.  
  
8.  Wählen Sie **Ausführlich** aus, um alle Ereignisse zum Ablaufverfolgungsprotokoll zu protokollieren.  
  
9. Klicken Sie auf **OK**.  
  
##  <a name="bkmk_how2viewlogfiles"></a>Anzeigen von SharePoint-Protokolldateien  
 Protokolldateien sind Textdateien. Sie können sie in jedem Text-Editor öffnen. Sie können auch Protokoll-Viewer-Anwendungen von Drittanbietern verwenden.  
  
#### <a name="use-a-text-editor"></a>Verwenden eines Text-Editors  
 Wenn Sie einen [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Serverfehler mit einem Text-Editor beheben, können Ihnen die folgenden Tipps dabei helfen, relevante Informationen in der Datei zu suchen:  
  
-   Für Fehler im Zusammenhang mit dem Veröffentlichen, Anzeigen oder Aktualisieren einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe, durchsuchen Sie die Protokolldatei nach dem Namen der Arbeitsmappe.  
  
-   Für Fehler, die eine Korrelations-ID ausgeben, kopieren Sie diese und verwenden Sie sie als Suchbegriff in der Protokolldatei.  
  
-   Suchen Sie nach dem Fehlerstatus "Hoch" oder "Ausnahme". Suchen Sie nach "Power Pivot-Dienst".  
  
-   Wenn Sie wissen, wann der Fehler aufgetreten ist, verwenden Sie die Datums- und Uhrzeitinformationen, um den Bereich von Einträgen, den Sie durchsuchen müssen, einzugrenzen.  
  
#### <a name="use-a-log-viewer-application"></a>Verwenden einer Protokoll-Viewer-Anwendung  
 Obwohl Sie die Ablaufverfolgungsprotokolle mithilfe eines Text-Editors einzeln anzeigen können, kann eine Protokoll-Viewer-Anwendung, die Ihnen ermöglicht, mehrere Protokolldateien anzuzeigen, viel nützlicher sein. Glücklicherweise gibt es mehrere Protokoll-Viewer-Anwendungen von Drittanbietern auf der CodePlex-Website zum Download, die Ihnen helfen können, mehrere Ablaufverfolgungsprotokolle in einem einzelnen Arbeitsbereich anzuzeigen.  
  
 Die folgenden Anweisungen enthalten Links zu gängigen SharePoint ULS Protokoll-Viewern, die Sie aus CodePlex herunterladen können.  
  
1.  Gehen Sie zu [SharePoint LogViewer](http://sharepointlogviewer.codeplex.com) oder [SharePoint ULS Log Viewer](https://go.microsoft.com/fwlink/?LinkId=150052) auf der Codeplex-Website.  
  
2.  Klicken Sie auf die Registerkarte **Downloads** .  
  
3.  Klicken Sie auf die ausführbare Datei. Es handelt sich entweder um **SharePointLogViewer.exe** oder um **ULS Viewer 2.0 Binary**.  
  
4.  Lesen Sie die Lizenzbedingungen und stimmen Sie ihnen zu.  
  
5.  Klicken Sie auf **Speichern** , um die Software auf Ihr lokales System herunterzuladen.  
  
     Wenn Sie SharePoint ULS Log Viewer herunterladen, speichern Sie ULSViewer.zip im Ordner "Downloads".  
  
6.  Klicken Sie im Ordner Downloads mit der rechten Maustaste auf „ULSViewer.zip“, und wählen Sie **Alle extrahieren**aus.  
  
7.  Geben Sie einen Zielordner an, und klicken Sie dann auf **Extrahieren**.  
  
8.  Doppelklicken Sie im Ordner, der die extrahierten Programmdateien enthält, auf **ULSViewer** , und führen Sie die Anwendung aus.  
  
9. Klicken Sie auf das Ordnersymbol oben links in der Ecke des Anwendungsfensters.  
  
10. Navigieren Sie zu \Programme\Gemeinsame Dateien\Microsoft Shared\Web Server Extensions\14\Logs.  
  
11. Wählen Sie ein oder mehrere Ablaufverfolgungsprotokolle aus. Standardmäßig bestehen Ablaufverfolgungsprotokolldateinamen aus dem Computernamen plus Datums- und Uhrzeitinformationen. Der Dateityp ist Textdokument.  
  
12. Klicken Sie auf **Öffnen** , und warten Sie, bis die Dateien geladen sind.  
  
13. Wählen Sie die Daten mithilfe der integrierten Filter nach Schweregrad, Prozess, Kategorie oder nach einer benutzerdefinierten Textdatei aus. Sie können auch auf Spaltenüberschriften klicken, um die Sortierreihenfolge zu ändern.  
  
#### <a name="entries-for-powerpivot-services"></a>Einträge für PowerPivot-Dienste  
 Die folgende Tabelle beschreibt die Einträge für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Servervorgänge, die am häufigsten in einer SharePoint-Protokolldatei gefunden werden.  
  
|Prozess|Bereich|Category|Ebene|`Message`|Details|  
|-------------|----------|--------------|-----------|-------------|-------------|  
|w3wp.exe|PowerPivot-Dienst|Verwendung|Ausführlich|Es gibt keine aktuellen Anforderungsstatistiken, nichts ist zu protokollieren.|Die Serviceberichte fragen in vordefinierten Intervallen Reaktionsstatistiken als Verwendungsereignis für das Verwendungsdatensammlungssystem ab. Diese Meldung gibt an, dass es keine Abfragestatistiken für einen Bericht gibt.|  
|w3wp.exe|PowerPivot-Dienst|Web-Front-End|Ausführlich|Starten der Suche nach einem Anwendungsserver für Datenquelle\<=*Pfad*>|Wenn das Programm eine Verbindungsanforderung empfängt, identifiziert der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Dienst einen verfügbaren [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] , um die Anforderung zu behandeln. Wenn es nur einen Server in der Farm gibt, akzeptiert der lokale Server die Anforderung in allen Fällen.|  
|w3wp.exe|PowerPivot-Dienst|Web-Front-End|Ausführlich|Die Suche nach dem Anwendungsserver war erfolgreich.|Die Anfrage wurde einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Dienstanwendung zugeordnet.|  
|w3wp.exe|PowerPivot-Dienst|Web-Front-End|Ausführlich|Umleiten der Anforderung für \<die *powerpivotdata-Quelle*> [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]an den.|Die Anforderung wurde an den [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]weitergeleitet.|  
|w3wp.exe|PowerPivot-Dienst|Anforderungsverarbeitung|Ausführlich|Umleiten der Anforderung für\<Benutzernamen-*SharePoint-Benutzer*> an die Datenbank|Eine personifizierte Verbindung zur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Datenquelle wurde für den SharePoint-Benutzer erstellt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sammlung von Power Pivot-Verwendungs Daten](power-pivot-usage-data-collection.md)   
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [Konfigurieren der Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
