---
title: Dialogfeld des SSIS-Protokolle konfigurieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configuredtslogs.loggingdetails.f1
- sql12.dts.designer.configuredtslogs.providersandlogs.f1
- sql12.dts.designer.configuredtslogs.containers.f1
helpviewer_keywords:
- Configure SSIS Logs dialog box
ms.assetid: 4b980275-cd9a-4943-8c36-727d51f9a484
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dbba1b7712bcbdccc821e419b3101065c3164913
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834566"
---
# <a name="configure-ssis-logs-dialog-box"></a>SSIS-Protokolle konfigurieren (Dialogfeld)
  Verwenden Sie das Dialogfeld **SSIS-Protokolle konfigurieren** , um Protokollierungsoptionen für ein Paket zu definieren.  
  
 **Was möchten Sie tun?**  
  
1.  [Öffnen Sie das Dialogfeld "SSIS-Protokolle konfigurieren".](#open_dialog)  
  
2.  [Konfigurieren Sie die Optionen im Bereich "Container".](#container)  
  
3.  [Konfigurieren Sie die Optionen auf der Registerkarte "Anbieter und Protokolle".](#provider)  
  
4.  [Konfigurieren Sie die Optionen auf der Registerkarte "Details".](#detail)  
  
##  <a name="open_dialog"></a> Öffnen Sie das Dialogfeld "SSIS-Protokolle konfigurieren".  
 **So öffnen Sie das Dialogfeld "SSIS-Protokolle konfigurieren"**  
  
-   Klicken Sie in [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer auf **Protokollierung** im **SSIS** -Menü.  
  
##  <a name="container"></a> Konfigurieren Sie die Optionen im Bereich "Container".  
 Mithilfe des **Container** -Bereichs des Dialogfelds **SSIS-Protokolle konfigurieren** können Sie das Paket und seine Container für das Protokollieren aktivieren.  
  
### <a name="options"></a>Optionen  
 **Container**  
 Aktivieren Sie die Kontrollkästchen in der hierarchischen Sicht, um das Paket und seine Container für die Protokollierung zu aktivieren:  
  
-   Falls diese Option deaktiviert ist, ist der Container nicht für die Protokollierung aktiviert. Wählen Sie diese Option aus, um die Protokollierung zu aktivieren.  
  
-   Falls die Option abgeblendet ist, verwendet der Container die Protokollierungsoptionen des ihm übergeordneten Containers. Diese Option steht für das Paket nicht zur Verfügung.  
  
-   Wenn diese Option aktiviert ist, definiert der Container seine eigenen Protokollierungsoptionen.  
  
 Falls ein Container abgeblendet ist und Sie Protokollierungsoptionen für den Container festlegen möchten, klicken Sie zweimal auf das entsprechende Kontrollkästchen. Durch das erste Klicken wird das Kontrollkästchen deaktiviert, durch das zweite Klicken wird es ausgewählt, und Sie können somit die zu verwendenden Protokollanbieter und die zu protokollierenden Informationen auswählen.  
  
##  <a name="provider"></a> Konfigurieren Sie die Optionen auf der Registerkarte "Anbieter und Protokolle".  
 Verwenden Sie die Registerkarte **Anbieter und Protokolle** des Dialogfelds **SSIS-Protokolle konfigurieren** , um Protokolle für das Aufzeichnen von Laufzeitereignissen zu erstellen und zu konfigurieren.  
  
### <a name="options"></a>Optionen  
 **Anbietertyp**  
 Wählen Sie einen Protokollanbietertyp aus der Liste aus.  
  
 **Hinzufügen**  
 Fügen Sie der Auflistung der Protokollanbieter des Pakets ein Protokoll des angegebenen Typs hinzu.  
  
 **Name**  
 Aktivieren oder deaktivieren Sie Protokolle für Container und Tasks, die Sie im Bereich **Container** des Dialogfelds **SSIS-Protokolle konfigurieren** auswählen, indem Sie die Kontrollkästchen aktivieren bzw. deaktivieren. Das Feld Name kann bearbeitet werden. Verwenden Sie den Standardnamen für den Anbieter, oder geben Sie einen eindeutigen, beschreibenden Namen ein.  
  
 **Beschreibung**  
 Das Feld Beschreibung kann bearbeitet werden. Klicken Sie in das Feld und ändern Sie die Standardbeschreibung des Protokolls.  
  
 **Configuration**  
 Wählen Sie einen vorhandenen Verbindungs-Manager aus der Liste aus, oder klicken Sie auf \<**Neue Verbindung...**>, um einen neuen Verbindungs-Manager zu erstellen. Abhängig vom Typ des Protokollanbieters können Sie einen OLE DB-Verbindungs-Manager oder einen Dateiverbindungs-Manager konfigurieren. Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows-Ereignisprotokollanbieter erfordert keine Verbindung.  
  
 Verwandte Themen: [OLE DB-Verbindungs-Manager](connection-manager/ole-db-connection-manager.md), [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md)  
  
 **Löschen**  
 Wählen Sie einen Protokollanbieter aus, und klicken Sie auf **Löschen**.  
  
##  <a name="detail"></a> Konfigurieren Sie die Optionen auf der Registerkarte "Details".  
 Auf der Registerkarte **Details** des Dialogfelds **SSIS-Protokolle konfigurieren** können Sie die Ereignisse für das Protokollieren sowie die zu protokollierenden Informationsdetails aktivieren. Die Informationen, die Sie auswählen, gelten für alle Protokollanbieter im Paket. Sie können z. B. nicht einige Informationen in die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz und andere Informationen in eine Textdatei schreiben.  
  
### <a name="options"></a>Optionen  
 **Ereignisse**  
 Aktivieren oder Deaktivieren von Ereignissen für die Protokollierung.  
  
 **Beschreibung**  
 Anzeigen einer Beschreibung des Ereignisses.  
  
 **Erweitert**  
 Auswählen oder Löschen zu protokollierender Ereignisse und Auswählen oder Löschen von Informationen, die für jedes Ereignis protokolliert werden sollen. Klicken Sie auf **Standard** , um alle Protokollierungsdetails mit Ausnahme der Liste der Ereignisse auszublenden. Die folgenden Informationen sind für die Protokollierung verfügbar:  
  
|Wert|Description|  
|-----------|-----------------|  
|**Computer**|Der Name des Computers, auf dem das protokollierte Ereignis aufgetreten ist.|  
|**Operator**|Der Benutzername der Person, die das Paket gestartet hat.|  
|**SourceName**|Der Name des Pakets, Containers oder Tasks, in dem das protokollierte Ereignis aufgetreten ist.|  
|**SourceID**|GUID (Global Unique Identifier) des Pakets, Containers oder Tasks, in dem das protokollierte Ereignis aufgetreten ist.|  
|**ExecutionID**|Der global eindeutige Bezeichner der Paketausführungsinstanz.|  
|**MessageText**|Eine dem Protokolleintrag zugeordnete Meldung.|  
|**DataBytes**|Zur künftigen Verwendung reserviert.|  
  
 **Grundlegend**  
 Wählen Sie zu protokollierende Ereignisse aus, oder löschen Sie diese. Diese Option blendet alle Protokollierungsdetails mit Ausnahme der Liste der Ereignisse aus. Wenn Sie ein Ereignis auswählen, werden standardmäßig alle Protokollierungsdetails für das Ereignis ausgewählt. Klicken Sie auf **Erweitert** , um alle Protokollierungsdetails anzuzeigen.  
  
 **Load**  
 Geben Sie eine vorhandene XML-Datei an, die als Vorlage zum Festlegen der Protokollierungsoptionen verwendet werden soll.  
  
 **Speichern**  
 Speichern Sie Konfigurationsdetails als Vorlage in einer XML-Datei.  
  
  
