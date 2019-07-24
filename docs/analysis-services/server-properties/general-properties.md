---
title: Allgemeine Eigenschaften Analysis Services | Microsoft-Dokumentation
ms.date: 07/24/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d0d2a1fd8a83c4b181dfc182f5fb5630e29c9efb
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419517"
---
# <a name="general-properties"></a>Allgemeine Eigenschaften
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt die in den folgenden Tabellen aufgeführten Servereigenschaften. In diesem Thema werden die Servereigenschaften in der Datei msmdsrv.ini dokumentiert, die nicht in einem bestimmten Abschnitt wie Sicherheit, Netzwerk oder ThreadPool behandelt werden. Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Servereigenschaften in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 Diese Eigenschaften gelten für den mehrdimensionalen und tabellarischen Server Modus, sofern nichts anderes angegeben ist.  
  
## <a name="non-specific-category"></a>Nicht spezifische Kategorie  
 **AdminTimeout**  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die den Administratortimeoutwert in Sekunden definiert. Hierbei handelt es sich um eine erweiterte Eigenschaft, die nicht ohne die Unterstützung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 Der Standardwert für diese Eigenschaft ist Null (0), d. h. es findet kein Timeout statt.  
  
 **AllowedBrowsingFolders**  
 Eine Zeichenfolgeneigenschaft, die in einer getrennten Liste die Ordner angibt, die durchsucht werden können, wenn Dateien in Analysis Services-Dialogfeldern gespeichert, geöffnet und gesucht werden. Das Analysis Services-Dienstkonto muss Lese- und Schreibberechtigungen für alle Ordner haben, die Sie der Liste hinzufügen.  
  
 **BackupDir**  
 Eine Zeichen folgen Eigenschaft, die den Namen des Verzeichnisses identifiziert, in dem Sicherungsdateien standardmäßig gespeichert werden, im Fall, dass kein Pfad als Teil des Backup-Befehls angegeben wird.  
 
**Clientcacherefreshpolicy** Bei tabellarischen Modellen in SSAS und Azure Analysis Services überschreibt diese Eigenschaft die Einstellung für die **geplante Cache Aktualisierung** für alle Power BI Datasets. Alle Live Connect-Berichte beobachten die Einstellung auf Serverebene unabhängig von der Einstellung auf Datasetebene oder dem Arbeitsbereich, in dem Sie sich befinden.

Der Standardwert für diese Eigenschaft ist-1. Dadurch werden alle Aktualisierungen des Hintergrund Caches gemäß der Einstellung für die geplante Cache Aktualisierung für das DataSet ermöglicht. Geben Sie 0 (null) an, um alle Aktualisierungen des Hintergrund Caches abzuraten.

  
 **CollationName**  
 Eine Zeichenfolge, die die Serversortierung identifiziert. Weitere Informationen finden Sie unter [Sprachen und Sortierungen &#40;Analysis Services&#41;](../../analysis-services/languages-and-collations-analysis-services.md).  
  
 **CommitTimeout**  
 Eine Ganzzahleigenschaft, die angibt, wie lange der Server wartet (in Millisekunden), um eine Schreibsperre für den Commit einer Transaktion abzurufen. Eine Wartezeit ist oftmals erforderlich, da der Server darauf warten muss, dass andere Sperren freigegeben werden, bevor eine Schreibsperre verwendet werden kann, die einen Commit für die Transaktion ausführt.  
  
 Der Standardwert für diese Eigenschaft ist 0 (null), d. h., der Server wartet unbegrenzt. Weitere Informationen zu sperrenbezogenen Eigenschaften finden Sie im [SQL Server 2008 R2 Analysis Services Operations Guide](http://go.microsoft.com/fwlink/?LinkID=225539)(SQL Server 2008 R2 Analysis Services-Vorgangshandbuch).  
  
 **CoordinatorBuildMaxThreads**  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die maximale Anzahl von Threads zum Erstellen von Partitionsindizes definiert. Durch Erhöhen dieses Werts kann die Partitionsindizierung auf Kosten der Speicherauslastung beschleunigt werden. Weitere Informationen zu dieser Eigenschaft finden Sie im [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
 **CoordinatorCancelCount**  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die definiert, wie häufig der Server überprüfen soll, ob ein Cancel-Ereignis aufgetreten ist (basierend auf der Anzahl interner Iterationen). Verringern Sie diese Zahl, um häufiger, jedoch zu Lasten der allgemeinen Leistung, eine Überprüfung auf Cancel-Ereignisse durchzuführen. Diese Eigenschaft wird im tabellarischen Server Modus ignoriert.  
  
 **CoordinatorExecutionMode**  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die maximale Anzahl von parallelen Servervorgängen definiert, einschließlich von Verarbeitungs- und Abfragevorgängen. Null (0) bedeutet, dass der Server basierend auf einem internen Algorithmus selbst entscheidet. Eine positive Zahl zeigt die maximale Anzahl von Vorgängen insgesamt an. Eine negative Zahl (mit umgekehrtem Vorzeichen) zeigt die maximale Anzahl von Vorgängen pro Prozessor an.  

 Der Standardwert für diese Eigenschaft ist -4. Dies bedeutet, der Server ist auf 4 parallele Vorgänge pro Prozessor eingeschränkt. Weitere Informationen zu dieser Eigenschaft finden Sie im [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
 **CoordinatorQueryMaxThreads**  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die maximale Anzahl von Threads pro Partitionssegment während der Abfrageauflösung definiert. Je kleiner die Anzahl von gleichzeitigen Benutzern ist, umso höher kann dieser Wert sein, jedoch auf Kosten des Arbeitsspeichers. Umgekehrt muss bei einer großen Anzahl von gleichzeitigen Benutzern der Wert möglicherweise reduziert werden.  
  
 **CoordinatorShutdownMode**  
 Eine boolesche Eigenschaft, die den Modus zum Herunterfahren des Koordinators definiert. Hierbei handelt es sich um eine erweiterte Eigenschaft, die nicht ohne die Unterstützung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **DataDir**  
 Eine Zeichenfolge, die den Namen des Verzeichnisses zum Speichern von Daten identifiziert.  
  
 **DeploymentMode**  
 Bestimmt den operativen Kontext einer Analysis Services-Serverinstanz. Diese Eigenschaft wird in Dialogfeldern, Meldungen und Dokumentation als "Server Modus" bezeichnet. Diese Eigenschaft wird basierend auf dem Servermodus, den Sie beim Installieren von Analysis Services ausgewählt haben, von SQL Server-Setup konfiguriert. Diese Eigenschaft sollte nur intern berücksichtigt und immer der vom Setup angegebene Wert verwendet werden.  
  
 Für diese Eigenschaften gibt es u. a. folgende gültige Werte:  
  
|Wert|Description|  
|-----------|-----------------|  
|0|Dies ist der Standardwert. Der mehrdimensionale Modus wird angegeben. Er dient zur Verwaltung von mehrdimensionalen Datenbanken, die MOLAP, HOLAP und ROLAP-Speicher sowie Data Mining-Modelle verwenden.|  
|1|Gibt Analysis Services-Instanzen an, die als Teil einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Bereitstellung installiert waren. Ändern Sie die Bereitstellungsmoduseigenschaft der Analysis Services-Instanz nicht, die Teil einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für SharePoint-Installation ist. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Daten nicht mehr auf dem Server ausgeführt.|  
|2|Gibt den Tabellenmodus an, der zum Hosten von Tabellenmodelldatenbanken dient, die Speicher im Arbeitsspeicher oder DirectQuery-Speicher verwenden.|  
  
 Die Modi schließen sich gegenseitig aus. Ein Server, der für den Tabellenmodus konfiguriert ist, kann keine Analysis Services-Datenbanken ausführen, die Cubes und Dimensionen enthalten. Bei Unterstützung durch die zugrunde liegende Computerhardware können Sie mehrere Instanzen von Analysis Services auf demselben Computer installieren und jede Instanz für einen anderen Bereitstellungsmodus konfigurieren. Beachten Sie, dass Analysis Services eine ressourcenintensive Anwendung ist. Die Bereitstellung mehrerer Instanzen auf demselben System wird nur für High-End-Server empfohlen.  
  
 **EnableFast1033Locale**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **ExternalCommandTimeout**  
 Eine Ganzzahleigenschaft, die den Timeoutwert (in Sekunden) für Befehle definiert, die an externe Server ausgegeben werden, einschließlich relationaler Datenquellen und externer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server.  
  
 Der Standardwert für diese Eigenschaft ist 3.600 (Sekunden).  
  
 **ExternalConnectionTimeout**  
 Eine Ganzzahleigenschaft, die den Timeoutwert (in Sekunden) für das Erstellen von Verbindungen mit externen Servern definiert, einschließlich relationaler Datenquellen und externer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server. Diese Eigenschaft wird ignoriert, wenn ein Verbindungstimeout für die Verbindungszeichenfolge angegeben wird.  
  
 Der Standardwert für diese Eigenschaft ist 60 Sekunden.  
  
 **ForceCommitTimeout**  
 Eine Ganzzahleigenschaft, die angibt, wie lange (Dauer in Millisekunden) ein Schreib-Commit-Vorgang warten soll, bevor andere Befehle abgebrochen werden, die dem aktuellen Befehl vorausgingen, einschließlich momentan ausgeführter Abfragen. Dadurch kann die Commit-Transaktion fortgesetzt werden, da Vorgänge mit niedrigerer Priorität, z. B. Abfragen, abgebrochen werden.  
  
 Der Standardwert für diese Eigenschaft ist 30 Sekunden (30.000 Millisekunden), d. h., dass für andere Befehle erst dann ein Timeout erzwungen wird, wenn die Commit-Transaktion 30 Sekunden lang gewartet hat.  
  
> [!NOTE]  
>  Abfragen und Prozesse, die von diesem Ereignis abgebrochen wurden, geben die folgende Fehlermeldung aus: „`Server: The operation has been cancelled`“.  
  
 Weitere Informationen zu dieser Eigenschaft finden Sie im [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
> [!IMPORTANT]  
>  **ForceCommitTimeout** gilt für Cubeverarbeitungsbefehle und Rückschreibevorgänge.  
  
 **IdleConnectionTimeout**  
 Eine Ganzzahleigenschaft, die ein Timeout für inaktive Verbindungen angibt (in Sekunden).  
  
 Der Standardwert für diese Eigenschaft ist Null (0), d. h. bei Verbindungen im Leerlauf erfolgt kein Timeout.  
  
 **IdleOrphanSessionTimeout**  
 Eine Ganzzahleigenschaft, die definiert, wie lange verwaiste Sitzungen im Arbeitsspeicher des Servers beibehalten werden (Dauer in Sekunden). Eine verwaiste Sitzung ist eine Sitzung, die keine zugeordnete Verbindung besitzt. Der Standardwert ist 120 Sekunden.  
  
 **InstanceVisible**  
 Eine boolesche Eigenschaft, die angibt, ob die Serverinstanz sichtbar ist, um Instanzanforderungen des SQL Server-Browserdiensts zu ermitteln. Der Standardwert ist True. Wenn Sie False festlegen, ist die Instanz für den SQL Server-Browser nicht sichtbar.  
  
 **Sprache**  
 Eine Zeichenfolge, die die Sprache definiert, auch für Fehlermeldungen und Zahlenformatierung. Diese Eigenschaft überschreibt die CollationName-Eigenschaft.  
  
 Der Standardwert für diese Eigenschaft ist leer. Dies bedeutet, dass die Sprache durch die CollationName-Eigenschaft definiert wird.  
  
 **LogDir**  
 Eine Zeichenfolge, die den Namen des Verzeichnisses identifiziert, das die Serverprotokolle enthält. Diese Eigenschaft gilt nur, wenn für die Protokollierung Dateien auf dem Datenträger anstelle von Datenbanktabellen (das Standardverhalten) verwendet werden.  
  
 **MaxIdleSessionTimeout**  
 Eine Ganzzahleigenschaft, die den maximalen Timeoutwert für Verbindungen im Leerlauf in Sekunden definiert. Der Standard ist 0 (null) und gibt an, dass für Sitzungen niemals ein Timeout erfolgt. Allerdings werden Sitzungen im Leerlauf weiterhin entfernt, wenn der Server Ressourceneinschränkungen unterliegt.  
  
 **MinIdleSessionTimeout**  
 Eine Ganzzahleigenschaft, die den minimalen Timeoutwert für Verbindungen im Leerlauf in Sekunden definiert. Der Standardwert ist 2.700 Sekunden. Nach Ablauf dieser Zeit kann der Server die Sitzung im Leerlauf beenden, sofern der belegte Arbeitsspeicher benötigt wird.  
  
 **Port**  
 Eine Ganzzahleigenschaft, die die Portnummer definiert, an der der Server auf Clientverbindungen lauscht. Wird diese Eigenschaft nicht festgelegt, sucht der Server dynamisch nach dem ersten freien Port.  
  
 Der Standardwert für diese Eigenschaft ist Null (0), d. h. es wird standardmäßig Port 2383 verwendet. Weitere Informationen zur Portkonfiguration finden Sie unter [Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
 **ServerTimeout**  
 Eine Ganzzahl, die das Timeout für Abfragen definiert (in Sekunden). Der Standardwert beträgt 3600 Sekunden (oder 60 Minuten). Null (0) gibt an, dass für Abfragen kein Timeout erzwungen wird.  
  
 **TempDir**  
 Eine Zeichenfolgeneigenschaft, die den Ort zum Speichern von temporären Dateien angibt, die während Verarbeitung, Wiederherstellung und anderer Vorgänge verwendet werden. Der Standardwert für diese Eigenschaft wird von Setup bestimmt. Wenn nichts angegeben wird, wird standardmäßig das Verzeichnis Data verwendet.  
  
## <a name="requestprioritization-category"></a>RequestPrioritization-Kategorie  
 **Enabled**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **StatisticsStoreSize**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="see-also"></a>Siehe auch  
 [Servereigenschaften in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
