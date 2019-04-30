---
title: Zuordnen von m:n-Beziehungen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], many-to-many
- junction tables [SQL Server]
- many-to-many relationships [SQL Server]
- mapping many-to-many relationships [SQL Server]
- database diagrams [SQL Server], relationships
ms.assetid: 2977cf92-98b5-48b2-b0fd-8fbc7040f2b4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a943d0ed7cfb0932f7eec757b40fef4d8de6504c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63306011"
---
# <a name="map-many-to-many-relationships-visual-database-tools"></a>Zuordnen von m:n-Beziehungen (Visual Database Tools)
  Durch m:n-Beziehungen können Sie jede Zeile in einer Tabelle mit mehreren Zeilen in einer anderen Tabelle verknüpfen und umgekehrt. Sie können z. B. eine m:n-Beziehung zwischen der Tabelle `authors` und der Tabelle `titles` erstellen, um einerseits allen Autoren ihre Bücher und andererseits jedem Buch alle seine Autoren zuzuordnen. Das Erstellen einer 1:n-Beziehung von einer der beiden Tabellen würde fälschlicherweise angeben, dass jedes Buch nur einen Autor besitzen oder jeder Autor nur ein Buch schreiben kann.  
  
 In Datenbanken werden n:n-Beziehungen zwischen Tabellen mithilfe von Jointabellen erstellt. Eine Jointabelle enthält die Primärschlüsselspalten der beiden zu verknüpfenden Tabellen. Erstellen Sie dann eine Beziehung von den Primärschlüsselspalten beider Tabellen zu den korrespondierenden Spalten in der Jointabelle. In der Datenbank Pubs handelt es sich bei der Tabelle `titleauthor` um eine Jointabelle.  
  
### <a name="to-create-a-many-to-many-relationship-between-tables"></a>So erstellen Sie eine m:n-Beziehung zwischen Tabellen  
  
1.  Fügen Sie im Datenbankdiagramm die Tabellen hinzu, zwischen denen Sie eine m:n-Beziehung erstellen möchten.  
  
2.  Erstellen Sie eine dritte Tabelle, indem Sie mit rechten Maustaste auf das Diagramm klicken und anschließend im Kontextmenü **Neue Tabelle** auswählen. Die neue Tabelle fungiert als Jointabelle.  
  
3.  Ändern Sie im Dialogfeld **Namen auswählen** den vom System zugewiesenen Tabellennamen. Die Jointabelle zwischen der Tabelle `titles` und der Tabelle `authors` heißt jetzt `titleauthors`.  
  
4.  Kopieren Sie die Primärschlüsselspalten aus den beiden anderen Tabellen in die Jointabelle. Sie können der Jointabelle wie jeder anderen Tabelle weitere Spalten hinzufügen.  
  
5.  Der Primärschlüssel in der Jointabelle muss sämtliche Primärschlüsselspalten aus den beiden anderen Tabellen enthalten. Weitere Informationen finden Sie unter [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md).  
  
6.  Definieren Sie zwischen beiden Primärtabellen und der Jointabelle jeweils eine 1:n-Beziehung. Die Jointabelle muss in beiden Beziehungen die n-Seite darstellen. Weitere Informationen finden Sie unter [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md).  
  
    > [!NOTE]  
    >  Beim Erstellen einer Jointabelle in einem Datenbankdiagramm werden keine Daten aus den verknüpften Tabellen in die Jointabelle eingefügt. Informationen zum Einfügen von Daten in eine Tabelle finden Sie unter [Erstellen von Abfragen zum Einfügen von Ergebnissen &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Datenbankdiagrammen &#40;Visual Database Tools&#41;](work-with-database-diagrams-visual-database-tools.md)  
  
  
