---
title: Übersicht über Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], about extensions
ms.assetid: 1d652605-9313-4c75-98b4-ba4dcbbb222d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad425c954526fabd6b9b1cf83b42fe5667979c3a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63165421"
---
# <a name="data-processing-extensions-overview"></a>Übersicht über Datenverarbeitungserweiterungen
  Mithilfe von Datenverarbeitungserweiterungen in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] können Sie eine Verbindung zu einer Datenquelle herstellen und Daten abrufen. Sie dienen außerdem als Verbindung zwischen einer Datenquelle und einem Dataset. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterungen sind einer Teilmenge der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Datenanbieterschnittstellen nachgebildet.  
  
 In folgender Tabelle finden Sie eine Liste der Datenverarbeitungserweiterungen, die in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enthalten sind.  
  
|Datenverarbeitungserweiterung|Description|  
|-------------------------------|-----------------|  
|Datenverarbeitungserweiterung für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Verwendet den .NET Framework-Datenanbieter für SQL Server, um eine Verbindung zu [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] herzustellen und Daten daraus abzurufen|  
|Datenverarbeitungserweiterung für OLE DB|Verwendet den .NET Framework-Datenanbieter für OLE DB. Mit dieser Erweiterung kann der Berichtsserver jede Datenquelle abfragen, die über einen OLE DB-Anbieter verfügt.|  
|Datenverarbeitungserweiterung für Oracle|Verwendet den .NET Framework-Datenanbieter für Oracle. Mit dieser Erweiterung kann der Berichtsserver über die Oracle-Clientkonnektivitätssoftware auf Oracle-Datenquellen zugreifen.|  
|Datenverarbeitungserweiterung für ODBC|Verwendet den .NET Framework-Datenanbieter für ODBC. Mit dieser Erweiterung kann der Berichtsserver auf Daten in jeder Datenbank zugreifen, für die ein ODBC-Treiber vorhanden ist.|  
  
 Sie können die [!INCLUDE[ssRS](../../../includes/ssrs.md)]-Datenverarbeitungs-API verwenden, um benutzerdefinierte Datenverarbeitungen zu Ihrem Berichtsserver hinzuzufügen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verfügt über integrierte Unterstützung von Datenanbietern in [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Wenn Sie bereits einen kompletten Datenanbieter implementiert haben, müssen Sie die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung nicht implementieren. Sie sollten jedoch überlegen, ob Sie Ihren Datenanbieter erweitern, sodass er spezifische Funktionen für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 2005 enthält, z. B. sichere Verbindungsanmeldeinformationen und serverseitige Aggregate.  
  
 Jede in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enthaltene Datenverarbeitungserweiterung verwendet eine Reihe gemeinsamer Schnittstellen. Damit wird sichergestellt, dass jede Erweiterung vergleichbare Funktionen implementiert.  
  
 Sie können Datenverarbeitungserweiterungen für Ihre eigenen Datenquellen entwickeln, oder Sie können die Schnittstellen verwenden, um den allgemeinen Datenbankinfrastrukturen eine weitere Datenverarbeitungsebene hinzuzufügen. Sie können Ihre benutzerdefinierten Datenverarbeitungserweiterungen so bereitstellen, dass sie eine nahtlose Integration der Daten in die bestehenden Berichtsserver in Ihrer Organisation ermöglichen. Sie können Sie auch als Teil einer benutzerdefinierten Berichtssuite verwenden, die Sie Ihren Consumern anbieten.  
  
 ![Architektur von Datenverarbeitungserweiterungen](../../media/bk-dataprocess-extensions.gif "Data processing extension architecture")  
Architektur für Berichtsserver-Datenverarbeitungserweiterungen  
  
 Die Implementierung einer benutzerdefinierten [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung hat folgende Vorteile:  
  
-   Eine vereinfachte Datenzugriffsarchitektur, häufig mit besserer Verwaltbarkeit und verbesserter Leistung.  
  
-   Die Fähigkeit, erweiterungsspezifische Funktionen direkt für die Consumer verfügbar zu machen.  
  
-   Eine spezifische Schnittstelle für die Consumer, um auf die Datenquelle in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] zuzugreifen.  
  
## <a name="data-extension-process-flow"></a>Verarbeitungsablauf für Datenerweiterungen  
 Bevor Sie Ihre benutzerdefinierte Datenerweiterung bereitstellen, sollten Sie wissen, wie der Berichtsserver Datenerweiterungen zur Verarbeitung von Daten verwendet. Sie sollten auch die Konstruktoren und Verfahren kennen, die vom Berichtsserver aufgerufen werden.  
  
 ![Prozessfluss in Datenverarbeitungserweiterungen](../../media/bk-ext-01.gif "Process flow for data processing extension")  
Der schrittweise Verarbeitungsablauf einer Datenerweiterung, die vom Berichtsserver aufgerufen wird  
  
 Die Abbildung stellt die folgende Abfolge von Ereignissen dar:  
  
1.  Der Berichtsserver erstellt ein Verbindungsobjekt und übergibt die Verbindungszeichenfolge und die zum Bericht gehörigen Anmeldeinformationen.  
  
2.  Der Befehlstext des Berichts wird verwendet, um ein Befehlsobjekt zu erstellen. Im Prozess kann die Datenverarbeitungserweiterung Code enthalten, der den Befehlstext analysiert und alle Parameter für den Befehl erstellt.  
  
3.  Sobald das Befehlsobjekt und die Parameter verarbeitet sind, wird ein Datenleser generiert, der ein Resultset zurückgibt und den Berichtsserver in die Lage versetzt, die Berichtsdaten mit dem Berichtslayout zu verknüpfen.  
  
## <a name="developer-requirements"></a>Anforderungen für die Entwickler  
 Für die Entwicklung einer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung benötigen Sie Folgendes:  
  
-   Einen Bereitstellungscomputer, auf dem Berichts-Designer oder ein Berichtsserver installiert ist.  
  
-   Einen Entwicklungscomputer, auf dem [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] oder höher bzw. das [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK (Software Development Kit) installiert ist  
  
-   Sehr gute Kenntnisse der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Funktionen und -Möglichkeiten.  
  
-   Sehr gute Kenntnisse der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]-Architektur, der [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Datenanbieter, ADO.NET Dataset-Objekte und der allgemeinen [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]-Schnittstellen  
  
-   Entwicklungserfahrung in einer [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Sprache, z.B. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# oder [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
