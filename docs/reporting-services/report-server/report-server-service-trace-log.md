---
title: Berichtsserverdienst-Ablaufverfolgungsprotokoll
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 04/23/2019
ms.openlocfilehash: 667f18f449a1f2564c04a03ca593c917a7b46005
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "68254866"
---
# <a name="report-server-service-trace-log"></a>Berichtsserverdienst-Ablaufverfolgungsprotokoll

Bei den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsserver-Ablaufverfolgungsprotokollen handelt es sich um ASCII-Textdateien, die detaillierte Informationen zu den Vorgängen des Berichtsserverdiensts enthält.  Die Informationen in der Datei umfassen Vorgänge, die vom Berichtsserver-Webdienst, vom Webportal und von der Hintergrundverarbeitung durchgeführt wurden. In den Ablaufverfolgungsprotokollen sind redundante Informationen gespeichert, die in anderen Protokolldateien aufgezeichnet werden, sowie zusätzliche Informationen, die anderweitig nicht verfügbar sind. Ablaufverfolgungsinformationen sind beispielsweise zum Debuggen einer Anwendung, die einen Berichtsserver enthält, oder zum Analysieren eines bestimmten Problems, das ins Ereignis- oder Ausführungsprotokoll geschrieben wurde, nützlich sein. Zum Beispiel bei der Behandlung von Problemen mit Abonnements.  

## <a name="where-are-the-report-server-log-files"></a><a name="bkmk_view_log"></a> Wo befinden sich die Protokolldateien des Berichtsservers?

Die Ablaufverfolgungs-Protokolldateien sind `ReportServerService_<timestamp>.log` und `Microsoft.ReportingServices.Portal.WebHost_<timestamp>.log`. Diese befinden sich in folgendem Ordner:

`C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\LogFiles` 

Die Ablaufverfolgungsprotokolle werden täglich erstellt, beginnend mit dem ersten Eintrag nach Mitternacht (lokale Zeit) sowie nach Neustart des Diensts. Der Timestamp basiert auf der koordinierten Weltzeit (UTC). Die Datei liegt im Format EN-US vor. Standardmäßig sind Ablaufverfolgungsprotokolle auf 32 Megabyte begrenzt und werden nach 14 Tagen gelöscht.  

## <a name="trace-configuration-settings"></a><a name="bkmk_trace_configuration_settings"></a> Konfigurationseinstellungen für die Ablaufverfolgung

Das Verhalten der Ablaufverfolgungsprotokolle wird in der Konfigurationsdatei **ReportingServicesService.exe.config** verwaltet. Die Konfigurationsdatei befindet sich unter folgendem Ordnerpfad:  
  
 `\Program Files\Microsoft SQL Server\MSRS13.<instance name>\Reporting Services\ReportServer\bin`.  
  
 Im folgenden Beispiel wird die XML-Struktur der **RStrace** -Einstellungen veranschaulicht. Der Wert für **DefaultTraceSwitch** bestimmt die Art der Informationen, die dem Protokoll hinzugefügt werden. Mit Ausnahme des **Components** -Attributs sind die Werte für **RStrace** in den Konfigurationsdateien identisch.  
  
```
  \<system.diagnostics>
    <switches>
      <add name="DefaultTraceSwitch" value="3" />
    </switches>
  \</system.diagnostics>
  <RStrace>
    <add name="FileName" value="ReportServerService_" />
    <add name="FileSizeLimitMb" value="32" />
    <add name="KeepFilesForDays" value="14" />
    <add name="Prefix" value="appdomain, tid, time" />
    <add name="TraceListeners" value="file" />
    <add name="TraceFileMode" value="unique" />
    <add name="Components" value="all:3" />
  </RStrace>
```  
  
 Die folgende Tabelle enthält Informationen zu den einzelnen Einstellungen.  
  
|Einstellung|BESCHREIBUNG|Werte|  
|-------------|-----------------|------------|  
|**RStrace**|Gibt Namespaces an, die für Fehler und für die Ablaufverfolgung verwendet werden.||  
|**DefaultTraceSwitch**|Gibt die Ebene der Informationen an, die im Ablaufverfolgungsprotokoll ReportServerService aufgezeichnet werden. Jede Ebene enthält jeweils die Informationen aller niedrigerer Ebenen. Das Deaktivieren der Ablaufverfolgung wird nicht empfohlen.|Gültige Werte sind:<br /><br /> <br /><br /> 0= Deaktiviert die Ablaufverfolgung. Das ReportServerService-Protokoll ist standardmäßig aktiviert. Um diese Funktion zu deaktivieren, legen Sie die Ablaufverfolgungsebene auf 0 fest.<br /><br /> 1= Ausnahmen und Neustarts<br /><br /> 2= Ausnahmen, Neustarts, Warnungen<br /><br /> 3= Ausnahmen, Neustarts, Warnungen, Statusmeldungen (Standard)<br /><br /> 4= Ausführlicher Modus|  
|**FileName**|Gibt den ersten Teil des Protokolldateinamens an. Der Wert von **Prefix** ergänzt den restlichen Namen.||  
|**FileSizeLimitMb**|Gibt eine Obergrenze für die Größe des Ablaufverfolgungsprotokolls an. Die Datei wird in Megabytes gemessen.<br /><br /> Sie können die Dateigröße beeinflussen, indem Sie Ablaufverfolgungsebenen festlegen (0 bis 4), um zu steuern, wie viel Inhalt aufgezeichnet wird. Zudem können Sie angeben, welche Bestandteile verfolgt werden. Wenn das Maximum der Protokolldatei vor dem Ablaufdatum von 14 Tagen erreicht wird, werden ältere Einträge durch neuere Einträge ersetzt.|Gültige Werte sind 0 bis zu einer maximalen ganzen Zahl. Der Standardwert ist 32. Wenn Sie 0 oder eine negative Zahl angeben, wird dieser Wert vom Berichtsserver wie der Wert 1 behandelt.|  
|**KeepFilesForDays**|Gibt die Anzahl von Tagen an, nach der eine Ablaufverfolgungs-Protokolldatei gelöscht wird.|Gültige Werte sind 0 bis zu einer maximalen ganzen Zahl. Der Standardwert ist 14. Wenn Sie 0 oder eine negative Zahl angeben, wird dieser Wert vom Berichtsserver wie der Wert 1 behandelt.|  
|**Präfix**|Gibt einen generierten Wert an, der die Protokollinstanzen voneinander unterscheidet.|Standardmäßig werden Timestampwerte an die Dateinamen von Ablaufverfolgungsprotokollen angehängt. Dieser Wert wird auf „appdomain, tid, time“ festgelegt. Ändern Sie diese Einstellung nicht.|  
|**TraceListeners**|Gibt die Zieladresse für die Ausgabe des Inhalts von Ablaufverfolgungsprotokollen an. Sie können mehrere durch Trennzeichen getrennte Ziele angeben.|Gültige Werte sind:<br /><br /> <br /><br /> DebugWindow<br /><br /> File (Standard)<br /><br /> StdOut|  
|**TraceFileMode**|Gibt an, ob Ablaufverfolgungsprotokolle Daten für einen Zeitraum von 24 Stunden enthalten. Für jede Komponente sollte pro Tag ein eindeutiges Ablaufverfolgungsprotokoll erstellt werden.|Dieser Wert wird auf "Unique (Standard)" festgelegt. Ändern Sie diesen Wert nicht.|  
|**Komponentenkategorie**|Gibt die Komponenten, für die Ablaufverfolgungsprotokoll-Informationen generiert werden, sowie die Ablaufverfolgungsebene in diesem Format an:<br /><br /> \<Komponentenkategorie>:\<Ablaufverfolgungsebene><br /><br /> Sie können alle oder einige der Komponenten (**all**, **RunningJobs**, **SemanticQueryEngine**, **SemanticModelGenerator**) angeben. Wenn Informationen für eine bestimmte Komponente nicht generiert werden sollen, können Sie deren Ablaufverfolgung deaktivieren (z. B. "SemanticModelGenerator:0"). Deaktivieren Sie nicht die Ablaufverfolgung für **all**.<br /><br /> Sie können "SemanticQueryEngine:4" festlegen, wenn Sie die für jede Semantikabfrage generierten Transact-SQL-Anweisungen anzeigen möchten. Die Transact-SQL-Anweisungen werden im Ablaufverfolgungsprotokoll aufgezeichnet. Im folgenden Beispiel wird die Konfigurationseinstellung veranschaulicht, die dem Protokoll Transact-SQL-Anweisungen hinzufügt:<br /><br /> \<add name="Komponenten" value="all,SemanticQueryEngine:4" />|Für Komponentenkategorien kann Folgendes festgelegt werden:<br /><br /> <br /><br /> **All** wird zur Ablaufverfolgung der allgemeinen Berichtsserveraktivität für alle Vorgänge verwendet, die nicht in die einzelnen Kategorien unterteilt werden.<br /><br /> **RunningJobs** wird für die Ablaufverfolgung eines gegenwärtig ausgeführten Berichts oder eines Abonnementvorgangs verwendet.<br /><br /> **SemanticQueryEngine** wird für die Ablaufverfolgung einer Semantikabfrage verwendet, die verarbeitet wird, wenn ein Benutzer eine Ad-hoc-Durchsuchung von Daten in einem modellbasierten Bericht ausführt.<br /><br /> **SemanticModelGenerator** wird für die Ablaufverfolgung der Modellgenerierung verwendet.<br /><br /> **http** wird verwendet, um die Berichtsserver-HTTP-Protokolldatei zu aktivieren. Weitere Informationen finden Sie unter [Report Server HTTP Log](../../reporting-services/report-server/report-server-http-log.md).|  
|**trace level**-Wert (Wert auf Ablaufverfolgungsebene) für Komponentenkategorien|\<Komponentenkategorie>:\<Ablaufverfolgungsebene><br /><br /> <br /><br /> Wenn Sie keine Ablaufverfolgungsebene an die Komponente anfügen, wird der für **DefaultTraceSwitch** angegebene Wert verwendet. Wenn Sie beispielsweise "all,RunningJobs,SemanticQueryEngine,SemanticModelGenerator" angeben, verwenden alle Komponenten die Standard-Ablaufverfolgungsebene.|Gültige Werte für die Ablaufverfolgungsebene sind Folgende:<br /><br /> <br /><br /> 0= Deaktiviert die Ablaufverfolgung<br /><br /> 1= Ausnahmen und Neustarts<br /><br /> 2= Ausnahmen, Neustarts, Warnungen<br /><br /> 3= Ausnahmen, Neustarts, Warnungen, Statusmeldungen (Standard)<br /><br /> 4= Ausführlicher Modus<br /><br /> Der Standardwert für Berichtsserver ist: "all:3".|  
  
## <a name="adding-custom-configuration-setting-to-specify-a-dump-file-location"></a><a name="bkmk_add_custom"></a> Hinzufügen einer benutzerdefinierten Konfigurationseinstellung zum Angeben eines Speicherortes für eine Sicherungsdatei  
Sie können dem Speicherort, der vom Windows-Tool Dr. Watson zum Speichern von Sicherungsdateien verwendet wird, eine benutzerdefinierte Einstellung hinzufügen. Die benutzerdefinierte Einstellung ist **Directory**. Im folgenden Beispiel wird veranschaulicht, wie diese Konfigurationseinstellung im Abschnitt **RStrace** angegeben wird:  

```
<add name="Directory" value="U:\logs\" />  
```  
  
Weitere Informationen finden Sie im [Knowledge Base-Artikel 913046](https://support.microsoft.com/?kbid=913046) auf der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Website.  
  
##  <a name="log-file-fields"></a><a name="bkmk_log_file_fields"></a> Protokolldateifelder

Ein Ablaufverfolgungsprotokoll enthält folgende Felder:  
  
- Systeminformationen, einschließlich Betriebssystem, Version, Anzahl der Prozessoren und Arbeitsspeicher.  
  
- [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponente und Versionsinformationen.  
  
- Im Anwendungsprotokoll protokollierte Ereignisse.  
  
- Vom Berichtsserver generierte Ausnahmen.  
  
- Von einem Berichtsserver protokollierte Warnungen wegen unzureichender Ressourcen.  
  
- Eingehende SOAP-Umschläge und zusammengefasste ausgehende SOAP-Umschläge.  
  
- Informationen zu HTTP-Header, Stapelüberwachung und Debugablaufverfolgung.  
  
 Sie können anhand der Informationen im Ablaufverfolgungsprotokoll bestimmen, ob ein Bericht übermittelt wurde, wer den Bericht empfangen hat und wie viele Übermittlungsversuche unternommen wurden. Ablaufverfolgungsprotokolle zeichnen auch Berichtsausführungsaktivitäten sowie die Umgebungsvariablen auf, die bei der Berichtsverarbeitung verwendet werden. Fehler und Ausnahmen werden ebenfalls in Ablaufverfolgungsprotokollen aufgezeichnet. Dazu zählen beispielsweise Berichtstimeoutfehler (erkennbar am **ThreadAbortExceptions** -Eintrag).  

## <a name="previous-versions"></a>Vorgängerversionen

In vorherigen Releases von [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]waren mehrere Ablaufverfolgungs-Protokolldateien vorhanden, eine pro Anwendung. Die folgenden Dateien sind veraltet und werden in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen nicht mehr erstellt:
+ ReportServerWebApp_ *\<Zeitstempel>* .log
+ ReportServer_ *\<Zeitstempel>* .log
+ ReportServerService_main_ *\<Zeitstempel>* .log
  
## <a name="see-also"></a>Weitere Informationen

- [Reporting Services Log Files and Sources (Reporting Services-Protokolldateien und -Quellen)](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
- [Fehler- und Ereignisreferenz &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  

Haben Sie dazu Fragen? [Besuchen Sie das Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)