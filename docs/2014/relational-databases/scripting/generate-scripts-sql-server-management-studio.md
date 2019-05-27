---
title: Erstellen von Skripts (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9711c617-3c68-4e5a-aea3-befc64d51524
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8aa65678c9604cac609ca1a914e542724d354872
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66090362"
---
# <a name="generate-scripts-sql-server-management-studio"></a>Erstellen von Skripts (SQL Server Management Studio)
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] stellt zwei Mechanismen zum Generieren von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts bereit. Verwenden Sie zum Erstellen von Skripts für mehrere Objekte den **Assistenten zum Generieren und Veröffentlichen von Skripts**. Sie können ein Skript für einzelne Objekte oder mehrere Objekte auch über das Menü **Skript für** im **Objekt-Explorer**generieren.  
  
1.  **Wählen Sie eine Methode ein:**  [Generieren und Veröffentlichen von Skripts Assistenten](#GenPubScriptWiz), [Objekt-Explorer-Skript als Menü](#OEScriptAsMenu)  
  
2.  **So verwenden Sie das Skript als Menü:**  [Skript für ein einzelnes Objekt](#ScriptSingleObject), [Skript für zwei Objekte mithilfe des Objekt-Explorer](#ScriptTwoObjectsOE), [Skript für zwei Objekte mithilfe von Details zum Objekt-Explorer](#ScriptTwoObjectsOED)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Wählen Sie den Mechanismus aus, der Ihre Anforderungen am besten erfüllt.  
  
###  <a name="GenPubScriptWiz"></a> Assistent zum Generieren und Veröffentlichen von Skripts  
 Verwenden Sie den **Assistenten zum Generieren und Veröffentlichen von Skripts** , um ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript für zahlreiche Objekte zu erstellen. Der Assistent generiert ein Skript für alle in einer Datenbank enthaltenen Objekte bzw. für eine ausgewählte Teilmenge der Objekte. Der Assistent verfügt über viele Optionen für Skripts, z. B. ob Berechtigungen, Sortierung, Einschränkungen usw. eingeschlossen werden sollen. Anweisungen zum Verwenden des Assistenten finden Sie unter [Generate and Publish Scripts Wizard](generate-and-publish-scripts-wizard.md).  
  
###  <a name="OEScriptAsMenu"></a> Objekt-Explorer-Menü "Skript für Objekttyp als"  
 Sie können das Objekt-Explorer-Menü **Skript für Objekttyp als** verwenden, um ein Skript für ein einzelnes Objekt, für mehrere Objekte bzw. mehrere Anweisungen für einzelne Objekte zu erstellen. Sie können unter mehreren Skripttypen auswählen: z. B. zum Erstellen, Ändern oder Löschen des Objekts. Sie können das Skript entweder im Abfrage-Editor-Fenster, in einer Datei oder in der Zwischenablage speichern. Das Skript wird im Unicode-Format erstellt.  
  
##  <a name="ScriptSingleObject"></a> So generieren Sie ein Skript für ein einzelnes Objekt  
 **So erstellen Sie ein Skript für ein einzelnes Objekt**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie dann die Datenbank, die das Objekt enthält, das geschrieben werden soll.  
  
3.  Erweitern Sie die Kategorie des Objekts. Beispiel: Erweitern Sie den Knoten **Tabellen** oder **Sichten** .  
  
4.  Klicken Sie mit der rechten Maustaste auf das Objekt, zeigen Sie auf **Skript für \<Objekttyp> als**. Zeigen Sie z.B. auf **Skripttabelle als**.  
  
5.  Zeigen Sie auf den Skripttyp, z. B. **CREATE in** oder **ALTER in**.  
  
6.  Wählen Sie den Speicherort zum Speichern des Skripts aus, z. B. **Neues Abfrage-Editor-Fenster** oder **Zwischenablage**.  
  
##  <a name="ScriptTwoObjectsOE"></a> So generieren Sie mithilfe des Objekt-Explorers ein Skript für zwei Objekte  
 **So erstellen Sie ein Skript für zwei Objekte mithilfe des Objekt-Explorers**  
  
 Möglicherweise benötigen Sie in einigen Fällen ein Skript mit mehreren Optionen, z. B. zum Löschen und anschließenden Erstellen einer Prozedur oder zum Erstellen und anschließenden Ändern einer Tabelle. Die folgenden Verfahren zum Generieren von Skripts für mehrere Objekte sind auch erfolgreich, wenn Sie ein Skript erstellen müssen, das auf verschiedene Objekttypen verweist, z. B. Tabellen, Sichten und gespeicherte Prozeduren.  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie dann die Datenbank, die die Objekte enthält, die geschrieben werden sollen.  
  
3.  Klicken Sie mit der rechten Maustaste auf das erste zu schreibende Objekt, zeigen Sie auf **Skript für \<Objekttyp> als**, und wählen Sie unter **Speichern unter** die Option **Neues Fenster für den Abfrageeditor** als Ausgabeziel aus.  
  
4.  Navigieren Sie zum zweiten Objekt, für das Sie ein Skript erstellen möchten.  
  
5.  Klicken Sie mit der rechten Maustaste auf das Objekt, zeigen Sie auf **Skript für \<Objekttyp> als**, und wählen Sie unter **Speichern unter** die Option **Zwischenablage** als Ausgabeziel aus.  
  
6.  Fügen Sie in dem für das erste Objekt geöffneten Abfrage-Editor-Fenster das Skript für das zweite Objekt aus der Zwischenablage ein.  
  
##  <a name="ScriptTwoObjectsOED"></a> So generieren Sie mit "Details zum Objekt-Explorer" ein Skript für zwei Objekte  
 **So erstellen Sie ein Skript für zwei Objekte mithilfe von "Details zum Objekt-Explorer"**  
  
 Sie können den Bereich **Details zum Objekt-Explorer** verwenden, um ein Skript für mehrere Objekte der gleichen Kategorie zu generieren.  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie dann die Datenbank, die die Objekte enthält, die geschrieben werden sollen.  
  
3.  Erweitern Sie den Kategorieknoten der Objekttypen, für die Sie ein Skript erstellen möchten, z. B. den Knoten **Tabellen** .  
  
4.  Öffnen Sie den Bereich **Details zum Objekt-Explorer** durch Drücken von **F7**oder durch Öffnen des Menüs **Ansicht** und Auswahl der Option **Details zum Objekt-Explorer**.  
  
5.  Klicken Sie mit der linken Maustaste auf eines der Objekte, für das Sie ein Skript erstellen möchten.  
  
6.  Klicken Sie bei gedrückter STRG-TASTE mit der linken Maustaste auf das zweite Objekt, für das Sie ein Skript erstellen möchten.  
  
7.  Klicken Sie mit der rechten Maustaste auf eines der ausgewählten Objekte, und wählen Sie **Skript für \<Objekttyp> als** aus.  
  
  
