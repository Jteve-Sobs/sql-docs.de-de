---
title: Vergleichen von Optionen zum Speichern von Blobs (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c90dd764a04b3eb470f0cf76d29e2ee2002d6b97
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877217"
---
# <a name="compare-options-for-storing-blobs-sql-server"></a>Vergleichen von Optionen zum Speichern von Blobs (SQL Server)
  Erläutert und vergleicht die Optionen, die zum Speichern von Dateien und Dokumenten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar sind.  
  
##  <a name="Expectations"></a> Speichern von Dateien in der Datenbank: Vorteile und Erwartungen  
 Ein großer Prozentsatz der Unternehmensdaten ist unstrukturiert und wird in der Regel als Dateien und Dokumente in Dateisystemen gespeichert. Der Großteil dieser Daten wird von Anwendungen generiert, verwaltet und benötigt, die über Windows-APIs auf die Dateien zugreifen. Unternehmen speichern diese Daten in der Regel im Dateisystem, wohingegen die verwandten Metadaten für die Dateien in einer relationalen Datenbank gespeichert werden.  
  
 Die Integration unstrukturierter Daten in die relationale Datenbank bietet bedeutende Vorteile. Dazu gehören folgende Vorteile:  
  
-   Integrierte Speicher- und Datenverwaltungsfunktionen, z. B. Sicherungen.  
  
-   Integrierte Dienste, z. B. Volltextsuche und semantische Suche über Daten und Metadaten.  
  
-   Einfache Administration und Richtlinienverwaltung der unstrukturierten Daten.  
  
 Es war weitestgehend jedoch nicht zweckdienlich, solch unstrukturierte Daten in einer relationalen Datenbank zu speichern. Es war zuvor nicht möglich, vorhandene, auf Windows basierende Anwendungen auf relationalen Systemen auszuführen. Das erneute Schreiben etablierter Anwendungen (z. B. Microsoft Word oder Adobe Reader) zur Ausführung auf relationalen Datenbank-APIs ist nicht praktisch. Bei diesen Anwendungen wird einfach erwartet, dass über Windows-APIs auf die Daten zugegriffen werden kann. Anders ausgedrückt umfassen die Erwartungen Folgendes:  
  
-   Für Windows-Anwendungen sind keine Datenbanktransaktionen erforderlich, und diese werden nicht berücksichtigt.  
  
-   Windows-Anwendungen erfordern für Datei- und Verzeichnisdaten Kompatibilität mit Dateisystem-APIs.  
  
##  <a name="Filestream"></a> FILESTREAM  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt bereits über die FILESTREAM-Funktion, die ein effizientes Speichern, Verwalten und Streamen unstrukturierter Daten ermöglicht, die als Dateien im Dateisystem gespeichert sind. Bei einer FILESTREAM-Lösung ist jedoch die benutzerdefinierte Programmierung erforderlich. Sie wird der oben beschriebenen Anforderung im Hinblick auf vollständige Windows-Anwendungskompatibilität nicht gerecht.  
  
##  <a name="FileTables"></a> FileTables  
 Die FileTable-Funktion beruht auf vorhandenen FILESTREAM-Funktionen, über die Unternehmenskunden, unstrukturierte Dateidaten und Verzeichnishierarchien in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank speichern können, indem die Anforderungen für nicht transaktionalen Zugriff und Windows-Anwendungskompatibilität für dateibasierte Daten erfüllt werden.  
  
##  <a name="CompareFileTable"></a> Vergleichen von FILESTREAM und FileTable  
  
|Funktion|Dateiserver und Datenbanklösung|FILESTREAM-Lösung|FileTable-Lösung|  
|-------------|---------------------------------------|-------------------------|------------------------|  
|**Einzelne Story für Verwaltungstasks**|Nein|Ja|**ja**|  
|**Einzelner Satz von Diensten**: Suche, Berichterstellung, Abfrage usw.|Nein|Ja|**ja**|  
|**Integriertes Sicherheitsmodell**|Nein|Ja|**Ja**|  
|**Direkte Updates der FILESTREAM-Daten**|Ja|Nein|**ja**|  
|**In der Datenbank beibehaltene Datei- und Verzeichnishierarchie**|Nein|Nein|**ja**|  
|**Windows-Anwendungskompatibilität**|Ja|Nein|**Ja**|  
|**Relationaler Zugriff auf Dateiattribute**|Nein|Nein|**ja**|  
  
##  <a name="CompareRBS"></a> Vergleichen von FILESTREAM und Remote BLOB-Speicher (RBS)  
 Einen Vergleich dieser beiden Features finden Sie in diesem Blogbeitrag vom RBS-Team: [SQL Server Remote BLOB Store "und" FILESTREAM-Funktion – Vergleich](https://go.microsoft.com/fwlink/?LinkId=210317).  
  
##  <a name="more"></a> Weitere Informationen  
 [FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md)  
 [FileTables &#40;SQL Server&#41;](filetables-sql-server.md)  
 [Remoteblobspeicher &#40;RBS&#41; &#40;SQL Server&#41;](remote-blob-store-rbs-sql-server.md)  
  
