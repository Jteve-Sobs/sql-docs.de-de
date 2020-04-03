---
title: Exportieren als CSV-Datei (Berichts-Generator) | Microsoft-Dokumentation
description: Im Berichts-Generator rendert die CSV-Renderingerweiterung paginierte Berichte in das Format Nur-Text, das von vielen Anwendungen gelesen werden kann und mit ihnen kompatibel ist.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: 68ec746e-8c82-47f5-8c3d-dbe403a441e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1104054faef55ca3b3b661ea210c279c9aa55841
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "80342880"
---
# <a name="exporting-to-a-csv-file-report-builder-and-ssrs"></a>Exportieren als CSV-Datei (Berichts-Generator und SSRS)
  Die durch Trennzeichen getrennte CSV-Renderingerweiterung (Comma-Separated Value) rendert paginierte Berichte als vereinfachte Darstellung der Daten eines Berichts in einem standardisierten Nur-Text-Format, das leicht lesbar und mit anderen Anwendungen austauschbar ist.  
  
 Dabei werden Felder und Zeilen durch ein Trennzeichen getrennt, für das auch ein anderes Zeichen als ein Komma gewählt werden kann. Die erstellte Datei kann in einem Tabellenkalkulationsprogramm wie [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] geöffnet oder als Importformat für andere Programme verwendet werden. Der exportierte Bericht wird zu einer CSV-Datei und gibt den MIME-Typ **Text/CSV**zurück.  
  
 Wenn Sie in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]mit Daten für Diagramme, Datenbalken, Sparklines, Messgeräte oder Indikatoren arbeiten möchten, exportieren Sie den Bericht in eine CSV-Datei, und öffnen Sie diese anschließend in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.  
  
 Weitere Informationen zum Exportieren ins CSV-Format finden Sie unter [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="csv-rendering"></a><a name="CSVRendering"></a> CSV-Rendering  
 Ein CSV-Bericht, der mit den Standardeinstellungen gerendert wurde, besitzt folgende Merkmale:  
  
-   Das standardmäßige Feldtrennzeichen ist ein Komma (,).  
  
    > [!NOTE]  
    >  Sie können das Feldtrennzeichen in ein beliebiges Zeichen (einschließlich TAB) ändern, indem Sie die Geräteinformationseinstellungen ändern. Weitere Informationen finden Sie unter [CSV Device Information Settings](../../reporting-services/csv-device-information-settings.md).  
  
-   Die Datensatztrennzeichen-Zeichenfolge ist der Wagenrücklauf und der Zeilenvorschub (\<cr>\<lf>).  
  
-   Als Textqualifizierer-Zeichenfolge dient das Anführungszeichen (").  
  
     Der CSV-Renderer fügt keine Qualifizierer um alle Textzeichenfolgen hinzu. Textqualifizierer werden nur hinzugefügt, wenn der Wert das Trennzeichen oder einen Zeilenumbruch enthält.  
  
-   Falls der Text eine eingebettete Trennzeichenfolge oder Qualifiziererzeichenfolge enthält, wird der Text in den Textqualifizierer eingeschlossen, und die eingebetteten Qualifiziererzeichenfolgen werden verdoppelt.  
  
-   Formatierung und Layout werden ignoriert.  
  
 Die folgenden Elemente werden beim Rendern ignoriert:  
  
-   Seitenkopf  
  
-   Seitenfuß  
  
-   Benutzerdefinierte Berichtselemente  
  
-   Zeile  
  
-   Image  
  
-   Rechteck  
  
-   Automatische Teilergebnisse  
  
 Die verbleibenden Berichtselemente werden von oben nach unten und dann von links nach rechts sortiert. Anschließend wird jedes Element in eine Spalte gerendert. Enthält der Bericht geschachtelte Datenelemente, wie Listen oder Tabellen, werden die übergeordneten Elemente in jedem Datensatz wiederholt.  
  
 In der folgenden Tabelle wird die Darstellung von Berichtselementen beim Rendern angegeben:  
  
|Element|Renderingverhalten|  
|----------|------------------------|  
|Textfeld|Der Inhalt des Textfelds wird gerendert. Im Standardmodus werden Elemente auf Grundlage der Formatierungseigenschaften des Elements formatiert. Im kompatiblen Modus kann die Formatierung durch die Geräteinformationseinstellungen geändert werden. Weitere Informationen zu den CSV-Renderingmodi finden Sie weiter unten.|  
|Tabelle|Das Rendering erfolgt durch Erweitern der Tabelle und Erstellen einer Zeile und Spalte für jede Zeile und Spalte auf der untersten Detailebene. Teilergebniszeilen und -spalten weisen keine Zeilen- und Spaltenüberschriften auf. Drillthroughberichte werden nicht unterstützt.|  
|Matrix|Das Rendering erfolgt durch Erweitern der Matrix und Erstellen einer Zeile und Spalte für jede Zeile und Spalte auf der untersten Detailebene. Teilergebniszeilen und -spalten weisen keine Zeilen- und Spaltenüberschriften auf.|  
|List|Für jede Detailzeile oder Instanz in der Liste wird ein Datensatz gerendert.|  
|Unterbericht|Das übergeordnete Element wird für jede Instanz des Inhalts wiederholt.|  
|Diagramm|Wird gerendert, indem eine Zeile für jeden Diagrammwert und jede Elementbezeichnung erstellt wird. Bezeichnungen aus Reihen und Kategorien in Hierarchien werden vereinfacht und in die Zeile für einen Diagrammwert eingeschlossen.|  
|Datenbalken|Wird wie ein Diagramm gerendert. Ein Datenbalken enthält normalerweise keine Hierarchien oder Bezeichnungen.|  
|Sparkline|Wird wie ein Diagramm gerendert. Eine Sparkline enthält üblicherweise keine Hierarchien oder Bezeichnungen.|  
|Maßstab|Wird als einzelner Datensatz mit dem Minimal- und Maximalwert der linearen Skala, dem Start- und Endwert des Bereichs und dem Wert des Zeigers gerendert.|  
|Indikator|Es wird als einzelnes Element mit dem Namen des aktiven Zustands, den verfügbaren Zuständen und dem Datenwert als Attribute gerendert.|  
|Karte|Rendert eine Zeile mit den Bezeichnungen und Werten der einzelnen Kartenelemente einer Kartenebene.<br /><br /> Wenn die Karte über mehrere Ebenen verfügt, variieren die Werte in den Zeilen abhängig davon, ob die Kartenebenen die gleichen oder unterschiedliche Kartendatenbereiche verwenden. Wenn mehrere Kartenebenen den gleichen Datenbereich verwenden, enthalten die Zeilen Daten aus allen Ebenen.|  
  
### <a name="hierarchical-and-grouped-data"></a>Hierarchische und gruppierte Daten  
 Hierarchische und gruppierte Daten müssen vereinfacht werden, um im CSV-Format dargestellt zu werden.  
  
 Die Renderingerweiterung vereinfacht den Bericht zu einer Baumstruktur, die die geschachtelten Gruppen innerhalb des Datenbereichs darstellt. So vereinfachen Sie den Bericht:  
  
-   Eine Zeilenhierarchie wird vor einer Spaltenhierarchie vereinfacht.  
  
-   Spalten werden wie folgt sortiert: Textfelder im Hauptteil von links nach rechts und von oben nach unten, gefolgt von Datenbereichen von links nach rechts und von oben nach unten.  
  
-   Innerhalb eines Datenbereichs werden die Spalten wie folgt sortiert: Eckelemente, Zeilenhierarchieelemente, Spaltenhierarchieelemente und Zellen  
  
-   Peerdatenbereiche sind Datenbereiche oder dynamische Gruppen, die einen allgemeinen Datenbereich oder einen dynamischen Vorgänger gemeinsam nutzen. Peerdaten werden durch Verzweigen der vereinfachten Struktur identifiziert.  
  
 Weitere Informationen finden Sie unter [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
  
##  <a name="renderer-modes"></a><a name="RenderingModes"></a> Renderermodi  
 Für die CSV-Renderingerweiterung stehen zwei Modi zur Verfügung. Ein Modus ist für Excel, der andere für Anwendungen von Drittanbietern optimiert, die eine strikte CSV-Kompatibilität mit der CSV-Spezifikation in RFC 4180 erfordern. Je nach verwendetem Modus werden Peerdatenbereiche unterschiedlich behandelt.  
  
### <a name="default-mode"></a>Standardmodus  
 Der Standardmodus ist für Excel optimiert. Im Standardmodus wird der Bericht als CSV-Datei mit mehreren Abschnitten gerenderter CSV-Daten gerendert. Jeder Peerdatenbereich wird durch eine leere Zeile begrenzt. Peerdatenbereiche innerhalb des Berichthauptteils werden als separate Datenblocks innerhalb der CSV-Datei gerendert. Das Ergebnis ist eine CSV-Datei mit folgenden Merkmalen:  
  
-   Einzelne Textfelder innerhalb des Berichthauptteils werden einmal als erster Datenblock innerhalb der CSV-Datei gerendert.  
  
-   Jeder Peerdatenbereich der obersten Ebene im Hauptteil des Berichts wird in einem eigenen Datenblock gerendert.  
  
-   Geschachtelte Datenbereiche werden diagonal in den gleichen Datenblock gerendert.  
  
#### <a name="formatting"></a>Formatierung  
 Numerische Werte werden in ihrem formatierten Status gerendert. Excel kann formatierte numerische Werte, wie Währungen, Prozentwerte und Datumsangaben, erkennen und die Zellen beim Importieren einer CSV-Datei entsprechend formatieren.  
  
### <a name="compliant-mode"></a>Kompatibler Modus  
 Der kompatible Modus ist für Anwendungen von Drittanbietern optimiert.  
  
#### <a name="data-regions"></a>Datenbereiche  
 Nur die erste Textzeile in der Datei enthält die Spaltenkopfzeilen, und jede Zeile verfügt über dieselbe Spaltenanzahl.  
  
#### <a name="formatting"></a>Formatierung  
 Die Werte sind unformatiert.  
  
##  <a name="interactivity"></a><a name="Interactivity"></a> Interaktivität  
 Interaktivität wird von keinem der durch diesen Renderer generierten CSV-Formate unterstützt. Die folgenden interaktiven Elemente werden nicht gerendert:  
  
-   Links  
  
-   Anzeigen oder ausblenden  
  
-   Dokumentstruktur  
  
-   Drillthrough oder Links mit Durchklicken  
  
-   Endbenutzersortierung  
  
-   Feste Berichtsköpfe  
  
-   Lesezeichen  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a> Geräteinformationseinstellungen  
 Sie kännen einige Standardeinstellungen für diesen Renderer ändern, beispielsweise den Modus für das Rendern, die Zeichen, die als Trennzeichen verwendet werden können, und die Zeichen, die als Textqualifizierer für die Standardzeichenfolge verwendet werden können. Ändern Sie dazu die Geräteinformationseinstellungen. Weitere Informationen finden Sie unter [CSV Device Information Settings](../../reporting-services/csv-device-information-settings.md).  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paginierung in Reporting Services &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Renderingverhalten (Berichts-Generator und SSRS)](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Interaktive Funktionalität für verschiedene Berichtsrenderingerweiterungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [Rendern von Berichtselementen (Berichts-Generator und SSRS)](../../reporting-services/report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
