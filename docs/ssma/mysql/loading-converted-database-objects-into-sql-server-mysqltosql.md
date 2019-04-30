---
title: Loading Converted Database Objects into SQLServer (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ac993a6d-0283-4823-8793-6b217677dfa3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b2e58eb534088482493e6f36c3841f36644183af
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187227"
---
# <a name="loading-converted-database-objects-into-sql-server-mysqltosql"></a>Laden konvertierter Datenbankobjekte in SQL Server (MySqlToSql)
Nachdem Sie die MySQL-Datenbanken zu konvertiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, laden die daraus resultierende Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können entweder SSMA, die die Objekte zu erstellen, oder Sie können Skripts für die Objekte und führen Sie die Skripts selbst. Darüber hinaus SSMA können Sie die Metadaten mit den eigentlichen Inhalt der aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Auswählen zwischen Synchronisierung und Skripts  
Wenn Sie die konvertierten Datenbankobjekten in laden möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure ohne Änderungen, können Sie SSMA direkt zu erstellen oder die Datenbankobjekte neu erstellt haben. Dass die Methode kann schnell und einfach, aber es lässt sich nicht für die Anpassung der Transact-SQL-Code, definiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte.  
  
Verwenden Sie Wenn die Transact-SQL zu ändern, die zum Erstellen von Objekten verwendet werden sollen oder wenn Sie mehr Kontrolle über die Objekte erstellen möchten, SSMA zum Erstellen von Skripts. Sie können diese Skripts ändern, klicken Sie dann, jedes Objekt einzeln erstellen und verwenden SQL Server-Agent auch planen, diese Objekte erstellt.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Verwenden SSMA zum Synchronisieren von Objekten mit SQLServer  
Um SSMA zum Erstellen von SQL Server oder SQL Azure-Datenbank-Objekten zu verwenden, wählen Sie die Objekte im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer, und klicken Sie dann zu synchronisieren der Objekte mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, wie im folgenden Verfahren dargestellt. Standardmäßig, wenn die Objekte noch in vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, wenn der SSMA-Metadaten enthält, einige lokale Änderungen oder Updates für die Definition dieser Objekte sehr, SSMA ändern, die Objektdefinitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können das Standardverhalten ändern, indem Sie die Bearbeitung **Projekteinstellungen**.  
  
> [!NOTE]  
> Sie können auswählen, vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbankobjekte, die vom MySQL-Datenbanken nicht konvertiert wurden. Aber werden diese Objekte nicht neu erstellt oder geändert werden von SSMA.  
  
##### <a name="to-synchronize-objects-with-sql-server-or-sql-azure"></a>Zum Synchronisieren von Objekten mit SQL Server oder SQL Azure  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer, erweitern im oberen Bereich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Knoten, und erweitern Sie dann **Datenbanken**.  
  
2.  Wählen Sie die zu verarbeitenden Objekte aus:  
  
    -   Um eine vollständige Datenbank zu synchronisieren, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Klicken Sie zum Synchronisieren, oder lassen Sie einzelne Objekte oder Kategorien von Objekten, aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt oder einen Ordner.  
  
3.  Nachdem Sie die zu verarbeitenden in SQL Server oder SQL Azure-Metadaten-Explorer Objekte ausgewählt haben, mit der rechten Maustaste **Datenbanken**, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
    Sie können auch die einzelne Objekte oder Kategorien von Objekten synchronisieren, indem Sie mit der rechten Maustaste das Objekt oder der übergeordnete Ordner, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
    Danach SSMA zeigt die **synchronisieren mit der Datenbank** Dialogfeld hier Sie zwei Gruppen von Elementen sehen. Klicken Sie auf der linken Seite zeigt SSMA ausgewählte Datenbankobjekte in einer Struktur dargestellt. Klicken Sie auf der rechten Seite sehen Sie eine Struktur, die dieselben Objekte in der SSMA-Metadaten darstellt. Sie können die Struktur durch Klicken auf Links oder rechts erweitern Schaltfläche "+". Die Richtung der Synchronisierung wird in der Aktionsspalte zwischen die beiden Strukturen angeordnet wurden, angezeigt.  
  
    Eine Aktion anmelden können die folgenden drei Zustände aufweisen:  
  
    -   Ein Pfeil nach links bedeutet, dass der Inhalt der Metadaten in der Datenbank (Standard) gespeichert werden soll.  
  
    -   Ein Pfeil nach rechts bedeutet, dass es sich bei Datenbankinhalte die SSMA-Metadaten überschrieben werden.  
  
    -   Ein Kreuz bedeutet, dass keine weitere Aktion durchgeführt wird.  
  
    -   Klicken Sie auf der Aktion zum Ändern des Zustands. Tatsächliche Synchronisierung wird durchgeführt, wenn Sie auf **OK** -Schaltfläche der **synchronisieren mit der Datenbank** Dialogfeld.  
  
## <a name="scripting-objects"></a>Skripterstellung für Objekte  
Zum Speichern [!INCLUDE[tsql](../../includes/tsql-md.md)] Definitionen der konvertierten Datenbankobjekte, um die Objektdefinitionen ändern und Ausführen von Skripts selbst, können Sie speichern die konvertierte Datenbank Objektdefinitionen, [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts.  
  
**Zum Speichern von Objekten wie Skripts**  
  
1.  Nachdem Sie die Objekte, die in einem Skript speichern ausgewählt haben, mit der rechten Maustaste **Datenbanken**, und klicken Sie dann auf **speichern als Skript**.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten von der rechten Maustaste auf das Objekt oder der übergeordnete Ordner, und klicken Sie dann auf Skripts **speichern als Skript**.  
  
2.  In der **speichern unter** Dialogfeld Suchen den Ordner, in der Sie speichert das Skript, einen Dateinamen in eingeben möchten, die **Dateiname** Feld, und klicken Sie dann [!INCLUDE[clickOK](../../includes/clickok-md.md)] SSMA wird die SQL-Dateinamenerweiterung angefügt.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie die SQL Server- oder SQL Azure-Objektdefinitionen als Skript gespeichert haben, können Sie SQL Server Management Studio, um das Skript bearbeiten.  
  
**Um ein Skript zu ändern.**  
  
1.  Management Studio **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Klicken Sie im Dialogfeld "Öffnen" Suchen und wählen Sie die Skriptdatei, und klicken Sie dann auf **OK**.  
  
3.  Bearbeiten Sie die Skriptdatei mit dem abfrageeditor. Weitere Informationen zu den Abfrage-Editor finden Sie unter "-Editor der Einfachheit halber Befehle und Funktionen" in SQL Server-Onlinedokumentation.  
  
4.  Wählen Sie zum Speichern des Skripts im Menü Datei **speichern**.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
Sie können ein Skript oder einzelne Anweisungen in SQL Server Management Studio ausführen.  
  
**Zum Ausführen eines Skripts**  
  
1.  Auf dem SQL Server Management Studio **Datei** Startmenü **öffnen** , und klicken Sie dann auf **Datei**.  
  
2.  Klicken Sie im Dialogfeld "Öffnen" Suchen und wählen Sie die Skriptdatei, und klicken Sie dann auf **OK**.  
  
3.  Um das vollständige Skript auszuführen, drücken Sie die **F5** Schlüssel.  
  
4.  Um einen Satz von Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster, und drücken Sie dann die **F5** Schlüssel.  
  
5.  Weitere Informationen dazu, wie Sie den Abfrage-Editor verwenden, um Skripts auszuführen finden Sie unter "SQL Server Management Studio Transact-SQL-Abfrage" in SQL Server-Onlinedokumentation.  
  
6.  Sie können Skripts auch über die Befehlszeile ausführen, mit der **Sqlcmd** -Hilfsprogramm, und von SQL Server-Agent. Weitere Informationen zu **Sqlcmd**, finden Sie unter "Hilfsprogramms" Sqlcmd"" in SQL Server-Onlinedokumentation. Weitere Informationen zu SQL Server-Agent finden Sie unter "Automatisieren von administrativen Tasks (SQL Server-Agent)" in SQL Server-Onlinedokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern die Objekte in SQLServer  
Nachdem Sie die konvertierten Datenbankobjekten in SQL Server geladen haben, können Sie erteilen und Verweigern von Berechtigungen für diese Objekte. Es ist eine gute Idee, klicken Sie hierzu vor dem Migrieren von Daten in SQL Server. Informationen dazu, wie Sie sichere Objekte in SQL Server-Hilfe finden Sie unter "Security Überlegungen zu Datenbanken und Datenbankanwendungen" in SQL Server-Onlinedokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Im nächsten Schritt des Migrationsvorgangs [Migrieren von MySQL-Daten in SQL Server – Azure SQL-Datenbank &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
