---
title: Herstellen einer Verbindung mit Azure SQL-Datenbank (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- instance of SQL Azure
- metadata, refreshing
- refreshing metadata
- SQL Azure
- SQL Azure, connecting
- SQL Azure, connecting to
- SQL Azure, reconnecting
- SQL Azure, synchronizing metadata
ms.assetid: 1ba0d113-dc05-4431-8689-e14a8821bafd
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8924ffbbbbbedccdc3bb99469c92667efb822a4c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63138922"
---
# <a name="connecting-to-azure-sql-db-accesstosql"></a>Herstellen einer Verbindung mit Azure SQL-Datenbank (AccessToSQL)
Um den Zugriff auf Datenbanken zu SQL Azure zu migrieren, müssen Sie mit der Zielinstanz von SQL Azure verbinden. Wenn Sie eine Verbindung herstellen, wird SSMA Ruft Metadaten zu allen Datenbanken in der Instanz von SQL Azure-und Datenbank-Metadaten in der SQL Azure-Metadaten-Explorer angezeigt. SSMA speichert Informationen über die Instanz von SQL Azure verbunden sind, jedoch werden keine Kennwörter gespeichert werden.  
  
Die Verbindung mit SQL Azure bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie auf SQL Azure erneut, wenn Sie möchten, dass eine aktive Verbindung mit dem Server verbinden. Sie können offline arbeiten, bis Sie die Datenbankobjekte in SQL Azure laden und Migrieren von Daten.  
  
Metadaten zu der Instanz von SQL Azure wird nicht automatisch synchronisiert. Um die Metadaten in SQL Azure-Metadaten-Explorer zu aktualisieren, müssen Sie stattdessen manuell die SQL Azure-Metadaten aktualisieren. Weitere Informationen finden Sie unter "Synchronisieren von SQL Azure-Metadaten" im Abschnitt weiter unten in diesem Thema.  
  
## <a name="required-sql-azure-permissions"></a>SQL Azure erforderliche Berechtigungen  
Das Konto, das verwendet wird, zur Verbindung mit SQL Azure erfordert unterschiedliche Berechtigungen abhängig von den Aktionen, die das Konto ausführt:  
  
-   So konvertieren Sie Objekte der Zugriff auf [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax so aktualisieren Sie Metadaten aus SQL Azure oder Speichern der konvertierten Syntax, um Skripts, das Konto muss die Berechtigung zum Anmelden mit der Instanz von SQL Azure verfügen.  
  
-   Um Datenbankobjekte in SQL Azure zu laden, ist die Anforderung mindestens die Mitgliedschaft in der **Db_owner** Datenbankrolle in der Zieldatenbank.  
  
## <a name="establishing-a-sql-azure-connection"></a>Einrichten einer SQL Azure-Verbindung  
Bevor Sie den Zugriff auf Datenbankobjekte in SQL Azure-Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz von SQL Azure einrichten, die Access-Datenbank oder Datenbanken migriert werden sollen.  
  
Wenn Sie die Verbindungseigenschaften definieren, geben Sie auch die Datenbank, in dem Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Ebene des Zugriffs nach dem Herstellen einer Verbindung mit SQL Azure anpassen. Weitere Informationen finden Sie unter [Zuordnen von Microsoft Access-Datenbanken in SQL Server-Schemas](mapping-source-and-target-databases-accesstosql.md)  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung mit SQL Azure, stellen Sie sicher, dass die Instanz von SQL Azure ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit SQL Azure**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit SQL Azure** (diese Option ist aktiviert, nach der Erstellung eines Projekts).  
  
    Wenn Sie zuvor mit SQL Azure verbunden, gibt der Namen des Befehls werden **Wiederherstellen der Verbindung zu SQL Azure**.  
  
2.  Klicken Sie im Dialogfeld Verbindung geben Sie ein, oder wählen Sie den Namen des SQL Azure.  
  
3.  Geben Sie ein, wählen oder **Durchsuchen** der Name der Datenbank.  
  
4.  Geben Sie ein oder wählen Sie **Benutzername**.  
  
5.  Geben Sie die **Kennwort**.  
  
6.  SSMA empfiehlt verschlüsselte Verbindung für SQL Azure.  
  
7.  Klicken Sie auf **Verbinden**.  
  
> [!IMPORTANT]  
> SSMA für Access unterstützt keine Verbindung mit **master** Datenbank in SQL Azure.  
  
Wenn keine Datenbanken im SQL Azure-Konto vorhanden sind, können Sie erstellen, die erste Datenbank mit **Azure-Datenbank erstellen** Option, die auf das Klicken auf **Durchsuchen** Schaltfläche.  
  
## <a name="synchronizing-sql-azure-metadata"></a>Synchronisieren von SQL Azure-Metadaten  
Metadaten zu SQL Azure-Datenbanken wird nicht automatisch aktualisiert. Die Metadaten in SQL Azure-Metadaten-Explorer ist, dass eine Momentaufnahme der Metadaten, wenn Sie zunächst mit SQL Azure verbunden ist, oder der letzten Ausführung, die Sie manuell die Metadaten aktualisiert werden. Sie können die Metadaten für alle Datenbanken oder für jede einzelne Datenbank oder Datenbankobjekt, das manuell aktualisieren.  
  
**Zum Synchronisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit SQL Azure verbunden sind.  
  
2.  Wählen Sie in SQL Azure-Metadaten-Explorer das Kontrollkästchen neben der Datenbank oder das Datenbankschema, die Sie aktualisieren möchten.  
  
    Z. B. um die Metadaten für alle Datenbanken zu aktualisieren, wählen Sie das Kontrollkästchen neben den Datenbanken an.  
  
3.  Mit der rechten Maustaste, Datenbanken, oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **synchronisieren mit der Datenbank**.  
  
## <a name="refreshing-sql-azure-metadata"></a>Aktualisieren von SQL Azure-Metadaten  
Wenn SQL Azure-Schemas ändern, nachdem Sie eine Verbindung herstellen, können Sie Metadaten vom Server aktualisieren.  
  
**Aktualisieren von SQL Azure-Metadaten**  
  
-   In SQL Azure-Metadaten-Explorer mit der rechten Maustaste **Datenbanken**, und wählen Sie dann **Refresh from Database aktualisieren**.  
  
## <a name="reconnecting-to-sql-azure"></a>Wiederherstellen der Verbindung mit SQL Azure  
Die Verbindung mit SQL Azure bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie auf SQL Azure erneut, wenn Sie möchten, dass eine aktive Verbindung mit dem Server verbinden. Sie können offline arbeiten, bis Sie die Datenbankobjekte in SQL Azure laden und Migrieren von Daten.  
  
Das Verfahren zum Wiederherstellen der Verbindung mit SQL Azure ist identisch mit dem Verfahren zum Herstellen einer Verbindung.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Informationen zum Anpassen der Zuordnung zwischen Schemas für den Zugriff und SQL Azure-Datenbanken und Schemas finden Sie unter [Zuordnung Access-Datenbanken in SQL Server-Schemas](mapping-source-and-target-databases-accesstosql.md).  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Setting Project Options Projektoptionen](setting-conversion-and-migration-options-accesstosql.md).  
  
-   Wenn die Zuordnung von Datentypen für Quell- und zieleinstellungen anpassen möchten, finden Sie unter [Zuordnungsquelle und das Ziel Datentypen](mapping-source-and-target-data-types-accesstosql.md).  
  
-   Wenn Sie nicht zum Ausführen dieser Aufgaben verfügen, können Sie die Objektdefinitionen für Access-Datenbank in SQL Azure-Objektdefinitionen konvertieren. Weitere Informationen finden Sie unter [Access-Datenbanken konvertieren](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
