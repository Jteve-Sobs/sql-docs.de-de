---
title: Optionen für die Anforderung für Profil für NULL-Verhältnis der Spalte (Datenprofilerstellungs-Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 04d5c60c925fd97c3b8b823ec42c2e065a3d0596
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52790742"
---
# <a name="column-null-ratio-profile-request-options-data-profiling-task"></a>Optionen für die Anforderung für Profil für NULL-Verhältnis der Spalte (Datenprofilerstellungs-Task)
  Verwenden Sie den Bereich **Anforderungseigenschaften** der Seite **Profilanforderungen** , um die Optionen für das im Anforderungsbereich ausgewählte **Profil für NULL-Verhältnis der Spalte** festzulegen. Ein Profil für das NULL-Verhältnis der Spalte dokumentiert den Prozentsatz der NULL-Werte in der ausgewählten Spalte. Dieses Profil hilft Ihnen, Probleme mit den Daten zu identifizieren, z. B. ein unerwartet hohes Verhältnis an NULL-Werten in einer Spalte. Ein Profil für das NULL-Verhältnis einer Spalte kann beispielsweise ein Profil für eine Spalte für die Postleitzahl erstellen und einen nicht zulässigen hohen Prozentsatz an fehlenden Postleitzahlen erkennen.  
  
> [!NOTE]  
>  Die in diesem Thema beschriebenen Optionen werden auf der Seite **Profilanforderungen** im **Editor für den Datenprofilerstellungs-Task**angezeigt. Weitere Informationen zu dieser Seite des Editors finden Sie unter [Editor für den Datenprofilerstellungs-Task &#40;Seite „Profilanforderungen“&#41;](data-profiling-task-editor-profile-requests-page.md).  
  
 Weitere Informationen zum Verwenden des Datenprofilerstellungs-Tasks finden Sie unter [Einrichten von Datenprofilerstellungs-Tasks](data-profiling-task.md). Weitere Informationen zum Verwenden des Datenprofil-Viewers zum Analysieren der Ausgabe des Datenprofilerstellungs-Tasks finden Sie unter [Datenprofil-Viewer](data-profile-viewer.md).  
  
## <a name="request-properties-options"></a>Optionen für Anforderungseigenschaften  
 Für eine **Anforderung für NULL-Verhältnis der Spalte**zeigt der Bereich **Anforderungseigenschaften** die folgenden Gruppen von Optionen an:  
  
-   **Daten**, die die Optionen **TableOrView** und **Spalte** enthalten  
  
-   **Allgemein**  
  
### <a name="data-options"></a>Datenoptionen  
 **ConnectionManager**  
 Wählen Sie den vorhandenen [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager aus, der den .NET-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) verwendet, um eine Verbindung zur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank herzustellen, die die Tabelle oder Sicht enthält, für die ein Profil erstellt werden soll.  
  
 **TableOrView**  
 Wählen Sie die vorhandene Tabelle oder die Sicht aus, die die Spalte enthält, für die ein Profil erstellt werden soll.  
  
 Weitere Informationen finden Sie im Abschnitt "TableorView-Optionen" in diesem Thema.  
  
 **Column**  
 Wählen Sie die vorhandene Spalte aus, für die ein Profil erstellt werden soll. Wählen Sie **(\*)** aus, um ein Profil für alle Spalten zu erstellen.  
  
 Weitere Informationen finden Sie im Abschnitt "Spaltenoptionen" in diesem Thema.  
  
#### <a name="tableorview-options"></a>TableOrView-Optionen  
 **Schema**  
 Gibt das Schema an, zu dem die ausgewählte Tabelle gehört. Diese Option ist schreibgeschützt.  
  
 **Tabelle**  
 Zeigt den Namen der ausgewählten Tabelle an. Diese Option ist schreibgeschützt.  
  
#### <a name="column-options"></a>Spaltenoptionen  
 **IsWildCard**  
 Gibt an, ob der Platzhalter **(\*)** ausgewählt wurde. Diese Option wird auf **TRUE** festgelegt, wenn Sie **(\*)** ausgewählt haben, um ein Profil für alle Spalten zu erstellen. Die Option wird auf **False** festgelegt, wenn Sie eine einzelne Spalte ausgewählt haben, für die ein Profil erstellt werden soll. Diese Option ist schreibgeschützt.  
  
 **ColumnName**  
 Zeigt den Namen der ausgewählten Spalte an. Diese Option ist leer, wenn Sie **(\*)** ausgewählt haben, um ein Profil für alle Spalten zu erstellen. Diese Option ist schreibgeschützt.  
  
 **StringCompareOptions**  
 Diese Option gilt nicht für das Profil für NULL-Verhältnis für Spalten.  
  
### <a name="general-options"></a>Allgemeine Optionen  
 **RequestID**  
 Geben Sie einen beschreibenden Namen ein, um diese Profilanforderung zu kennzeichnen. In der Regel müssen Sie den automatisch generierten Wert nicht ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Editor für den Datenprofilerstellungs-Task &#40;Seite "Allgemein"&#41;](../general-page-of-integration-services-designers-options.md)   
 [Schnellprofilformular für eine einzelne Tabelle &#40;Datenprofilerstellungs-Task&#41;](single-table-quick-profile-form-data-profiling-task.md)  
  
  
