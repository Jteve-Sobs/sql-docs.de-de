---
title: Konfigurieren von Berichterstellungseigenschaften für Power View-Berichte | Microsoft-Dokumentation
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3ee35ac833a1170a688bb9439ed4dd8f6b6d6716
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403372"
---
# <a name="supplemental-lesson---configure-reporting-properties-for-power-view-reports"></a>Ergänzende Lektion: Konfigurieren von Berichterstellungseigenschaften für Power View-Berichte
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser ergänzenden Lektion legen Sie berichterstellungseigenschaften für das AW Internet Sales-Projekt. Berichterstellungseigenschaften erleichtern Benutzern das auswählen und Anzeigen von Modelldaten in Power View. Zusätzlich legen Sie Eigenschaften fest, um bestimmte Spalten und Tabellen auszublenden und neue Daten zur Verwendung in Diagrammen zu erstellen.   
  
Geschätzte Zeit zum Abschließen dieser Lektion: **30 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Diese ergänzende Lektion ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser ergänzenden Lektion alle vorherigen Lektionen abgeschlossen haben.  
Zum Ausführen dieser ergänzenden Lektion benötigen Sie zusätzlich Folgendes:  
  
-   Das AW Internet Sales-Projekt (dieses Tutorial abgeschlossen) möchten Sie die bereitgestellt oder bereits mit einem Analysis Services-Server bereitgestellt werden.  
  
  
## <a name="model-properties-that-affect-reporting"></a>Modelleigenschaften, die sich auf die Berichterstellung auswirken  
Bei der Erstellung eines tabellarischen Modells sind bestimmte Eigenschaften, die Sie für einzelne Spalten und Tabellen festlegen können, um den Benutzer, der berichterstellungsumgebung in Power View zu verbessern. Darüber hinaus können Sie zusätzliche Modelldaten erstellen, um die Datenvisualisierung und weitere Funktionen zu unterstützen, die für den Berichterstellungsclient spezifisch sind. Im Folgenden sind einige Änderungen aufgeführt, die Sie am Beispiel Adventure Works Internet Sales Model vornehmen:  
  
-   **Hinzufügen von neuen Daten** -Hinzufügen von neuen Daten in einer berechneten Spalte mithilfe einer DAX-Formel werden Datumsinformationen in einem Format, das zum Anzeigen in Diagrammen einfacher wird erstellt.  
  
-   **Tabellen und Spalten ausblenden, die für den Endbenutzer nicht von Nutzen sind** – Die Eigenschaft **Ausgeblendet** steuert, ob Tabellen und Tabellenspalten im Berichterstellungsclient angezeigt werden. Elemente mit dieser Eigenschaft werden zwar ausgeblendet, bleiben jedoch Teil des Modells und sind weiterhin für Abfragen und Berechnungen verfügbar.  
  
-   **Aktivieren Sie ein-Klick Tabellen** -standardmäßig keine Aktion ausgeführt wird, wenn ein Benutzer eine Tabelle in der Feldliste klickt. Um dieses Verhalten zu ändern, legen Sie für jede Spalte, die Sie in die Tabelle aufnehmen möchten, einen Standardfeldsatz fest, damit die Tabelle dem Bericht hinzugefügt wird, wenn darauf geklickt wird. Diese Eigenschaft wird für die Tabellenspalten festgelegt, die Endbenutzer am wahrscheinlichsten verwenden möchten.  
  
-   **Gruppierungen festlegen, falls erforderlich** – Die Eigenschaft **Eindeutige Zeilen beibehalten** bestimmt, ob die Werte in der Spalte nach Werten in einem anderen Feld gruppiert werden sollen, z.B. einem Bezeichnerfeld. Für Spalten, die doppelte Werte z. B. mit Kundenname (z. B. mehrere Kunden mit dem Namen John Smith) enthalten, es ist wichtig, die Gruppe "" (eindeutige Zeilen beibehalten) auf die **Zeilenbezeichner** Feld, damit Ihre Endbenutzer Bereitstellen der korrekte Ergebnisse.  
  
-   **Datentypen und Datenformate festlegen** – Power View wendet standardmäßig Regeln auf Grundlage des Spaltendatentyps an, um zu bestimmen, ob das Feld als Measure verwendet werden kann. Da jede datenvisualisierung in Power View über Regeln verfügt, in dem Measures und nicht-Measures platziert werden können, ist es wichtig, den Datentyp im Modell festzulegen oder zu überschreiben die Standardeinstellung, um das Verhalten zu erzielen, das Sie für Ihre Benutzer verwenden möchten.  
  
-   **Legen Sie nach Spalte sortieren** -Eigenschaft: die **nach Sortierspalte** Eigenschaft gibt an, ob die Werte in der Spalte nach Werten in einem anderen Feld sortiert werden sollen. Beispiel: In der Spalte Month Calendar, die den Monatsnamen enthält, soll eine Sortierung nach der Spalte Month Number ausgeführt werden.  
  
## <a name="hide-tables-from-client-tools"></a>Ausblenden von Tabellen aus Clienttools  
Da bereits eine berechnete Spalte Product Category und eine berechnete Spalte Product Subcategory in der Tabelle Product vorhanden sind, ist es nicht notwendig, dass die Tabellen Product Category und Product Subcategory für Clientanwendungen sichtbar sind.  
  
#### <a name="to-hide-the-product-category-and-product-subcategory-tables"></a>So blenden Sie die Tabellen "Product Category" und "Product Subcategory" aus  
  
1.  Klicken Sie im Modell-Designer mit der rechten Maustaste auf die Tabelle (Registerkarte) **Product Category** , und klicken Sie anschließend auf **Aus Clienttools ausblenden**.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Tabelle (Registerkarte) **Product Subcategory** , und klicken Sie anschließend auf **Aus Clienttools ausblenden**.  
  
## <a name="create-new-data-for-charts"></a>Erstellen neuer Daten für Diagramme  
Es kann zeitweise erforderlich sein, mithilfe von DAX-Formeln neue Daten im Modell zu erstellen. In dieser Aufgabe fügen Sie der Tabelle Date zwei neue berechnete Spalten hinzu. Diese neuen Spalten enthalten Datumsfelder in einem für Diagramme geeigneten Format.  
  
#### <a name="to-create-new-data-for-charts"></a>So erstellen Sie neue Daten für Diagramme  
  
1.  Führen Sie in der Tabelle **Date** einen Bildlauf zum rechten Rand der Tabelle durch, und klicken Sie anschließend auf **Spalte hinzufügen**.  
  
2.  Fügen Sie mithilfe der folgenden Formeln in der Bearbeitungsleiste zwei neue berechnete Spalten hinzu:  
  
    |Spaltenname|Formel|  
    |---------------|-----------|  
    |Year Quarter|=[Calendar Year] & " Q" & [Calendar Quarter]|  
    |Year Month|=[Calendar Year] & FORMAT([Month],"#00")|  
  
## <a name="default-field-set"></a>Standardfeldsatz  
Der Standardfeldsatz ist eine vordefinierte Liste von Spalten und Measures für eine Tabelle, die auf einem Zeichenbereich des Berichts automatisch hinzugefügt werden, wenn die Tabelle in der berichtsfeldliste geklickt wird. Im Wesentlichen können Sie die standardmäßigen Spalten und Measures sowie die Feldreihenfolge angeben, die Benutzer erwarten würden, wenn diese Tabelle in Power View-Berichten visuell dargestellt wird.  Für das Modell Internet Sales definieren Sie einen Standardfeldsatz und eine Standardreihenfolge für die Tabellen Customer, Geography und Product. Es werden nur die am häufigsten verwendeten Spalten aufgenommen, die Benutzer zum Analysieren der Daten in Adventure Works Internet Sales mithilfe von Power View-Berichten benötigen.  
  
Ausführliche Informationen zum Standardfeldsatz finden Sie unter [konfigurieren Standardfeldsatzes für Power View-Berichte](../tabular-models/power-view-configure-default-field-set-for-reports.md).  
  
#### <a name="to-set-default-field-set-for-tables"></a>So legen Sie den Standardfeldsatz für Tabellen fest  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Customer** .  
  
2.  Klicken Sie im **Eigenschaftenfenster** unter **Berichterstellungseigenschaften**in der Eigenschaft **Standardfeldsatz** auf **Zum Bearbeiten klicken** , um das Dialogfeld **Standardfeldsatz** zu öffnen.  
  
3.  Drücken Sie im Dialogfeld **Standardfeldsatz** im Listenfeld **Felder in der Tabelle** STRG, wählen Sie die folgenden Felder aus, und klicken Sie anschließend auf **Hinzufügen**.  
  
    **Geburtsdatum**, **Customer Alternate ID**, **Vorname**, **Nachname**.  
  
4.  Verwenden Sie im Fenster **Standardfelder in Reihenfolge** die Schaltflächen Nach oben und Nach unten, um die folgende Reihenfolge festzulegen:  
  
    **Customer Alternate ID**  
  
    **First Name**  
  
    **Last Name**  
  
    **Birth Date**  
  
5.  Klicken Sie auf **OK** , um das Dialogfeld **Standardfeldsatz** für die Tabelle **Customer** zu schließen.  
  
6.  Führen Sie die gleichen Schritte für die Tabelle **Geography** aus, wobei Sie die folgenden Felder auswählen und die angegebene Reihenfolge beachten.  
  
    **City**, **State Province Code**, **Country Region Code**.  
  
7.  Führen Sie zuletzt die gleichen Schritte für die Tabelle **Product** aus, wobei Sie die folgenden Felder auswählen und die angegebene Reihenfolge beachten.  
  
    **Product Alternate ID**, **Produktname**.  
  
## <a name="table-behavior"></a>Tabellenverhalten  
Mit den Eigenschaften für das Tabellenverhalten können Sie das Standardverhalten für unterschiedliche Visualisierungstypen und das Gruppierungsverhalten für die in Power View-Berichten verwendeten Tabellen ändern. Auf diese Weise wird eine bessere Standardplatzierung von identifizierenden Informationen, wie Namen, Bildern oder Titeln, in Kachel-, Karten- und Diagrammlayouts erzielt.  
  
Ausführliche Informationen zu tabellenverhaltenseigenschaften finden Sie unter [Konfigurieren von Tabellenverhaltenseigenschaften für Power View-Berichte](../tabular-models/power-view-configure-table-behavior-properties-for-reports.md).  
  
#### <a name="to-set-table-behavior"></a>Tabellenverhalten festlegen 
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Customer** .  
  
2.  Klicken Sie im **Eigenschaftenfenster** in der Eigenschaft **Tabellenverhalten** auf **Zum Bearbeiten klicken**, um das Dialogfeld **Tabellenverhalten** zu öffnen.  
  
3.  In der **Tabellenverhalten** Dialogfeld die **Zeilenbezeichner** im Dropdown-Listenfeld auf der **Kunden-ID** Spalte.  
  
4.  Wählen Sie im Listenfeld **Eindeutige Zeilen beibehalten** **First Name** und **Last Name**aus.  
  
    Durch diese Eigenschafteneinstellung wird angegeben, dass diese Spalten Werte bereitstellen, die selbst dann als eindeutige Werte angesehen werden sollen, wenn sie doppelt vorkommen, z. B. wenn mindestens zwei Mitarbeiter den gleichen Namen aufweisen.  
  
5.  Wählen Sie im Dropdown-Listenfeld **Standardbeschriftung** die Spalte **Last Name** aus.  
  
    Durch diese Eigenschafteneinstellung wird angegeben, dass diese Spalte einen Anzeigenamen zur Darstellung von Zeilendaten bereitstellt.  
  
6.  Wiederholen Sie diese Schritte für die **Geography** Tabelle auswählen der **Geography ID** Spalte als Zeilenbezeichner und die **City** -Spalte in der **eindeutige Zeilen beibehalten**  Listenfeld. Sie müssen keine Standardbeschriftung für diese Tabelle festlegen.  
  
7.  Wiederholen Sie die folgenden Schritte aus, für die **Produkt** Tabelle auswählen der **Produkt-ID** Spalte als Zeilenbezeichner und die **Produktname** -Spalte in der **eindeutig zu halten Zeilen** Listenfeld. Für **Standardbeschriftung**Option **Product Alternate ID**.  
  
## <a name="reporting-properties-for-columns"></a>Berichterstellungseigenschaften für Spalten  
Für Spalten können eine Reihe grundlegender Spalteneigenschaften und bestimmte Berichterstellungseigenschaften festgelegt werden, mit deren Hilfe sich die Berichterstellung anhand von Modellen verbessern lässt. Es ist u. U. nicht erforderlich, dass Benutzer jede Spalte in jeder Tabelle sehen können. Ebenso, wie Sie die Tabellen Product Category und Product Subcategory zuvor, mithilfe der Spalteneigenschaft Hidden-Eigenschaft einer Spalte, können Sie bestimmte Spalten aus einer Tabelle ausblenden, die ansonsten angezeigt wird. Auch andere Eigenschaften, wie Datenformat und Nach Spalte sortieren, können die Darstellung von Spaltendaten in Berichten beeinflussen. Jetzt legen Sie einige Eigenschaften für bestimmten Spalten fest. Für andere Spalten ist keine Aktion erforderlich, daher werden sie unten nicht dargestellt.  
  
Sie legen hier nur einige von zahlreichen Spalteneigenschaften fest. Ausführlichere Informationen zu berichterstellungseigenschaften finden Sie unter [Spalteneigenschaften](../tabular-models/column-properties-ssas-tabular.md).  
  
#### <a name="to-set-properties-for-columns"></a>So legen Sie Eigenschaften für Spalten fest  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Customer** .  
  
2.  Klicken Sie auf die **Kunden-ID** Spalte zum Anzeigen der Spalteneigenschaften in der **Eigenschaften** Fenster.  
  
3.  Legen Sie im **Eigenschaftenfenster** die Eigenschaft **Ausgeblendet** auf True fest. Die **Kunden-ID** Spalte dann wird abgeblendet im Modell-Designer.  
  
4.  Wiederholen Sie diese Schritte, und legen Sie die folgenden Spalten- und Berichterstellungseigenschaften für alle angegebenen Tabellen fest. Verwenden Sie für alle anderen Eigenschaften die Standardeinstellungen.  
  
    Hinweis: Für alle Datumsspalten, stellen Sie sicher, dass **Datentyp** ist **Datum**.  
  
    **Kunde**  
  
    |Spalte|Eigenschaft|Wert|  
    |----------|------------|---------|  
    |Geography ID|Ausgeblendet|Wahr|  
    |Birth Date|Datenformat|Short Date|  
  
    **Datum**  
  
    > [!NOTE]  
    > Da die Date-Tabelle ausgewählt wurde, wie die Tabelle "date" mithilfe der markieren als Datumstabelle festlegen, "in" Lektion 7: Als Datumstabelle markieren, die Datumsspalte in der Tabelle Date als Spalte als eindeutiger Bezeichner, die Zeilen-ID-Eigenschaft für die Date-Spalte verwendet werden automatisch auf "true" festgelegt und kann nicht geändert werden. Bei Verwendung von Zeitintelligenzfunktionen in DAX-Formeln müssen Sie eine Datumstabelle angeben. In diesem Modell haben Sie unter Verwendung von Zeitintelligenzfunktionen eine Reihe von Measures zur Berechnung von Umsatzdaten für verschiedene Zeiträume, z. B. das vorherige und aktuelle Quartal, sowie zur Verwendung in KPIs erstellt. Weitere Informationen zum Angeben einer Datumstabelle finden Sie unter [geben markieren als Datumstabelle für die Verwendung mit Zeitintelligenz](../tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md).  
  
    |Spalte|Eigenschaft|Wert|  
    |----------|------------|---------|  
    |date|Datenformat|Short Date|  
    |Day Number of Week|Ausgeblendet|Wahr|  
    |Day Name|Nach Spalte sortieren|Day Number of Week|  
    |Day of Week|Ausgeblendet|Wahr|  
    |Day of Month|Ausgeblendet|Wahr|  
    |Day of Year|Ausgeblendet|Wahr|  
    |Month Name|Nach Spalte sortieren|Month|  
    |Month|Ausgeblendet|Wahr|  
    |Month Calendar|Ausgeblendet|Wahr|  
    |Fiscal Quarter|Ausgeblendet|Wahr|  
    |Fiscal Year|Ausgeblendet|Wahr|  
    |Fiscal Semester|Ausgeblendet|Wahr|  
  
    **Geography**  
  
    |Spalte|Eigenschaft|Wert|  
    |----------|------------|---------|  
    |Geography ID|Ausgeblendet|Wahr|  
    |Sales Territory ID|Ausgeblendet|Wahr|  
  
    **Product**  
  
    |Spalte|Eigenschaft|Wert|  
    |----------|------------|---------|  
    |Produkt-ID|Ausgeblendet|Wahr|  
    |Product Alternate ID|Standardbeschriftung|Wahr|  
    |Produkt-Unterkategorie-ID|Ausgeblendet|Wahr|  
    |Product Start Date|Datenformat|Short Date|  
    |Product End Date|Datenformat|Short Date|  
  
    **Internet Sales**  
  
    |Spalte|Eigenschaft|Wert|  
    |----------|------------|---------|  
    |Produkt-ID|Ausgeblendet|Wahr|  
    |Kunden-ID|Ausgeblendet|Wahr|  
    |Promotion-ID|Ausgeblendet|Wahr|  
    |Currency-ID|Ausgeblendet|Wahr|  
    |Sales Territory ID|Ausgeblendet|Wahr|  
    |Order Quantity|Datentyp<br /><br />Datenformat<br /><br />Dezimalstellen|Decimal Number<br /><br />Decimal Number<br /><br />0|  
    |Order Date|Datenformat|Short Date|  
    |Due Date|Datenformat|Short Date|  
    |Ship Date|Datenformat|Short Date|  
  
## <a name="redeploy-the-adventure-works-internet-sales-tabular-model"></a>Erneutes Bereitstellen des tabellarischen Modells "Adventure Works Internet Sales"  
Da Sie das Modell geändert haben, müssen Sie es erneut bereitstellen.  
  
#### <a name="to-redeploy-the-adventure-works-internet-sales-tabular-model"></a>So stellen Sie das tabellarische Modell "Adventure Works Internet Sales" erneut bereit  
  
-   Klicken Sie in SSDT auf das **erstellen** , und klicken Sie dann auf **bereitstellen Adventure Works Internet Sales Model**.  
  
    Das Dialogfeld **Bereitstellen** öffnet sich und zeigt den Bereitstellungsstatus der Metadaten sowie jede im Modell enthaltene Tabelle an.  
  
## <a name="next-steps"></a>Nächste Schritte  
Jetzt können Sie Excel verwenden, um Daten aus dem Modell zu visualisieren. Vergewissern Sie sich, dass das Analysis Services-Konto und Reporting Services-Konto auf der SharePoint-Website über Leseberechtigungen für die Analysis Services-Instanz verfügen, in der Sie das Modell bereitgestellt haben.  
  
  
  
  
