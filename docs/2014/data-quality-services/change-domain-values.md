---
title: Ändern von Domänenwerten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.values.f1
ms.assetid: 8c90ab70-3aea-4eaf-a174-4159485c87d3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 12d6db8e8f9add797d640f043de8470fa7a5ed15
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52392513"
---
# <a name="change-domain-values"></a>Ändern von Domänenwerten
  In diesem Thema wird beschrieben, wie die Metadaten in einer Wissensdatenbank in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) geändert und erweitert werden. Nachdem Sie Wissen durch die Wissensermittlung generiert haben, Wissen in die Wissensdatenbank oder Domänen importiert haben, oder eine Wissensdatenbank basierend auf einer anderen Wissensdatenbank erstellt haben, können Sie die Datenwerte interaktiv ändern. Die Generierung der Wissensdatenbank nutzt nicht nur computerunterstützte Prozesse, sondern ermöglicht Ihnen,, eigenes Wissen zu verwenden, um die Datenwerte zu überprüfen und sie wie folgt zu ändern:  
  
-   Hinzufügen eines Domänenwerts zur Wertliste oder Auswählen eines Werts und Löschen des Werts aus der Liste  
  
-   Ändern des Status eines Domänenwerts, der durch den DQS-Erkennungsprozess festgelegt wurde, in „Richtig“, „Fehler“ oder „Ungültig“  
  
-   Geben Sie für einen falschen oder ungültigen Wert einen Ersetzungswert ein. Ein Wert ist ungültig, wenn er nicht in die Domäne gehört, z. B., wenn er dem Domänendatentyp nicht entspricht oder eine Domänenregel nicht einhält. Ein Wert ist fehlerhaft, wenn er zwar in die Domäne gehört, aber einen Syntaxfehler aufweist.  
  
-   Legen Sie zwei oder mehr Werte als Synonyme fest, und ändern Sie den vom Erkennungsprozess festgelegten führenden Wert, so dass der führende Wert den Synonymwert ersetzt, wenn die Eigenschaft **Führenden Wert verwenden** beim Erstellen der Domäne festgelegt wurde.  
  
-   Importieren von Domänenwerten aus einer Excel-Datei  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
 Um einen Domänenwert zu ändern, müssen Sie eine Wissensdatenbank und eine Domäne in der Domänenverwaltungsaktivität geöffnet haben.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie müssen über die Rolle „dqs_kb_editor“ oder „dqs_administrator“ in der DQS_MAIN-Datenbank verfügen, um Domänenwerte zu ändern.  
  
##  <a name="Change"></a> Ändern von Domänenwerten  
 In der Tabelle **Wert** wird der Wissensdatenbank für eine einzelne Domäne hinzugefügtes Wissen angezeigt. Sie können jederzeit in der Domänenliste eine andere Domäne auswählen, um die Werte für diese Domäne anzuzeigen. Das Feld enthält die folgenden Spalten:  
  
-   In der Spalte **Wert** werden alle Werte angezeigt, die während des Ermittlungsprozesses der ausgewählten Domäne aus einem Feld im Datenbeispiel hinzugefügt wurden. Alle Werte, die als Fehler projiziert werden, werden als Synonym zu einem Wert angezeigt, der als richtig projiziert wird.  
  
-   In der Spalte **Typ** wird der Status des Werts angezeigt, wie vom Ermittlungsprozess bestimmt. Ein grünes Häkchen zeigt an, dass der Wert richtig ist oder korrigiert wurde. Ein rotes Kreuz zeigt an, dass der Wert einen Fehler aufweist. Ein orangefarbenes Dreieck mit einem Ausrufezeichen zeigt an, dass der Wert nicht gültig ist. Ein Wert, der nicht gültig ist, entspricht nicht den Datenanforderungen für die Domäne. Ein Wert, der einen Fehler aufweist, kann gültig sein, ist aber aus Datengründen nicht der richtige Wert.  
  
-   In der Spalte **Korrigieren in** wird ein richtiger Wert angezeigt, in den der Originalwert geändert wird, der als fehlerhaft oder ungültig gekennzeichnet wurde. DQS kann in Folge des Ermittlungsprozesses den richtigen Wert vorschlagen.  
  
 Um Werte zu ändern, gehen Sie wie folgt vor:  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ausführen der Data Quality-Clientanwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Öffnen oder erstellen Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm eine Wissensdatenbank. Wählen Sie **Domänenverwaltung** als Aktivität aus, und klicken Sie dann auf **Öffnen** oder **Erstellen**. Weitere Informationen finden Sie unter [Erstellen einer Wissensdatenbank](../../2014/data-quality-services/create-a-knowledge-base.md) oder [Öffnen einer Wissensdatenbank](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
    > [!NOTE]  
    >  Die Domänenverwaltung wird auf einer Seite des Data Quality Service-Clients ausgeführt, der fünf Registerkarten für separate Domänenverwaltungsvorgänge enthält. Es ist kein assistentengesteuerter Prozess; jeder Verwaltungsvorgang kann getrennt ausgeführt werden.  
  
3.  Wählen Sie aus der **Domänenliste** auf der Seite **Domänenverwaltung** die Domäne aus, in der Sie Werte ändern möchten, oder erstellen Sie eine neue Domäne. Wenn Sie eine neue Domäne erstellen müssen, finden Sie unter [Domäne erstellen](../../2014/data-quality-services/create-a-domain.md)weitere Informationen. Klicken Sie auf die Registerkarte **Domänenwerte** .  
  
4.  Zeigen Sie die zu ändernden Werte in der Tabelle **Wert** an. Weitere Informationen finden Sie weiter unten unter [So zeigen Sie die entsprechenden Werte an](#Display) .  
  
5.  Um den Status eines Werts zu ändern, gehen Sie wie folgt vor:  
  
    -   **Ausgewählte Domänenwerte als korrigiert festlegen**: Um den Status eines Werts von Fehler "oder" ungültig, korrigieren Sie ändern möchten, wählen Sie den Wert aus, und klicken Sie dann auf die **ausgewählte Domänenwerte als korrigiert festlegen** (überprüfen) aus nach Auswahl des Abwärtspfeils in der Symbolleiste oder aus der Dropdownliste Typ aus. Wenn der fehlerhafte oder ungültige Wert mit einem richtigen Wert gruppiert ist, löschen Sie diesen Wert nach dem Vorgang.  
  
    -   **Ausgewählte Domänenwerte als Fehler festlegen**: Um den Status eines Werts von richtig "oder" ungültig, Fehler zu ändern, wählen Sie den Wert aus, und klicken Sie dann auf die **ausgewählte Domänenwerte als Fehler** (Kreuz)-Symbol aus nach Auswahl des Abwärtspfeils in der Symbolleiste oder aus der Dropdownliste Typ aus. Sie können eine Korrektur in die Spalte **Korrigieren in** eingeben oder diese leer lassen.  
  
    -   **Ausgewählte Domänenwerte als ungültig festlegen**: Um den Status eines Werts von richtig "oder" Fehler auf ungültige ändern möchten, wählen Sie den Wert aus, und klicken Sie dann auf die **ausgewählte Domänenwerte als ungültig festlegen** (Dreieck)-Symbol aus nach Auswahl des Abwärtspfeils in der Symbolleiste oder aus der Dropdownliste Typ aus. Sie können eine Korrektur in die Spalte **Korrigieren in** eingeben oder diese leer lassen.  
  
    -   **Richtig**: Nachdem ein Wert oderungültig festgelegt, geben Sie einen neuen Wert in der **korrigieren in** Spalte. DQS fügt eine neue Zeile für den Ersatzwert hinzu, legt diesen als richtig fest und gruppiert dann die zwei Werte. Der neue Wert wird als führender Wert angezeigt. Dabei wird der führende Wert fett und der fehlerhafte oder ungültige Wert eingezogen dargestellt.  
  
6.  Um Werte als Gruppe von Synonymen festzulegen, wählen Sie mehrere richtige Werte aus, und gehen Sie dann wie folgt vor:  
  
    -   **Ausgewählte Domänenwerte als Synonyme festlegen**: Wählen Sie zum Festlegen von Synonymen mehrere Werte, die korrekt sind, und klicken Sie dann auf die **ausgewählte Domänenwerte als Synonyme festlegen** Symbol. DQS gruppiert die Werte und legt einen der Werte als führenden Wert fest, durch den die anderen Werte ersetzt werden. Wenn zwei Werte gruppiert werden, aber einer der Werte in der Gruppe fehlerhaft oder ungültig ist, sind die Werte keine Synonyme.  
  
        > [!NOTE]  
        >  Wenn Sie zwei oder mehr Werte in einer Gruppe und einen anderen Wert außerhalb der Gruppe auswählen und diese dann als Synonyme festlegen, erhalten Sie eine falsche Fehlermeldung. Die Werte werden ordnungsgemäß als Synonyme festgelegt, nachdem Sie die Fehlermeldung geschlossen haben.  
  
    -   **Beziehung zwischen ausgewählten Synonymen aufheben**: Um zwei oder mehr Werte die synonymzuordnung rückgängig zu machen, wählen Sie die Werte, und klicken Sie dann auf die **Beziehung zwischen ausgewählten Synonymen aufheben** Symbol. Die Werte müssen gruppiert und beide korrekt sein, damit die Gruppierung als Synonyme aufzuheben.  
  
    -   **Ausgewählten Domänenwert als führenden Wert der zugehörigen Gruppe festlegen**: Um den führenden Wert der Gruppe ändern möchten, wählen Sie einen Wert in der Gruppe, die nicht als führender Wert festgelegt ist, und klicken Sie dann auf die **ausgewählten Domänenwert als führenden Wert der zugehörigen Gruppe festlegen** Schaltfläche. Dies legt den führenden Wert als Ersatz für den anderen Wert fest. Dieser Vorgang kann nur verwendet werden, wenn Sie mindestens zwei gruppierte Werte festgelegt haben und Sie den von DQS festgelegten führenden Wert ändern möchten. Beachten Sie, dass der führende Wert durch eine blaue Zeile mit dem Wert in Fettdruck gekennzeichnet wird.  
  
7.  **Rechtschreibprüfung**: Wenn ein Wert eine wellige rote Unterstreichung aufweist, schlägt die Rechtschreibprüfung eine Korrektur für den Wert. Klicken Sie mit der rechten Maustaste auf den unterstrichenen Wert, und wählen Sie eine Korrektur aus, sofern zutreffend. Als Werttyp wird „Fehler“ festgelegt (oder beibehalten), und die Korrektur wird zur Spalte **Korrigieren in** hinzugefügt. Klicken Sie auf den Abwärtspfeil, um weitere vorgeschlagene Korrekturen anzuzeigen. Geben Sie eine Korrektur manuell ein, um sie dem Rechtschreibprüfungswörterbuch hinzuzufügen und als Korrektur auswählen zu können. Weitere Informationen finden Sie unter [Use the DQS Speller](../../2014/data-quality-services/use-the-dqs-speller.md) und [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).  
  
    > [!NOTE]  
    >  Um die Rechtschreibprüfung zu verwenden, können Sie diese auf der Seite **Domäneneigenschaften** aktivieren. Wenn sie auf der Seite **Domäneneigenschaften** deaktiviert ist, können Sie auf das Symbol **Rechtschreibprüfung aktivieren/deaktivieren** auf der Seite **Domänenwerte** klicken, um sie auf dieser Seite zu aktivieren.  
  
8.  **Neuen Domänenwert hinzufügen**: Klicken Sie auf diese Option, um eine Zeile am Ende der Tabelle hinzuzufügen. Nachdem Sie einen Wert eingegeben haben, wird die Zeile in alphabetischer Reihenfolge neu angeordnet und durch ein vorangestelltes Sternsymbol als neuer Eintrag gekennzeichnet.  
  
9. **Domänenwerte aus Excel importieren**: Klicken Sie auf den Pfeil nach unten, um neue Werte aus einer Excel-Tabellenkalkulation hinzuzufügen, die **Werte importieren** Symbol, und wählen Sie dann **Domänenwerte aus Excel importieren**. Geben Sie den Dateinamen ein, wählen Sie **Erste Zeile als Header verwenden** aus, sofern zutreffend, und klicken Sie dann auf **OK**. Weitere Informationen finden Sie unter [Importieren von Werten aus einer Excel-Datei in eine Domäne](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md).  
  
10. **Importieren von projektwerten**: Um neue Werte aus einem Data Quality-Projekt hinzuzufügen, indem Sie auf den Pfeil nach unten der **Werte importieren** , und wählen Sie dann **Projektwerte**. Geben Sie den Dateinamen ein, wählen Sie **Erste Zeile als Header verwenden** aus, sofern zutreffend, und klicken Sie dann auf **OK**. Wählen Sie das Projekt aus, aus dem Sie Werte importieren möchten, und klicken Sie auf **OK**. Die importierten Werte werden angezeigt. Klicken Sie auf **Fertig stellen**. Weitere Informationen finden Sie unter „Importieren von Projektwerten in eine Domäne“.  
  
11. **Ausgewählte Domänenwerte löschen**: Um eine oder mehrere vorhandene Werte aus der Domäne zu entfernen, wählen Sie die Werte in der werttabelle aus, und klicken Sie dann auf die **ausgewählte Domänenwerte löschen** Symbol. Ein Eintrag von DQS_NULL kann nicht gelöscht werden. Wenn Sie mehrere zu löschende Werte auswählen und einer davon DQS_NULL ist, schlägt der Vorgang daher fehl.  
  
12. Klicken Sie auf **Fertig stellen** , um die Domänenverwaltungsaktivität abzuschließen, wie in [Beenden der Domänenverwaltungsaktivität](../../2014/data-quality-services/end-the-domain-management-activity.md)beschrieben.  
  
##  <a name="FollowUp"></a> Zur Nachverfolgung: Nach dem Ändern von Domänenwerten  
 Nachdem Sie Domänenwerte geändert haben, können Sie andere Domänenverwaltungstasks in der Domäne ausführen, Sie können die Wissensermittlung durchführen, um der Domäne Wissen hinzuzufügen, oder Sie können der Domäne eine Abgleichsrichtlinie hinzufügen. Weitere Informationen finden Sie unter [Durchführen der Wissensermittlung](../../2014/data-quality-services/perform-knowledge-discovery.md), [Verwalten einer Domäne](../../2014/data-quality-services/managing-a-domain.md) oder [Erstellen einer Abgleichsrichtlinie](../../2014/data-quality-services/create-a-matching-policy.md).  
  
##  <a name="Meaning"></a> Die Bedeutung von richtigen, fehlerhaften und ungültigen Werten  
 Jedem Wert in der Tabelle **Wert** der Seite **Domänenwerte** wird eine Einstellung für **Typ** von **Richtig**, **Fehler**oder **Ungültig**zugewiesen. Der Typ des Werts wird anfänglich von der Wissensermittlungsaktivität generiert, Sie können diesen jedoch nach Bedarf ändern. Der abschließende sowohl auf der Ermittlung als auch auf interaktiven Änderungen basierende Typ wird durch die Bereinigungsaktivität generiert. Diese Einstellungen haben die folgenden Bedeutungen:  
  
-   **Richtig:** Dies ist ein Wert, der gehört zur Domäne und verfügt nicht über alle Syntaxfehler. Beispiel: „Chicago“ ist in einer Ortsdomäne richtig.  
  
-   **Fehler:** Dies ist ein Wert, der mit der Domäne gehört, ist aber fehlerhaft. Beispiel: „Shicago“ statt „Chicago“ ist in einer Ortsdomäne fehlerhaft. DQS kennzeichnet einen Wert als fehlerhaft, wenn ein Syntaxfehler und eine zugehörige Korrektur im Ermittlungsprozess erkannt wird. Syntaxfehler schließen auch orthographische Fehler ein.  
  
-   **Ungültig:** Dies ist ein Wert, der nicht zur Domäne gehört, und verfügt nicht über eine Korrektur. Beispiel: Der Wert „12345“ in einer Ortsdomäne ist ungültig. DQS kennzeichnet einen Wert als ungültig, wenn er eine Domänenregel nicht erfüllt.  
  
 Sie können den Typ eines Werts manuell in einen der beiden anderen Werte ändern. DQS erzwingt bei manuellen Vorgängen keine Gültigkeits- und Fehlersemantik. Sie können eine Korrektur für einen ungültigen Wert eingeben, ohne den Status zu ändern. Sie können einen Wert als ungültig festlegen, auch wenn er keiner Domänenregel widerspricht. Sie können einen Wert als fehlerhaft festlegen, auch wenn der Ermittlungsprozess nicht angegeben hat, dass er einen Syntaxfehler aufweist. Sie können außerdem eine Korrektur eines fehlerhaften Werts entfernen, der als richtig markiert wurde, ohne den Status zu ändern.  
  
 Wenn Sie eine interaktive Datenbereinigung auf der Seite **Ergebnisse verwalten und anzeigen** der Aktivität **Bereinigung** ausführen, werden sowohl ungültige als auf fehlerhafte Werte auf der Registerkarte **Ungültig** der Seite **Ergebnisse verwalten und anzeigen** angezeigt.  
  
##  <a name="Display"></a> How to Display the Appropriate Values  
 Sie können die Anzeige wie folgt ändern:  
  
-   **Filtern** Sie die Ergebnisse, die in der Tabelle angezeigt werden sollen, basierend auf deren Status, indem Sie in der Dropdownliste **Filter** den Status auswählen.  
  
-   **Suchen** Sie die Daten, die Sie prüfen oder ändern möchten, indem Sie einen oder mehrere zu suchende Buchstaben in das Textfeld **Suchen** eingeben. Hierdurch werden die Buchstaben hervorgehoben, wenn diese in einem beliebigen angezeigten Wert vorkommen.  
  
-   Klicken Sie aus **Nur neue anzeigen** , um die in der Tabelle angezeigten Werte auf die Werte zu beschränken, die in der aktuellen Sitzung ermittelt wurden, und um vorherige Werte auszuschließen.  
  
-   Klicken Sie die Schaltfläche **Alle erweitern** , um alle Werte in einer beliebigen Gruppe von Synonymen anzuzeigen, wenn der aktuelle Status reduziert ist.  
  
-   Klicken Sie die Schaltfläche **Alle reduzieren** , um alle Werte mit Ausnahme des führenden Werts in einer beliebigen Gruppe von Synonymen auszublenden, wenn der aktuelle Status erweitert ist.  
  
-   Klicken Sie auf die Schaltfläche **Bereich mit dem Verlauf der Domänenwertänderungen anzeigen/ausblenden** , um unterhalb der Werttabelle den Vorschaubereich einzublenden, in dem die letzten Änderungen an der Domänenwertsammlung angezeigt werden.  
  
##  <a name="Null"></a> So verarbeiten Sie NULL-Entsprechungen  
 Jede Werttabelle auf der Registerkarte **Domänenwerte** enthält einen DQS_NULL-Wert. Ein NULL-Wert in einer Datenquelle wird in der Werttabelle als SQL_NULL angezeigt. Sie können eine oder mehrere NULL-Entsprechungen als Synonyme für DQS_NULL festlegen. In diesem fall werden alle NULL-Werte und NULL-Entsprechungen als DQS_NULL verarbeitet.  
  
  
