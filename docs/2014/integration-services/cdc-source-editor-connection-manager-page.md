---
title: Quellen-Editor für CDC (Seite Verbindungs-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.connection.f1
ms.assetid: 304e6717-e160-4a7b-a06f-32182449fef8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d0e421d6ba1aaf69c04a450d8d93ff1ddf385935
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58391488"
---
# <a name="cdc-source-editor-connection-manager-page"></a>Quellen-Editor für CDC (Seite Verbindungs-Manager)
  Auf der Seite **Verbindungs-Manager** des Dialogfelds **Quellen-Editor für CDC** können Sie den ADO.NET-Verbindungs-Manager für die [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Datenbank auswählen, aus der die CDC-Quelle Änderungszeilen liest (CDC-Datenbank). Nachdem Sie die CDC-Datenbank ausgewählt haben, müssen Sie eine aufgezeichnete Tabelle in der Datenbank auswählen.  
  
 Weitere Informationen zur CDC-Quelle finden Sie unter [CDC Source](data-flow/cdc-source.md).  
  
## <a name="task-list"></a>Aufgabenliste  
 **So öffnen Sie die Seite "Verbindungs-Manager" des Quellen-Editors für CDC**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]das [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] -Paket, das die CDC-Quelle enthält.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf die CDC-Quelle.  
  
3.  Klicken Sie im **Quellen-Editor für CDC**auf **Verbindungs-Manager**.  
  
## <a name="options"></a>Optionen  
 **ADO.NET-Verbindungs-Manager**  
 Wählen Sie in der Liste einen vorhandenen Verbindungs-Manager aus, oder klicken Sie auf **Neu** , um eine neue Verbindung zu erstellen. Die Verbindung muss zu einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank hergestellt werden, die für CDC aktiviert ist und in der sich die ausgewählte Änderungstabelle befindet.  
  
 **Neu**  
 Klicken Sie auf **Neu**. Das Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** , in dem Sie einen neuen Verbindungs-Manager erstellen können, wird geöffnet.  
  
 **CDC Table**  
 Wählen Sie die CDC-Quelltabelle mit den aufgezeichneten Änderungen aus, die Sie lesen und zur Verarbeitung an Downstream-SSIS-Komponenten senden möchten.  
  
 **Capture instance**  
 Wählen Sie den Namen der CDC-Aufzeichnungsinstanz mit der zu lesenden CDC-Tabelle aus, oder geben Sie ihn ein.  
  
 Eine aufgezeichnete Quelltabelle kann über eine oder zwei aufgezeichnete Instanzen zum Behandeln des nahtlosen Übergangs der Tabellendefinition mithilfe von Schemaänderungen verfügen. Wenn mehr als eine Aufzeichnungsinstanz für die aufzuzeichnende Quelltabelle definiert wird, müssen Sie hier die gewünschte Aufzeichnungsinstanz auswählen. Der Standardname einer Aufzeichnungsinstanz für eine Tabelle [Schema].[Tabelle] lautet \<Schema>_\<Tabelle>. Die tatsächlich verwendeten Namen der Aufzeichnungsinstanzen können jedoch abweichen. Die tatsächliche Tabelle, aus der gelesen wird, ist die CDC-Tabelle **cdc.\<Aufzeichnungsinstanz>_CT**.  
  
 **CDC Processing Mode**  
 Wählen Sie den Verarbeitungsmodus aus, der sich für die Behandlung Ihrer Verarbeitungsanforderungen am besten eignet. Folgende Optionen sind möglich:  
  
-   **alle**: Gibt die Änderungen zurück in den aktuellen CDC-Bereich, ohne die **vor Update** Werte.  
  
-   **Alle mit den alten Werten**: Gibt die Änderungen im aktuellen CDC-Verarbeitungsbereich Einbeziehung der alten Werte (**vor Update**). Für jeden Updatevorgang gibt es zwei Zeilen, eine mit den Werten vor dem Update und eine mit den Werten nach dem Update.  
  
-   **NET**: Gibt nur eine Änderungszeile pro Quellzeile, die im aktuellen CDC-Verarbeitungsbereich geändert. Wenn eine Quellzeile mehrmals aktualisiert wurde, wird die kombinierte Änderung erzeugt (Beispiel: Einfügen+Update wird als einzelner Updatevorgang und Update+Löschen als einzelner Löschvorgang erzeugt). Beim Arbeiten im Änderungsverarbeitungsmodus Net ist es möglich, die Änderungen auf Lösch-, Einfüge- und Updatevorgänge aufzuteilen und parallel zu behandeln, da die einzelne Quellzeile in mehr als einer Ausgabe vorhanden ist.  
  
-   **NET mit updatemaske**: Dieser Modus ähnelt dem normalen Net-Modus, jedoch werden außerdem boolesche Spalten mit dem Namensmuster hinzugefügt **__ $\<Spaltenname >\__Changed** , die auf geänderte Spalten in der aktuellen Änderungszeile.  
  
-   **NET mit Merge**: Dieser Modus ähnelt dem normalen Net-Modus aber Hierbei sind Einfüge-und Updatevorgänge zu einem einzelnen Mergevorgang (UPSERT) zusammengeführt.  
  
> [!NOTE]  
>  Für alle Nettoänderungsoptionen muss die Quelltabelle über einen Primärschlüssel oder einen eindeutigen Index verfügen. Für Tabellen ohne Primärschlüssel oder eindeutigen Index muss die Option **All** verwendet werden.  
  
 **Variable, die den CDC-Status enthält**  
 Wählen Sie die SSIS-Zeichenfolgenpaketvariable aus, in der der CDC-Status für den aktuellen CDC-Kontext verwaltet wird. Weitere Informationen zur CDC-Statusvariablen finden Sie unter [Definieren einer Statusvariablen](data-flow/define-a-state-variable.md).  
  
 **Include reprocessing indicator column**  
 Aktivieren Sie dieses Kontrollkästchen, um eine spezielle Ausgabespalte mit dem Namen **__$reprocessing**zu erstellen.  
  
 Diese Spalte verfügt über den Wert **TRUE** , wenn sich der CDC-Verarbeitungsbereich mit dem ursprünglichen Verarbeitungsbereich überschneidet (der LSN-Bereich, der dem Zeitraum des erstmaligen Ladens entspricht) oder wenn ein CDC-Verarbeitungsbereich nach einem Fehler bei einer vorherigen Ausführung erneut verarbeitet wird. In dieser Indikatorspalte können SSIS-Entwickler Fehler unterschiedlich behandeln, wenn sie Änderungen erneut verarbeiten (z. B. können Aktionen, wie das Löschen einer nicht vorhandenen Zeile und ein fehlgeschlagener Einfügevorgang aufgrund eines doppelten Schlüssels, ignoriert werden).  
  
 Weitere Informationen finden Sie unter [CDC Source Custom Properties](data-flow/cdc-source-custom-properties.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Quellen-Editor für CDC &#40;Seite „Spalten“&#41;](../../2014/integration-services/cdc-source-editor-columns-page.md)   
 [Quellen-Editor für CDC &#40;Seite „Fehlerausgabe“&#41;](../../2014/integration-services/cdc-source-editor-error-output-page.md)  
  
  
