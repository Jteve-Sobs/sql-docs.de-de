---
title: Programmgesteuerte Verwaltung von Paketen und Ordnern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a6ede05e340cbd2822cd72ceee514f6ce31a2755
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62766852"
---
# <a name="managing-packages-and-folders-programmatically"></a>Programmgesteuerte Verwaltung von Paketen und Ordnern
  Beim programmgesteuerten Arbeiten mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen möchten Sie möglicherweise feststellen, ob ein einzelnes Paket oder ein einzelner Ordner vorhanden ist, oder Sie möchten die Ordner mit gespeicherten Paketen verwalten. Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt eine Reihe von Methoden bereit, die diese Anforderungen erfüllen.  
  
##  <a name="exists"></a> Bestimmen, ob ein Paket oder ein Ordner vorhanden ist  
 Um programmgesteuert zu ermitteln, ob ein gespeichertes Paket vorhanden ist, rufen Sie eine der folgenden Methoden auf, bevor Sie versuchen, das Paket zu laden und auszuführen:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|  
  
 Um programmgesteuert zu ermitteln, ob ein Ordner vorhanden ist, rufen Sie eine der folgenden Methoden auf, bevor Sie versuchen, die in dem Ordner gespeicherten Pakete aufzulisten:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|  
  

  
##  <a name="managing"></a> Verwalten von Paketen und Ordnern  
 Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt zusätzliche Methoden zum Verwalten von Paketen und den Ordnern, in denen diese gespeichert sind, bereit.  
  
###  <a name="managing_rempkg"></a> Entfernen eines Pakets  
 Rufen Sie zum programmgesteuerten Entfernen eines gespeicherten Pakets eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="managing_create"></a> Erstellen eines Ordners  
 Rufen Sie zum programmgesteuerten Erstellen eines Speicherordners eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="managing_remfldr"></a> Entfernen eines Ordners  
 Rufen Sie zum programmgesteuerten Entfernen eines Speicherordners eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="managing_rename"></a> Umbenennen eines Ordners  
 Rufen Sie zum programmgesteuerten Umbenennen eines Speicherordners eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Paketverwaltung &#40;SSIS-Dienst&#41;](../service/package-management-ssis-service.md)   
 [Programmgesteuertes Auflisten verfügbarer Pakete](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
