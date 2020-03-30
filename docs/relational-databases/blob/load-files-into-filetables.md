---
title: Laden von Dateien in FileTables | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], migrating files
- FileTables [SQL Server], bulk loading
- FileTables [SQL Server], loading files
ms.assetid: dc842a10-0586-4b0f-9775-5ca0ecc761d9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: de6e6a237c0aa80e2793f33373ec664dfe93f953
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "72908707"
---
# <a name="load-files-into-filetables"></a>Laden von Dateien in FileTables
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Beschreibt, wie Dateien in FileTables geladen und migriert werden.  
  
##  <a name="loading-or-migrating-files-into-a-filetable"></a><a name="BasicsLoadNew"></a> Laden oder Migrieren von Dateien in FileTables  
 Die Methode, die Sie zum Laden oder Migrieren von Dateien in eine FileTable auswählen, ist davon abhängig, wo die Dateien aktuell gespeichert sind.  
  
|Aktueller Speicherort von Dateien|Optionen für die Migration|  
|-------------------------------|---------------------------|  
|Dateien sind derzeit im Dateisystem gespeichert.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat keine Informationen über die Dateien.|Da eine FileTable im Windows-Dateisystem als Ordner angezeigt wird, können Sie Dateien mithilfe einer der verfügbaren Methoden zum Verschieben oder Kopieren von Dateien ganz einfach in eine neue FileTable laden. Zu diesen Methoden gehören Windows-Explorer, Befehlszeilenoptionen, einschließlich „xcopy“ und „robocopy“, sowie benutzerdefinierte Skripts oder Anwendungen.<br /><br /> Sie können einen vorhandenen Ordner nicht in eine FileTable konvertieren.|  
|Dateien sind derzeit im Dateisystem gespeichert.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält eine Tabelle von Metadaten, die Zeiger auf die Dateien enthält.|Der erste Schritt besteht darin, die Dateien mithilfe einer der oben erwähnten Methoden zu verschieben oder zu kopieren.<br /><br /> Der zweite Schritt besteht darin, die vorhandene Tabelle von Metadaten so zu aktualisieren, dass diese auf den neuen Speicherort der Dateien zeigt.<br /><br /> Weitere Informationen finden Sie unter [Example: Migrieren von Dateien aus dem Dateisystem in eine Dateitabelle](#HowToMigrateFiles) in diesem Artikel.|  
  
###  <a name="how-to-load-files-into-a-filetable"></a><a name="HowToLoadNew"></a> Vorgehensweise: Laden von Dateien in eine Dateitabelle  
Sie können die folgenden Methoden verwenden, um Dateien in eine FileTable zu laden:  
  
-   Drag & Drop von Dateien aus den Quellordnern in den neuen FileTable-Ordner in Windows-Explorer.  
  
-   Verwenden Sie Befehlszeilenoptionen wie MOVE, COPY, XCOPY oder ROBOCOPY an der Eingabeaufforderung oder in einer Batchdatei oder einem Skript.  
  
-   Schreiben Sie eine benutzerdefinierte Anwendung in C# oder Visual Basic.NET, um die Dateien zu verschieben oder zu kopieren. Rufen Sie Methoden aus dem Namespace **System.IO** auf.  
  
###  <a name="example-migrating-files-from-the-file-system-into-a-filetable"></a><a name="HowToMigrateFiles"></a> Beispiel: Migrieren von Dateien aus dem Dateisystem in eine Dateitabelle  
 In diesem Szenario werden die Dateien im Dateisystem gespeichert, und Sie verfügen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über eine Tabelle mit Metadaten, die Zeiger auf die Dateien enthält. Sie möchten die Dateien in eine FileTable verschieben und den ursprünglichen UNC-Pfad für jede Datei in den Metadaten durch den FileTable-UNC-Pfad ersetzen. Die Funktion [GetPathLocator &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getpathlocator-transact-sql.md) hilft Ihnen, dieses Ziel zu erreichen.  
  
 Nehmen Sie für dieses Beispiel an, dass eine Datenbanktabelle, **PhotoMetadata**, vorhanden ist, die Daten zu Fotos enthält. Diese Tabelle enthält eine Spalte **UNCPath** des Typs **varchar**(512), der den tatsächlichen UNC-Pfad zu einer JPG-Datei enthält.  
  
 Um die Bilddateien aus dem Dateisystem in eine FileTable zu migrieren, müssen Sie wie folgt vorgehen:  
  
1.  Erstellen Sie eine neue FileTable, in der sich die Dateien befinden. In diesem Beispiel wird der Tabellenname **dbo.PhotoTable**verwendet; es wird jedoch nicht der Code zum Erstellen der Tabelle aufgeführt.  
  
2.  Verwenden Sie xcopy oder ein ähnliches Tool, um die JPG-Dateien mit ihrer Verzeichnisstruktur in das Stammverzeichnis der FileTable zu kopieren.  
  
3.  Korrigieren Sie die Metadaten in der Tabelle **PhotoMetadata** mithilfe von Code, der ähnlich wie im folgenden Beispiel aussieht:  

```sql  
--  Add a path locator column to the PhotoMetadata table.  
ALTER TABLE PhotoMetadata ADD pathlocator hierarchyid;  
  
-- Get the root path of the Photo directory on the File Server.  
DECLARE @UNCPathRoot varchar(100) = '\\RemoteShare\Photographs';  
  
-- Get the root path of the FileTable.  
DECLARE @FileTableRoot varchar(1000);  
SELECT @FileTableRoot = FileTableRootPath('dbo.PhotoTable');  
  
-- Update the PhotoMetadata table.  
  
-- Replace the File Server UNC path with the FileTable path.  
UPDATE PhotoMetadata  
    SET UNCPath = REPLACE(UNCPath, @UNCPathRoot, @FileTableRoot);  
  
-- Update the pathlocator column to contain the pathlocator IDs from the FileTable.  
UPDATE PhotoMetadata  
    SET pathlocator = GetPathLocator(UNCPath);  
```  
  
##  <a name="bulk-loading-files-into-a-filetable"></a><a name="BasicsBulkLoad"></a> Massenladen von Dateien in eine FileTable  
 Eine FileTable verhält sich bei Massenvorgängen wie eine normale Tabelle, jedoch mit folgenden Merkmalen:  
  
 Eine FileTable weist systemdefinierte Einschränkungen auf, die sicherstellen, dass die Integrität des Datei- und Verzeichnisnamespace erhalten bleibt. Diese Einschränkungen müssen für die Daten überprüft werden, die mit einem Massenvorgang in die FileTable geladen wurden. Da einige Masseneinfügungsvorgänge das Ignorieren der Tabelleneinschränkungen zulassen, werden folgende Anforderungen erzwungen.  
  
-   Massenladevorgänge, die Einschränkungen erzwingen, können für eine FileTable sowie alle anderen Tabellen ausgeführt werden. Zu dieser Kategorie gehören die folgenden Vorgänge:  
  
    -   bcp mit CHECK_CONSTRAINTS-Klausel.  
  
    -   BULK INSERT mit CHECK_CONSTRAINTS-Klausel.  
  
    -   INSERT INTO ... SELECT * FROM OPENROWSET(BULK ...) ohne IGNORE_CONSTRAINTS-Klausel.  
  
-   Massenladevorgänge, die keine Einschränkungen erzwingen, führen zu Fehlern, es sei denn, die für FileTable vom System definierten Einschränkungen wurden deaktiviert. Zu dieser Kategorie gehören die folgenden Vorgänge:  
  
    -   bcp ohne CHECK_CONSTRAINTS-Klausel.  
  
    -   BULK INSERT ohne CHECK_CONSTRAINTS-Klausel.  
  
    -   INSERT INTO ... SELECT * FROM OPENROWSET(BULK ...) mit IGNORE_CONSTRAINTS-Klausel.  
  
###  <a name="how-to-bulk-load-files-into-a-filetable"></a><a name="HowToBulkLoad"></a> Vorgehensweise: Massenladen von Dateien in eine Dateitabelle  
 Sie können verschiedene Methoden zum Massenladen von Dateien in eine FileTable verwenden:  
  
-   **bcp**  
  
    -   Aufruf mit der **CHECK_CONSTRAINTS** -Klausel.  
  
    -   Deaktivieren Sie den FileTable-Namespace, und führen Sie den Aufruf ohne die **CHECK_CONSTRAINTS** -Klausel aus. Aktivieren Sie dann den FileTable-Namespace erneut.  
  
-   **BULK INSERT**  
  
    -   Aufruf mit der **CHECK_CONSTRAINTS** -Klausel.  
  
    -   Deaktivieren Sie den FileTable-Namespace, und führen Sie den Aufruf ohne die **CHECK_CONSTRAINTS** -Klausel aus. Aktivieren Sie dann den FileTable-Namespace erneut.  
  
-   **INSERT INTO ... SELECT \* FROM OPENROWSET(BULK...)** .  
  
    -   Aufruf mit der **IGNORE_CONSTRAINTS** -Klausel.  
  
    -   Deaktivieren Sie den FileTable-Namespace, und führen Sie den Aufruf ohne die **IGNORE_CONSTRAINTS** -Klausel aus. Aktivieren Sie dann den FileTable-Namespace erneut.  
  
 Informationen zum Deaktivieren der FileTable-Einschränkungen finden Sie unter [Verwalten von FileTables](../../relational-databases/blob/manage-filetables.md).  
  
###  <a name="how-to-disable-filetable-constraints-for-bulk-loading"></a><a name="disabling"></a> Vorgehensweise: Deaktivieren von Dateitabellen-Einschränkungen zum Massenladen  
 Um Dateien in einem Massenvorgang in eine FileTable zu laden und dabei den Aufwand zu vermeiden, die systemdefinierten Einschränkungen zu erzwingen, können Sie die Einschränkungen vorübergehend deaktivieren. Weitere Informationen finden Sie unter [Verwalten von FileTables](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf FileTables mit Transact-SQL](../../relational-databases/blob/access-filetables-with-transact-sql.md)   
 [Zugreifen auf FileTables mit Datei-E/A-APIs](../../relational-databases/blob/access-filetables-with-file-input-output-apis.md)  
  
  
