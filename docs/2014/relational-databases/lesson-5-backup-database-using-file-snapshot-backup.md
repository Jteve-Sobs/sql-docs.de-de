---
title: 'Lektion 6: Migrieren einer Datenbank aus einer Quelle lokalen zu einem Zielcomputer in Windows Azure | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: d9134ade-7b03-4c5c-8ed3-3bc369a61691
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 46d4018e125633319ed6d235873f56720fbe6bc2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743321"
---
# <a name="lesson-6-migrate-a-database-from-a-source-machine-on-premises-to-a-destination-machine-in-windows-azure"></a>Lektion 6: Migrieren einer Datenbank aus einer Quelle lokalen zu einem Zielcomputer in Windows Azure
  In dieser Lektion wird davon ausgegangen, dass bereits ein weiterer SQL Server vorhanden ist, der sich auf einem anderen lokalen Computer oder auf einem virtuellen Computer in Windows Azure befindet. Informationen zum Erstellen eines SQL Server-Computers in Windows Azure finden Sie unter [eine SQL Server-Computer in Windows Azure-Bereitstellung](http://www.windowsazure.com/manage/windows/common-tasks/install-sql-server/). Nachdem Sie einen virtuellen SQL Server-Computer in Windows Azure bereitgestellt haben, überprüfen Sie, ob Sie eine Verbindung mit einer SQL Server-Instanz auf diesem virtuellen Computer über SQL Server Management Studio auf einem anderen Computer herstellen können.  
  
 In dieser Lektion wird auch davon ausgegangen, dass Sie bereits die folgenden Schritte abgeschlossen haben:  
  
-   Sie verfügen über ein Windows Azure-Speicherkonto.  
  
-   Sie haben einen Container über Ihr Windows Azure-Speicherkonto erstellt.  
  
-   Sie haben eine Richtlinie in einem Container mit Lese-, Schreib- und Auflistungsrechten erstellt. Sie haben auch einen SAS-Schlüssel generiert.  
  
-   Sie haben die SQL Server-Anmeldeinformationen auf dem Quellcomputer erstellt.  
  
-   Sie haben bereits einen virtuellen SQL Server-Zielcomputer in Windows Azure erstellt. Es wird empfohlen, dass Sie diesen erstellen, indem Sie ein Plattformimage mit SQL Server 2014 auswählen.  
  
 Um eine Datenbank lokal von SQL Server zu einem anderen virtuellen Computer in Windows Azure zu migrieren, können Sie folgende Schritte ausführen:  
  
1.  Öffnen Sie auf dem Quellcomputer (in diesem Lernprogramm ein lokaler Computer) ein Abfragefenster in SQL Server Management Studio. Trennen Sie die Datenbank, um sie auf einen anderen Computer zu verschieben, indem Sie folgende Anweisungen ausführen:  
  
    ```  
    -- Detach the database in the source machine   
    USE master  
    EXEC sp_detach_db 'TestDB1', 'true';  
    ```  
  
2.  Wenn Sie eine Datenbank auf einen Zielcomputer übertragen müssen, müssen Sie ihn zunächst vorbereiten. Um den Zielcomputer vorzubereiten, müssen Sie zunächst SQL Server-Anmeldeinformationen auf dem Zielcomputer erstellen. Wenn es sich um eine verschlüsselte Datenbank handelt, müssen Sie auch das Zertifikat vom Quellcomputer auf den Zielcomputer importieren.  
  
    1.  Um SQL Server-Anmeldeinformationen auf dem Zielcomputer zu erstellen, führen Sie folgende Schritte aus:  
  
        1.  Stellen Sie eine Verbindung zum Zielcomputer über SQL Server Management Studio auf dem Quellcomputer her.  Oder starten Sie SQL Server Management Studio direkt auf dem Zielcomputer.  
  
        2.  Klicken Sie auf der Standardsymbolleiste auf **neue Abfrage**.  
  
        3.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf. Die folgende Anweisung erstellt SQL Server-Anmeldeinformationen zum Speichern des Zertifikats für Ihren Speichercontainers freigegebenen Zugriff.  
  
            ```sql  
  
            USE master   
            GO   
            CREATE CREDENTIAL [http://teststorageaccnt.blob.core.windows.net/testcontainer]   
            WITH IDENTITY='SHARED ACCESS SIGNATURE',   
            SECRET = 'your SAS key'   
            GO  
  
            ```  
  
        4.  Um alle verfügbaren Anmeldeinformationen anzuzeigen, können Sie im Abfragefenster die folgende Anweisung ausführen:  
  
            ```sql  
            SELECT * from sys.credentials   
            ```  
  
        5.  Wenn Sie mit dem Zielserver verbunden sind, öffnen Sie das Abfragefenster, und führen Sie Folgendes aus:  
  
            ```sql  
  
            -- Create a master key and a server certificate   
            USE master   
            GO   
            CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'MySQLKey01'; -- You may use a different password.   
            GO   
            CREATE CERTIFICATE MySQLCert   
            FROM FILE = 'C:\certs\MySQLCert.CER'   
            WITH PRIVATE KEY   
            (   
            FILE = 'C:\certs\MySQLPrivateKeyFile.PVK',   
            DECRYPTION BY PASSWORD = 'MySQLKey01'   
            );   
            GO  
  
            ```  
  
             Am Ende dieses Schritts wird das vom Quellcomputer kopierte Verschlüsselungszertifikat vom Zielcomputer importiert. Anschließend können Sie die Datendateien auf dem Zielcomputer anfügen.  
  
    2.  Erstellen Sie dann eine Datenbank mit Daten und Protokolldateien, die auf vorhandene Dateien im Windows Azure-Speicher verweisen. Verwenden Sie dazu die Option FOR ATTACH. Führen Sie die folgende Anweisung im Abfragefenster aus:  
  
        ```sql  
  
        --Create a database on the destination server   
        CREATE DATABASE TestDB1onDest   
        ON   
        (NAME = TestDB1_data,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Data.mdf' )   
        LOG ON   
         (NAME = TestDB1_log,   
            FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontainer/TestDB1Log.ldf')   
        FOR ATTACH   
        GO  
  
        ```  
  
    3.  Klicken Sie im Objekt-Explorer auf "Datenbanken" und mit der rechten Maustaste auf "Aktualisieren". Sie sollten die neu erstellte Datenbank "TestDB1onDest" anzeigen können.  
  
    4.  Führen Sie als Nächstes die folgende Anweisung im Abfragefenster aus:  
  
        ```sql  
  
        USE TestDB1onDest   
        SELECT * FROM Table1;   
        GO  
  
        ```  
  
         Es sollten alle Daten aufgelistet werden, die Sie in Lektion 4 eingegeben haben.  
  
 Beachten Sie, dass die verschlüsselte Datenbank ohne Datenverschiebung auf eine andere Berechnungsinstanz übertragen wurde.  
  
 Um über die SQL Server Management Studio-Benutzeroberfläche eine Datenbank mit Daten und Protokolldateien zu erstellen, die auf vorhandene Dateien im Windows Azure-Speicher verweisen, führen Sie die folgenden Schritte aus:  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz der SQL Server-Datenbank-Engine her, und erweitern Sie anschließend diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie dann auf **Neue Datenbank**. Klicken Sie anschließend mit der rechten Maustaste auf "TestDB". Klicken Sie auf "Tasks" und dann auf "Trennen". Prüfen Sie "Verbindungen löschen" im Dialogfeld "Trennen". Klicken Sie auf **OK**.  
  
3.  Stellen Sie eine Verbindung mit einem Zielcomputer her, der SQL Server 2014 CTP2 oder höher aufweist. Um den Zielcomputer vorzubereiten, müssen Sie SQL Server-Anmeldeinformationen auf dem Zielcomputer erstellen, um auf den gleichen Container zu verweisen, in dem sich TestDB1 befindet. Wenn Sie den erneuten Anfügevorgang auf dem gleichen Computer durchführen, ist es nicht erforderlich, andere Anmeldeinformationen zu erstellen.  
  
4.  In **Objekt-Explorer**, mit der rechten Maustaste **Datenbanken** , und klicken Sie auf **Anfügen**.  
  
5.  In der **Datenbanken anfügen** Dialogfeld Geben Sie die Datenbank angefügt werden, klicken Sie auf **hinzufügen**. In der **Datenbankdateien** Dialogfeld:  
  
     Geben Sie für die Datenbankdatendatei,: `https://teststorageaccnt.blob.core.windows.net/testcontainer/`.  
  
     Geben Sie für Dateinamen: `TestDB1Data.mdf`.  
  
6.  Klicken Sie auf **OK**.  
  
     ![SQL 14 CTP2](../tutorials/media/ss-was-tutlesson-6-7.gif "SQL 14 CTP2")  
  
 **Nächste Lektion:**  
  
 [Lektion 7: Verschieben von Datendateien in Microsoft Azure Storage](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)  
  
  
