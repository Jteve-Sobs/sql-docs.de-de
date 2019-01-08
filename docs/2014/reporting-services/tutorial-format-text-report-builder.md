---
title: 'Lernprogramm: Formatieren von Text (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ff0a14a546a14d37461193b71b4d682deb25925a
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53350107"
---
# <a name="tutorial-format-text-report-builder"></a>Lernprogramm: Formatieren von Text (Berichts-Generator)
  In diesem Tutorial können Sie die Formatierung von Text auf verschiedene Weise üben. Nach dem Einrichten des leeren Berichts mit der Datenquelle und dem Dataset können Sie die Schritte auswählen, mit denen Sie sich vertraut machen möchten.  
  
 Die folgende Abbildung zeigt einen Bericht, der mit dem Bericht vergleichbar ist, den Sie erstellen werden.  
  
 ![Rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "Rs_FormatTextFinal")  
  
 In einem Schritt machen Sie absichtlich einen Fehler, um dadurch erkennen zu können, warum es sich um einen Fehler handelt. Anschließend beheben Sie den Fehler, um den gewünschten Effekt zu erreichen.  
  
 Eine erweiterte Version des Berichts, den Sie in diesem Lernprogramm erstellen, ist als [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Berichts-Generator-Beispielbericht verfügbar. Weitere Informationen zum Herunterladen dieses Beispielberichts und anderer finden Sie unter [Beispielberichte für Berichts-Generator](https://go.microsoft.com/fwlink/?LinkId=184851).  
  
##  <a name="BackToTop"></a> Lernziele  
  
### <a name="set-up-the-report"></a>Einrichten des Berichts  
 1. [Erstellen ein leeres Berichts mit einer Datenquelle und des Datensets](#CreateReport)  
  
 2. [Hinzufügen eines Felds auf der Berichtsentwurfsoberfläche (falsch, dann ordnungsgemäß)](#AddField)  
  
 3. [Hinzufügen einer Tabelle auf der Berichtsentwurfsoberfläche](#AddTable)  
  
### <a name="pick-and-choose"></a>Auswählen  
 [Hinzufügen eines Links zum Bericht](#AddHyperlink)  
  
 [Drehen des Textfelds im Bericht](#RotateText)  
  
 [Anzeigen von Text mit HTML-Formatierung](#FormatHTML)  
  
 [Formatieren von Währung](#FormatCurrency)  
  
 [Speichern des Berichts](#Save)  
  
 Ungefähre Dauer dieses Lernprogramms: 20 Minuten.  
  
## <a name="requirements"></a>Anforderungen  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="CreateReport"></a> Erstellen ein leeres Berichts mit einer Datenquelle und des Datensets  
  
#### <a name="to-create-a-blank-report"></a>So erstellen Sie einen leeren Bericht  
  
1.  Klicken Sie auf **starten**, zeigen Sie auf **Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
    > [!NOTE]  
    >  Das Dialogfeld **Erste Schritte** wird angezeigt. Wenn dies nicht der Fall ist, klicken Sie auf der Schaltfläche des Berichts-Generators auf **Neu**.  
  
2.  Vergewissern Sie sich links im Dialogfeld **Erste Schritte** , dass die Option **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Leerer Bericht**.  
  
#### <a name="to-create-a-data-source"></a>So erstellen Sie eine Datenquelle  
  
1.  Klicken Sie im Berichtsdatenbereich auf **Neu**, und klicken Sie dann auf **Datenquelle**.  
  
2.  In der **Namen** geben: **TextDataSource**  
  
3.  Klicken Sie auf **In Bericht eingebettete Verbindung verwenden**.  
  
4.  Überprüfen Sie, ob der Verbindungstyp Microsoft SQL Server ist, und geben Sie anschließend im Feld **Verbindungszeichenfolge** Folgendes ein: **Datenquelle = \<Servername >**  
  
    > [!NOTE]  
    >  Der Ausdruck \<Servername >, z.B. Report001, bezeichnet einen Computer, auf dem eine Instanz von SQL Server-Datenbankmoduls installiert ist. Für dieses Lernprogramm sind keine bestimmten Daten erforderlich; es wird lediglich eine Verbindung mit einer [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] -Datenbank benötigt. Wenn unter **Datenquellenverbindungen** bereits eine Datenquellenverbindung aufgeführt ist, können Sie sie auswählen und zum nächsten Schritt übergehen, nämlich „So erstellen Sie ein Dataset“. Weitere Informationen finden Sie unter [Alternative Methoden zum Herstellen einer Datenverbindung (Berichts-Generator)](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-create-a-dataset"></a>So erstellen Sie ein Dataset  
  
1.  Klicken Sie im Berichtsdatenbereich auf **Neu**und anschließend auf **Dataset**.  
  
2.  Vergewissern Sie sich, dass die Datenquelle **TextDataSource**ist.  
  
3.  In der **Namen** geben: **TextDataset.**  
  
4.  Überprüfen Sie, ob der Abfragetyp **Text** ausgewählt ist, und klicken Sie anschließend auf **Abfrage-Designer**.  
  
5.  Klicken Sie auf **Als Text bearbeiten**.  
  
6.  Fügen Sie die folgende Abfrage in den Abfragebereich ein:  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  Klicken Sie auf „Ausführen“ (**!**), um die Abfrage auszuführen.  
  
     Bei den Abfrageergebnissen handelt es sich um die Daten, die im Bericht angezeigt werden können.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="AddField"></a> Hinzufügen eines Felds zur Berichtsentwurfsoberfläche  
 Wenn Sie möchten, dass ein Feld aus dem Dataset in einem Bericht erscheint, werden Sie möglicherweise zunächst versuchen, das Feld direkt auf die Entwurfsoberfläche zu ziehen. Diese Übung zeigt auf, warum dies nicht funktioniert und wie stattdessen vorzugehen ist.  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a>So fügen Sie dem Bericht ein Feld hinzu (und erhalten das falsche Ergebnis)  
  
1.  Ziehen Sie das Feld **FullName** aus dem Berichtsdatenbereich auf die Entwurfsoberfläche.  
  
     Berichts-Generator erstellt ein Textfeld mit einem darin enthaltenen, dargestellt als Ausdruck \<Expr >.  
  
2.  Klicken Sie auf **Ausführen**.  
  
     Beachten Sie, dass nur ein Datensatz **Fernando Ross**, d.h. alphabetisch den ersten Datensatz in der Abfrage. Die anderen Datensätze in diesem Feld werden nicht erneut angezeigt.  
  
3.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
4.  Wählen Sie den Ausdruck \<Expr > in das Textfeld ein.  
  
5.  Im Eigenschaftenbereich für die **Value** -Eigenschaft wird Folgendes angezeigt (wenn der Bereich nicht angezeigt wird, wählen Sie auf der Registerkarte **Ansicht** die Option **Eigenschaften**aus):  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
     Die `First` -Funktion dient dazu, dass nur der erste Wert in einem Feld abgerufen wird, und genau dies war auch der Fall.  
  
     Durch das direkte Ziehen des Felds auf die Entwurfsoberfläche wurde ein Textfeld erstellt. Textfelder an sich sind keine Datenbereiche, weshalb darin keine Daten aus einem Berichtsdataset angezeigt werden. In Textfeldern in Datenbereichen, z. B. Tabellen, Matrizen und Listen werden hingegen Daten angezeigt.  
  
6.  Wählen Sie das Textfeld aus (wenn der Ausdruck ausgewählt wurde, drücken Sie ESC, um das Textfeld auszuwählen), und drücken Sie die ENTF-TASTE.  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a>So fügen Sie dem Bericht ein Feld hinzu (und erhalten das richtige Ergebnis)  
  
1.  Klicken Sie auf der Registerkarte **Einfügen** des Menübands im Bereich **Datenbereiche** auf **Liste**. Klicken Sie auf die Entwurfsoberfläche, und ziehen Sie anschließend den Mauszeiger, um ein Feld mit einer Breite von ungefähr fünf Zentimetern und einer Höhe von ca. 2,5 Zentimetern zu erstellen.  
  
2.  Ziehen Sie das Feld **FullName** aus dem Berichtsdatenbereich in das Listenfeld.  
  
     Dieses Mal erstellt der Berichts-Generator ein Textfeld mit dem Ausdruck `[FullName]` darin.  
  
3.  Klicken Sie auf **Ausführen**.  
  
     Dieses Mal werden im Feld alle Datensätze in der Abfrage erneut angezeigt.  
  
4.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
5.  Wählen Sie den Ausdruck im Textfeld aus.  
  
6.  Im Eigenschaftenbereich für die **Value** -Eigenschaft wird Folgendes angezeigt:  
  
    ```  
    =Fields!FullName.Value  
    ```  
  
     Durch Ziehen des Textfelds in den Listendatenbereich werden die im Dataset enthaltenen Daten angezeigt.  
  
7.  Wählen Sie das Listenfeld aus, und drücken Sie die ENTF-TASTE.  
  
##  <a name="AddTable"></a> Hinzufügen einer Tabelle auf der Berichtsentwurfsoberfläche  
 Erstellen Sie diese Tabelle, damit Sie Hyperlinks und den gedrehten Text an einer bestimmten Stelle ablegen können.  
  
#### <a name="to-add-a-table-to-the-report"></a>So fügen Sie dem Bericht eine Tabelle hinzu  
  
1.  Auf der **einfügen** Menü klicken Sie auf **Tabelle**, und klicken Sie dann auf **Tabellenassistenten**.  
  
2.  Auf der **wählen Sie ein Dataset** Seite des Assistenten neue Tabelle oder Matrix, klicken Sie auf **wählen Sie ein vorhandenes Dataset in diesem Bericht oder ein freigegebenes Dataset**, und klicken Sie auf **TextDataset (in diesem Bericht)**, und klicken Sie dann auf **Weiter**.  
  
3.  Auf der **Anordnen von Feldern** Seite, ziehen Sie die **Territory**, **LinkText**, und **Produkt** Felder **Zeilengruppen**, ziehen Sie die **Sales** Feld **Werte**, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **auswählen des Layouts** Deaktivieren der **Gruppen erweitern/reduzieren** das Kontrollkästchen, damit Sie die gesamte Tabelle sehen, und klicken Sie dann auf **Weiter**.  
  
5.  Auf der **Auswählen eines Formats** auf **Slate**, und klicken Sie dann auf **Fertig stellen**.  
  
6.  Ziehen Sie die Tabelle, damit sie sich unter dem Titelblock befindet.  
  
7.  Klicken Sie auf **Ausführen**.  
  
     Die Tabelle sieht einwandfrei aus, enthält jedoch zwei Ergebniszeilen. Die **LinkText** -Feld benötigt keine Ergebniszeilen.  
  
8.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
9. Mit der rechten Maustaste in des Textfelds mit `[LinkText]`, und klicken Sie auf **Zellen teilen**.  
  
10. Wählen Sie die leere Zelle unter der `[LinkText]` Zelle, und klicken Sie dann die UMSCHALTTASTE gedrückt halten und wählen Sie die zwei Zellen rechts daneben: die **insgesamt** Zelle die **Produkt** Spalte und die `[Sum(Sales)]` Zelle in der  **Sales** Spalte.  
  
11. Klicken Sie mit diese drei Zellen ausgewählt sind, mit der rechten Maustaste eine der Zellen, und klicken Sie auf **Zeile löschen**.  
  
12. Klicken Sie auf **Ausführen**.  
  
##  <a name="AddHyperlink"></a> Hinzufügen eines Links zum Bericht  
 In diesem Abschnitt fügen Sie dem Text in der Tabelle aus dem vorherigen Abschnitt einen Link hinzu.  
  
#### <a name="to-add-a-hyperlink-to-the-report"></a>So fügen Sie dem Bericht einen Link hinzu  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Zelle, die `[LinkText]`enthält, und klicken Sie auf **Textfeldeigenschaften**.  
  
3.  In der **Textfeldeigenschaften** auf **Aktion**.  
  
4.  Klicken Sie auf **Gehe zu URL**.  
  
5.  In der **URL auswählen** auf **[URL]**, und klicken Sie dann auf **OK**.  
  
6.  Das Aussehen des Texts unterscheidet sich nicht. Es muss jedoch dem des Linktexts entsprechen.  
  
7.  Wählen Sie `[LinkText]`aus.  
  
8.  In der **Schriftart** Teil der **Startseite** Registerkarte, klicken Sie auf der **unterstrichen** Schaltfläche, und klicken Sie dann auf den Dropdown-Pfeil neben der **Farbe** Schaltfläche und klicken Sie auf **blaue**.  
  
9. Klicken Sie auf **Ausführen**.  
  
     Der Text sieht nun wie ein Link aus.  
  
10. Klicken Sie auf einen Link. Wenn der Computer mit dem Internet verbunden ist, wird vom Browser ein Hilfethema zu Berichts-Generator geöffnet.  
  
##  <a name="RotateText"></a> Drehen des Textfelds im Bericht  
 In diesem Abschnitt drehen Sie Text in der Tabelle aus den vorherigen Abschnitten.  
  
#### <a name="to-rotate-text"></a>So drehen Sie Text  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zurückzukehren.  
  
2.  Klicken Sie in die Zelle, die enthält. `[Territory].`  
  
3.  Klicken Sie auf der Registerkarte **Stamm** im Abschnitt **Schriftart** auf die Schaltfläche **Fett** .  
  
4.  Wenn der Eigenschaftenbereich nicht geöffnet ist, aktivieren Sie auf der Registerkarte **Ansicht** das Kontrollkästchen **Eigenschaften** .  
  
5.  Suchen Sie die WritingMode-Eigenschaft im Bereich Eigenschaften.  
  
    > [!NOTE]  
    >  Wenn die Eigenschaften im Eigenschaftenbereich in Kategorien angeordnet sind, befindet sich WritingMode in der Kategorie **Lokalisierung** . Stellen Sie sicher, dass Sie die Zelle und nicht den Text ausgewählt haben. WritingMode ist eine Eigenschaft des Textfeldes, nicht des Texts.  
  
6.  Klicken Sie in das Listenfeld **Rotate270**.  
  
7.  Auf der **Startseite** Registerkarte die **Absatz** auf die **mittleren** und **Center** Schaltflächen, um den Text in der Mitte der Zelle zu platzieren vertikal und horizontal.  
  
8.  Klicken Sie auf (**!**).  
  
 Nun verläuft der Text in der `[Territory]` -Zelle in den Zellen vertikal von unten nach oben.  
  
##  <a name="FormatHTML"></a> Anzeigen von Text mit HTML-Formatierung  
  
#### <a name="to-display-text-formatted-as-html"></a>So zeigen Sie als HTML formatierten Text an  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zu wechseln.  
  
2.  Klicken Sie auf der Registerkarte **Einfügen** auf **Textfeld**. Klicken Sie anschließend auf die Entwurfsoberfläche, und ziehen Sie den Mauszeiger, um unter der Tabelle ein Textfeld mit einer Breite von etwa zehn Zentimetern und einer Höhe von etwa 7,5 Zentimetern zu ziehen.  
  
3.  Kopieren Sie diesen Text, und fügen Sie ihn in das Textfeld ein:  
  
    ```  
    <h4>Limitations of cascading style sheet attributes</h4>  
          <p>Only a basic set of <b>cascading style sheet (CSS)</b> attributes are defined:</p>  
          <ul><li>  
              text-align, text-indent  
            </li><li>  
              font-family, font-size  
            </li><li>  
              color  
            </li><li>  
              padding, padding-bottom, padding-top, padding-right, padding-left  
            </li><li>  
              font-weight  
            </li></ul>  
    ```  
  
4.  Wählen Sie den gesamten Text im Textfeld aus.  
  
     Dies ist eine Eigenschaft des Texts (nicht des Textfelds). Daher kann in einem Textfeld eine Mischung aus Nur-Text und Text, die HTML-Tags als Formatvorlagen verwenden.  
  
5.  Klicken Sie mit der rechten Maustaste auf den gesamten ausgewählten Text und anschließend auf **Texteigenschaften**.  
  
6.  Auf der **allgemeine** Seite **Markuptyp**, klicken Sie auf **HTML - interpretieren von HTML-Tags als Formate**.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie auf „Ausführen“ (**!**), um eine Vorschau des Berichts anzuzeigen.  
  
 Der Text im Textfeld wird als Überschrift, Absatz und Aufzählung angezeigt.  
  
##  <a name="FormatCurrency"></a> Formatieren von Währung  
  
#### <a name="to-format-numbers-as-currency"></a>So formatieren Sie Zahlen als Währung  
  
1.  Klicken Sie auf **Entwurf** , um zur Entwurfsansicht zu wechseln.  
  
2.  Klicken Sie auf die oberste Tabellenzelle, die `[Sum(Sales)]`enthält, halten Sie die UMSCHALTTASTE gedrückt, und klicken Sie auf die unterste Tabellenzelle, die `[Sum(Sales)]`enthält.  
  
3.  Klicken Sie auf der Registerkarte **Stamm** in der Gruppe **Zahl** auf die Schaltfläche **Währung** .  
  
4.  (Optional) Auf der **Startseite** Registerkarte die **Anzahl** gruppieren, klicken Sie auf die **Platzhalterformate** Schaltfläche, und klicken Sie auf **Beispielwerte** , wie die Nummern angezeigt formatiert werden soll.  
  
5.  (Optional) Klicken Sie auf der Registerkarte **Stamm** in der Gruppe **Zahl** zweimal auf die Schaltfläche **Dezimalstellen verringern** , um volle Dollarbeträge ohne Centangaben anzuzeigen.  
  
6.  Klicken Sie auf „Ausführen“ (**!**), um eine Vorschau des Berichts anzuzeigen.  
  
 Im Bericht werden nun formatierte Daten angezeigt, und die Lesbarkeit wurde verbessert.  
  
##  <a name="Save"></a> Speichern des Berichts  
 Sie können Berichte auf einem Berichtsserver, in einer SharePoint-Bibliothek oder auf dem Computer speichern.  
  
 Speichern Sie in diesem Lernprogramm den Bericht auf einem Berichtsserver. Wenn Sie keinen Zugriff auf einen Berichtsserver besitzen, speichern Sie den Bericht auf dem Computer.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>So speichern Sie den Bericht auf einem Berichtsserver  
  
1.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
2.  Klicken Sie auf **Letzte Sites und Server**.  
  
3.  Wählen Sie den Namen des Berichtsservers aus, auf dem Sie zum Speichern von Berichten berechtigt sind, oder geben Sie ihn ein.  
  
     Die Meldung "Verbindung mit Berichtsserver wird hergestellt" wird angezeigt. Nachdem die Verbindung hergestellt wurde, sehen Sie den Inhalt des Berichtsordners, den der Berichtsserveradministrator als Standardspeicherort für Berichte angegeben hat.  
  
4.  Ersetzen Sie in **Name**den Standardnamen durch einen Namen Ihrer Wahl.  
  
5.  Klicken Sie auf **Speichern**.  
  
 Der Bericht wird auf dem Berichtsserver gespeichert. Der Name des Berichtsservers, mit dem Sie verbunden sind, wird in der Statusleiste unten im Fenster angezeigt.  
  
#### <a name="to-save-the-report-on-your-computer"></a>So speichern Sie den Bericht auf dem Computer  
  
1.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
2.  Klicken Sie auf **Desktop**, **Meine Dokumente**oder **Arbeitsplatz**, und navigieren Sie anschließend zu dem Ordner, in dem Sie den Bericht speichern möchten.  
  
3.  Ersetzen Sie in **Name**den Standardnamen durch einen Namen Ihrer Wahl.  
  
4.  Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Es gibt viele Möglichkeiten zum Formatieren von Text im Berichts-Generator [Lernprogramm: Erstellen eines Freiformberichts &#40;Berichts-Generator&#41; ](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) enthält weitere Beispiele.  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Formatieren von Berichtselementen (Berichts-Generator und SSRS)](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
