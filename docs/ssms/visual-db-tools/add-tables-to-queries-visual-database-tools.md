---
title: Hinzufügen von Tabellen zu Abfragen
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
- queries [SQL Server], tables
ms.assetid: 6551aa7e-31a1-4636-852a-819bc53d658b
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 3f333e275441f211457e14800cae14d19bd83b2a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75245371"
---
# <a name="add-tables-to-queries-visual-database-tools"></a>Hinzufügen von Tabellen zu Abfragen (Visual Database Tools)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Beim Erstellen einer Abfrage rufen Sie Daten aus einer Tabelle oder aus anderen Objekten mit Tabellenstruktur ab, z.B. aus Ansichten und bestimmten benutzerdefinierten Funktionen. Objekte, mit denen Sie in der Abfrage arbeiten möchten, müssen Sie dem **Diagrammbereich**hinzufügen.  
  
### <a name="to-add-a-table-or-table-valued-object-to-a-query"></a>So fügen Sie einer Abfrage eine Tabelle oder ein Tabellenwertobjekt hinzu  
  
1.  Klicken Sie im **Diagrammbereich** des Abfrage- und Sicht-Designers mit der rechten Maustaste auf den Hintergrund, und wählen Sie im Kontextmenü **Tabelle hinzufügen** aus.  
  
2.  Wählen Sie im Dialogfeld **Tabelle hinzufügen** die Registerkarte für den Objekttyp aus, den Sie zur Abfrage hinzufügen möchten.  
  
3.  Doppelklicken Sie in der Liste der Elemente auf jedes Element, das hinzugefügt werden soll.  
  
4.  Klicken Sie auf **Schließen**, wenn Sie das Hinzufügen abgeschlossen haben.  
  
    Der Abfrage- und Sicht-Designer aktualisiert den **Diagrammbereich**, den **Kriterienbereich**und den **SQL-Bereich** entsprechend.  
  
Tabellen und Sichten werden der Abfrage automatisch hinzugefügt, wenn Sie in der Anweisung im SQL-Bereich einen entsprechenden Verweis einfügen.  
  
Der Abfrage- und Sicht-Designer zeigt keine Datenspalten für eine Tabelle oder ein Objekt mit Tabellenstruktur an, wenn Sie nicht über die erforderlichen Zugriffsrechte verfügen oder wenn der Anbieter keine Informationen über die Tabelle oder das Objekt zurückgeben kann. In diesen Fällen werden für die Tabelle oder für das Tabellenwertobjekt nur eine Titelleiste und das Kontrollkästchen * (Alle Spalten) angezeigt.  
  
### <a name="to-add-an-existing-query-to-a-new-query"></a>So fügen Sie einer neuen Abfrage eine vorhandene Abfrage hinzu  
  
1.  Vergewissern Sie sich, dass der **SQL-Bereich** in der neu erstellten Abfrage angezeigt wird.  
  
2.  Geben Sie im **SQL-Bereich**eine öffnende und schließende Klammer ()nach dem Wort FROM ein.  
  
3.  Öffnen Sie für die vorhandene Abfrage den Abfrage-Designer. (Es sind nun zwei Instanzen des Abfrage-Designers geöffnet.)  
  
4.  Öffnen Sie den **SQL-Bereich** für die innere, d.h. die bereits vorhandene Abfrage, die Sie in die neue, äußere Abfrage einbeziehen.  
  
5.  Markieren Sie im **SQL-Bereich**den gesamten Text, und kopieren Sie ihn in die Zwischenablage.  
  
6.  Klicken Sie auf den **SQL-Bereich** der neuen Abfrage, positionieren Sie den Cursor zwischen den eingefügten Klammern, und fügen Sie den Inhalt der Zwischenablage ein.  
  
7.  Fügen Sie dann im **SQL-Bereich**einen Alias nach der schließenden Klammer ein.  
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen von Tabellenaliasen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-table-aliases-visual-database-tools.md)  
[Entfernen von Tabellen aus Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/remove-tables-from-queries-visual-database-tools.md)  
[Angeben von Suchkriterien &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
