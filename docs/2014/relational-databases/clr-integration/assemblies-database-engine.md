---
title: Assemblys (Database Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4830a677125cb03e2c53ed78065d94d5265d4a83
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62920783"
---
# <a name="assemblies-database-engine"></a>Assemblys (Database Engine)
  Die Themen in diesem Abschnitt enthalten Informationen, damit Sie Assemblys verstehen, entwerfen und implementieren können.  
  
 Assemblys sind DLL-Dateien, die in einer Instanz von verwendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zum Bereitstellen von Funktionen, gespeicherte Prozeduren, Trigger, benutzerdefinierte Aggregate und benutzerdefinierte Typen, die in einer der von gehosteten verwalteten Codesprachen geschrieben wurden die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gemeinsame Sprachlaufzeit (CLR), statt in [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 Eine Assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist ein Objekt, das auf ein verwaltetes Anwendungsmodul (DLL-Datei) verweist, das in der [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-CLR erstellt wurde. Eine Assembly enthält Klassenmetadaten und verwalteten Code. Das Hochladen einer Assembly in eine Instanz von SQL Server ist der erste Schritt beim Erstellen eines der folgenden Datenbankobjekte:  
  
-   CLR-Funktionen. Weitere Informationen finden Sie unter [erstellen CLR-Funktionen](../user-defined-functions/create-clr-functions.md).  
  
-   CLR-gespeicherte Prozeduren. Weitere Informationen finden Sie unter [CLR-gespeicherte Prozeduren](../../database-engine/dev-guide/clr-stored-procedures.md).  
  
-   CLR-Trigger. Weitere Informationen finden Sie unter [Erstellen von CLR-Triggern](../triggers/create-clr-triggers.md).  
  
-   Benutzerdefinierte Aggregatfunktionen. Weitere Informationen finden Sie unter [erstellen benutzerdefinierte Aggregate](../user-defined-functions/create-user-defined-aggregates.md).  
  
-   Benutzerdefinierte Typen. Weitere Informationen finden Sie unter [Verwenden von benutzerdefinierten Typen](../native-client/features/using-user-defined-types.md).  
  
 Assemblys besitzen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die folgenden Funktionen:  
  
-   Aufnehmen des verwalteten Codes, der die Funktionen eines oder mehrerer der CLR-Datenbankobjekte ausführt, die oben aufgelistet wurden.  
  
-   Aufnehmen von Metadaten, die z. B. die Versionsnummer und Kultur der Assembly, einen optionalen öffentlichen Schlüssel zum eindeutigen Identifizieren der Liste der Klassen der Assembly, die in der Assembly definierten Methoden und die Prozessorarchitektur der Assembly umfassen.  
  
-   Verwalten des Grades, bis zu dem verwalteter Code auf externe Ressourcen zugreifen kann, durch Steuern der Codezugriffsberechtigungen.  
  
-   Aufnehmen von Metadaten zu Abhängigkeiten von anderen Assemblys, auf die durch die Assembly verwiesen wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Entwerfen von Assemblys](assemblies-designing.md)|Erläutert, was vor dem Erstellen einer Assembly berücksichtigt werden muss. Dazu zählen das Verpacken von Assemblys, Codezugriffsberechtigungen und andere Einschränkungen.|  
|[Implementieren von Assemblys](assemblies-implementing.md)|Beschreibt das Erstellen und Löschen von Assemblys, wie und wann Assemblys geändert werden und wie Metadaten zu Assemblys abgerufen werden.|  
|[Abrufen von Informationen zu Assemblys](assemblies-getting-information.md)|Stellt eine Liste der Katalogsichten und Funktionen zur Verfügung, die für Metadaten zu Assemblys abgefragt werden können.|  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierkonzepte für die Integration der Common Language Runtime &#40;CLR&#41;](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
