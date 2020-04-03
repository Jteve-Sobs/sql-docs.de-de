---
title: Anzeigen einer Berichtsvorschau im Berichts-Generator | Microsoft-Dokumentation
description: Wenn Sie einen paginierten Bericht in den Reporting Services erstellen, können Sie eine Vorschau des Berichts anzeigen, um zu überprüfen, ob der Bericht das anzeigt, was Sie möchten.
ms.date: 01/09/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c5af8a22b4cba1fd7d2ad43629b379e351b207b3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "80342752"
---
# <a name="previewing-reports-in-report-builder"></a>Anzeigen einer Berichtsvorschau in Berichts-Generator
  Während Sie einen paginierten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bericht erstellen, sollten Sie ihn häufig in der Vorschau anzuzeigen, um zu überprüfen, ob die gewünschten Daten angezeigt werden. Klicken Sie auf **Ausführen**, um den Bericht in der Vorschau anzuzeigen. Der Bericht wird im Seitenansichtsmodus gerendert.  
  
 In Berichts-Generator wurde die Benutzerfreundlichkeit der Vorschau verbessert, indem Bearbeitungssitzungen verwendet werden, wenn eine Verbindung mit einem Berichtsserver hergestellt ist. Die Bearbeitungssitzung erstellt einen Datencache und stellt die Datasets im Cache für wiederholte Berichtsvorschauvorgänge zur Verfügung. Eine Bearbeitungssitzung ist keine Funktion, mit der Sie direkt interagieren. Sie sollten jedoch verstehen, wann das zwischengespeicherte Dataset aktualisiert wird, um die Leistung zu verbessern, wenn Sie einen Bericht in der Vorschau anzeigen, und um zu verstehen, warum der Bericht schneller oder langsamer gerendert wird.  
  
 Andere Vorteile von Bearbeitungssitzungen sind die Möglichkeit, Berichte zu bearbeiten, in denen eingebettete Datenquellen oder Verweiselemente wie z. B. Bilder oder Unterberichte verwendet werden, die auf dem Berichtsserver gespeichert sind.  
  
> [!NOTE]  
> Zwischen der Vorschau im Berichts-Generator und der Anzeige in einem Browser bestehen einige Unterschiede. Ein Kalendersteuerelement, das zu einem Bericht hinzugefügt wird, wenn Sie einen Datum/Uhrzeit-Typparameter angeben, unterschiedet sich im Berichts-Generator und in einem Browser. 
  
## <a name="improving-preview-performance"></a>Verbessern der Vorschauleistung  
 Wie Sie einen Bericht erstellen und aktualisieren, hat Auswirkungen darauf, wie schnell der Bericht in der Vorschau gerendert wird. Wenn Sie einen Bericht, der auf einem Serververweis basiert, zum ersten Mal in der Vorschau anzeigen, wird eine Bearbeitungssitzung erstellt, und die bei der Ausführung des Berichts verwendeten Daten werden einem auf dem Berichtsserver gespeicherten Datencache hinzugefügt. Wenn Sie Änderungen am Bericht vornehmen, die sich nicht auf die Daten auswirken, wird für den Bericht die zwischengespeicherte Kopie der Daten verwendet. Dies bedeutet, dass nicht jedes Mal, wenn Sie den Bericht in der Vorschau anzeigen, geänderte Daten angezeigt werden. Wenn Sie neue Daten anzeigen möchten, klicken Sie im Menüband auf die Schaltfläche **Aktualisieren** .  
  
 Die folgenden Aktionen bewirken, dass der Cache aktualisiert wird, und verlangsamen das Rendern des Berichts beim nächsten Anzeigen in der Vorschau:  
  
-   Hinzufügen, Ändern oder Löschen eines Datasets. Das zwischengespeicherte Dataset enthält alle vom Bericht verwendeten Datasets. Wenn ein Dataset geändert wird, wird das zwischengespeicherte Dataset ungültig. Dies schließt das Ändern des Namens, der Abfrage oder der Felder im Dataset ein.  
  
    > [!NOTE]  
    >  Wenn das Dataset viele Felder enthält, die Sie nicht verwenden möchten, sollten Sie das Dataset möglicherweise aktualisieren, um diese Felder wegzulassen. Obwohl dies eine neue Bearbeitungssitzung erstellt und die erste Vorschau des Bericht langsamer erzeugt wird, ist das kleinere zwischengespeichertes Dataset für die Leistung des Berichtsservers insgesamt nützlich.  
  
-   Hinzufügen, Ändern oder Löschen einer Datenquelle. Dies schließt das Ändern des Namens oder der Eigenschaften der Datenquelle, der Datenerweiterung der Datenquelle sowie der Eigenschaften der Verbindung mit der Datenquelle ein.  
  
-   Ändern der vom Bericht verwendeten freigegebenen Datenquelle zu einer anderen Datenquelle.  
  
-   Ändern der Sprache des Berichts.  
  
-   Ändern der Assemblys oder des benutzerdefinierten Codes, den der Bericht verwendet.  
  
-   Hinzufügen, Ändern oder Löschen der Abfrageparameter im Bericht oder der Parameterwerte.  
  
 Änderungen am Berichtslayout und an der Datenformatierung wirken sich nicht auf das zwischengespeicherte Dataset aus. Sie können die folgenden Aktionen ausführen, ohne dass das zwischengespeicherte Dataset aktualisiert wird:  
  
-   Hinzufügen oder Entfernen von Datenbereichen, wie z. B. von Tabellen, Matrizen oder Diagrammen.  
  
-   Hinzufügen oder Löschen von Spalten im Bericht. Alle Felder im Dataset stehen zur Verwendung im Bericht zur Verfügung. Das Hinzufügen oder Entfernen von Feldern im Bericht hat keine Auswirkungen auf das Dataset.  
  
-   Ändern der Reihenfolge der Felder in Tabellen und Matrizen.  
  
-   Hinzufügen, Ändern oder Löschen von Zeilen- und Spaltengruppen.  
  
-   Hinzufügen, Ändern oder Löschen der Formatierung von Datenwerten in Feldern.  
  
-   Hinzufügen, Ändern oder Löschen von Bildern, Linien oder Textfeldern.  
  
-   Ändern von Seitenumbrüchen.  
  
 Die Bearbeitungssitzung wird erstellt, wenn Sie einen Bericht zum ersten Mal in der Vorschau anzeigen. Standardmäßig dauert eine Bearbeitungssitzung 7200 Sekunden (2 Stunden). Die Sitzung wird bei jeder Ausführung des Berichts auf zwei Stunden zurückgesetzt. Bei Ablauf der Bearbeitungssitzung wird der Datencache gelöscht. Wenn die Bearbeitungssitzung abläuft, wird beim nächsten Anzeigen des Berichts in der Vorschau automatisch eine neue erstellt. Die Ablaufzeit für Bearbeitungssitzungen ist konfigurierbar. Wenn Sie feststellen, dass zwei Stunden zu lang oder zu kurz sind, wenden Sie sich an den Administrator des Berichtsservers.  
  
 Standardmäßig kann der Datencache bis zu fünf Datasets enthalten. Wenn Sie viele unterschiedliche Kombinationen von Parameterwerten verwenden, werden für den Bericht möglicherweise mehr Daten benötigt. In diesem Fall muss der Cache aktualisiert werden, und der Bericht wird beim nächsten Anzeigen in der Vorschau langsamer gerendert. Der Administrator des Berichtsservers kann die Anzahl der Einträge im Cache konfigurieren.  
  
## <a name="concurrency-of-report-updates"></a>Parallelität von Berichtsupdates  
 Häufig zeigen Sie einen Bericht in der Vorschau an, während Sie ihn aktualisieren und dann auf einem Berichtsserver speichern. Es ist möglich, dass eine andere Person gleichzeitig mit Ihnen den Bericht aktualisiert und dann speichert. Der zuletzt gespeicherte Bericht ist die Berichtsversion, die zukünftig zum Anzeigen und Aktualisieren verfügbar ist. Die in der Vorschau angezeigte Version des Berichts ist folglich u. U. nicht die Version, die Sie erneut öffnen. Sie können den Bericht mit der Option **Speichern unter** im Menü "Berichts-Generator" mit einem neuen Namen speichern.  
  
## <a name="external-report-items"></a>Externe Berichtselemente  
 Ihr Bericht enthält möglicherweise Elemente wie z. B. freigegebene Datenquellen, externe Images und Unterberichte, die getrennt vom Bericht gespeichert werden. Da die Elemente getrennt gespeichert werden, ist es möglich, dass sie an eine andere Position auf dem Berichtsserver verschoben werden oder gelöscht werden. In diesem Fall kann der Bericht möglicherweise nicht in der Vorschau angezeigt werden. Sie können den Bericht aktualisieren, um den aktualisierten Speicherort des Elements anzugeben. Wenn das Element gelöscht wurde, können Sie es durch ein vorhandenes Element ersetzen oder den Verweis auf das Element aus dem Bericht entfernen.  
  
 Wenn ein vom Bericht verwendeter Unterbericht nach der Erstellung der Bearbeitungssitzung geändert wird, wird der Bericht nicht in der Vorschau gerendert. Um den Bericht erfolgreich in der Vorschau anzuzeigen, müssen Sie den Bericht speichern oder auf **Aktualisieren** klicken, um neue Daten abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Berichtsdatasets &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Formatieren von Berichtselementen (Berichts-Generator und SSRS)](../../reporting-services/report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Speichern von Berichten &#40;Berichts-Generator&#41;](../../reporting-services/report-builder/saving-reports-report-builder.md)  
  
  
