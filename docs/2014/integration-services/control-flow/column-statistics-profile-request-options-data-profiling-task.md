---
title: Optionen für die Anforderung für Spaltenstatistikprofil (Datenprofilerstellungs-Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 87205984-507a-49f3-b27c-36a0075c234d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 046e1c9d97cf7f508fa69e67bfe7369e7186e137
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52768462"
---
# <a name="column-statistics-profile-request-options-data-profiling-task"></a>Optionen für die Anforderung für Spaltenstatistikprofil (Datenprofilerstellungs-Task)
  Verwenden Sie den Bereich **Anforderungseigenschaften** der Seite **Profilanforderungen** , um die Optionen für die im Anforderungsbereich ausgewählte **Anforderung für Spaltenstatistikprofil** festzulegen. Ein Spaltenstatistikprofil meldet Statistiken, wie minimale, maximale, durchschnittliche und standardmäßige Abweichung für numerische Spalten und den Mindest- und Höchstwert für `datetime`-Spalten. Dieses Profil hilft Ihnen, Probleme mit den Daten zu identifizieren, z. B. ungültige Datumsangaben. Beispiel: Sie erstellen ein Profil einer Spalte mit historischen Daten und entdecken einen Maximalwert, der in der Zukunft liegt.  
  
> [!NOTE]  
>  Die in diesem Thema beschriebenen Optionen werden auf der Seite **Profilanforderungen** im **Editor für den Datenprofilerstellungs-Task**angezeigt. Weitere Informationen zu dieser Seite des Editors finden Sie unter [Editor für den Datenprofilerstellungs-Task &#40;Seite „Profilanforderungen“&#41;](data-profiling-task-editor-profile-requests-page.md).  
  
 Weitere Informationen zum Verwenden des Datenprofilerstellungs-Tasks finden Sie unter [Einrichten von Datenprofilerstellungs-Tasks](data-profiling-task.md). Weitere Informationen zum Verwenden des Datenprofil-Viewers zum Analysieren der Ausgabe des Datenprofilerstellungs-Tasks finden Sie unter [Datenprofil-Viewer](data-profile-viewer.md).  
  
## <a name="request-properties-options"></a>Optionen für Anforderungseigenschaften  
 Für eine **Anforderung für Spaltenstatistikprofil**zeigt der Bereich **Anforderungseigenschaften** die folgenden Gruppen von Optionen an:  
  
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
 Diese Option gilt nicht für das Spaltenstatistikprofil.  
  
### <a name="general-options"></a>Allgemeine Optionen  
 **RequestID**  
 Geben Sie einen beschreibenden Namen ein, um diese Profilanforderung zu kennzeichnen. In der Regel müssen Sie den automatisch generierten Wert nicht ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Editor für den Datenprofilerstellungs-Task &#40;Seite "Allgemein"&#41;](../general-page-of-integration-services-designers-options.md)   
 [Schnellprofilformular für eine einzelne Tabelle &#40;Datenprofilerstellungs-Task&#41;](single-table-quick-profile-form-data-profiling-task.md)  
  
  
