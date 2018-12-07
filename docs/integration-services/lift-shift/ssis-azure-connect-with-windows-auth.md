---
title: Herstellen einer Verbindung mit Datenquellen und Dateifreigaben mit der Windows-Authentifizierung | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie den SSIS-Katalog in Azure SQL-Datenbank und die Azure SSIS Integration Runtime so konfigurieren, dass er Pakete ausführt, die die Windows-Authentifizierung verwenden, um eine Verbindung mit Datenquellen und Dateifreigaben herzustellen.
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 61d4d29b0dfc7fe67097c6cb61547c1c65dd79f1
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52411877"
---
# <a name="connect-to-data-sources-and-file-shares-with-windows-authentication-from-ssis-packages-in-azure"></a>Herstellen einer Verbindung mit Datenquellen und Dateifreigaben mit der Windows-Authentifizierung über SSIS-Pakete in Azure
Sie können sowohl lokal als auch auf Azure-VMs und in Azure Files die Windows-Authentifizierung verwenden, um eine Verbindung mit Datenquellen und Dateifreigaben im selben virtuellen Netzwerk herzustellen, in dem Ihre Azure SSIS Integration Runtime (IR) ausgeführt wird. Es gibt drei Methoden, um eine Verbindung mit Datenquellen und Dateifreigaben mit der Windows-Authentifizierung über SSIS-Pakete herzustellen, die in der Azure SSIS IR ausgeführt werden:

| Verbindungsmethode | Effektiver Geltungsbereich | Schritt zum Einrichten | Zugriffsmethode in Paketen | Anzahl der Anmeldeinformationssätze und verbundenen Ressourcen | Typ der verbundenen Ressourcen | 
|---|---|---|---|---|---|
| Speicherung von Anmeldeinformationen mit dem Befehl `cmdkey` | Pro Azure SSIS IR | Führen Sie bei der Bereitstellung bzw. Neukonfiguration der Azure SSIS IR (z.B. `cmdkey /add:fileshareserver /user:xxx /pass:yyy`) den Befehl `cmdkey` in einem benutzerdefinierten Setupskript (`main.cmd`) aus.<br/><br/> Weitere Informationen finden Sie unter [Anpassen des Setups für die Azure SSIS IR](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup). | Zugriff auf Ressourcen direkt in Paketen über einen UNC-Pfad (z.B. `\\fileshareserver\folder`) | Unterstützung für mehrere Anmeldeinformationssätze für verschiedene verbundene Ressourcen | – Lokale Dateifreigaben oder Dateifreigaben von Azure-VMs<br/><br/> – Azure Files (siehe [Einbinden einer Azure-Dateifreigabe und Zugreifen auf die Freigabe unter Windows](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows)) <br/><br/> – SQL Server mit der Windows-Authentifizierung<br/><br/> – Andere Ressourcen mit der Windows-Authentifizierung |
| Einrichten eines Ausführungskontexts auf Katalogebene | Pro Azure SSIS IR | Führen Sie die gespeicherte SSISDB-Prozedur `catalog.set_execution_credential` aus, um einen Kontext für „Ausführung als“ einzurichten.<br/><br/> Weitere Informationen finden Sie nachfolgend im weiteren Verlauf dieses Artikels. | Zugriff auf Ressourcen direkt in Paketen | Unterstützung nur für einen Anmeldeinformationssatz für alle verbundenen Ressourcen | – Lokale Dateifreigaben oder Dateifreigaben von Azure-VMs<br/><br/> – Azure Files (siehe [Einbinden einer Azure-Dateifreigabe und Zugreifen auf die Freigabe unter Windows](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows)) <br/><br/> – SQL Server mit der Windows-Authentifizierung<br/><br/> – Andere Ressourcen mit der Windows-Authentifizierung | 
| Einbinden von Laufwerken zur Paketausführungszeit (ohne Persistenz) | Pro Paket | Führen Sie den Befehl `net use` im Task „Prozess ausführen“ aus, der zu Beginn der Ablaufsteuerung in Ihren Paketen (z.B. `net use D: \\fileshareserver\sharename`) hinzugefügt wird. | Zugriff auf Dateifreigaben über zugeordnete Laufwerke | Unterstützung für mehrere Laufwerke für verschiedene Dateifreigaben | – Lokale Dateifreigaben oder Dateifreigaben von Azure-VMs<br/><br/> – Azure Files (siehe [Einbinden einer Azure-Dateifreigabe und Zugreifen auf die Freigabe unter Windows](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows)) |
|||||||

> [!WARNING]
> Wenn Sie keine der oben genannten Methoden verwenden, um eine Verbindung mit Datenquellen und Dateifreigaben herzustellen, können Pakete, die von der Windows-Authentifizierung abhängig sind, keine Verbindung mit diesen herstellen. Zur Laufzeit tritt dann ein Fehler auf. 

Im weiteren Verlauf dieses Artikels wird beschrieben, wie Sie den SSIS-Katalog in Azure SQL-Datenbank zum Ausführen von Paketen konfigurieren, die die Windows-Authentifizierung verwenden, um eine Verbindung mit Datenquellen und Dateifreigaben herzustellen. 

## <a name="you-can-only-use-one-set-of-credentials"></a>Sie können nur einen Satz Anmeldeinformationen verwenden
Wenn Sie Windows-Authentifizierung in einem SSIS-Paket verwenden, können Sie in einem Paket nur einen Satz Anmeldeinformationen verwenden. Die Anmeldeinformationen für die Domäne, die Sie beim Ausführen der in diesem Artikel dargestellten Schritte angeben, gelten solange für alle (interaktiven oder geplanten) Paketausführungen in Ihrer Azure SSIS IR, bis Sie die Anmeldeinformationen ändern oder entfernen. Wenn Ihr Paket eine Verbindung mit mehreren Datenquellen und Dateifreigaben mit verschiedenen Sätzen von Anmeldeinformationen herstellen muss, sollten Sie möglicherweise die oben genannten alternativen Methoden anwenden.

## <a name="provide-domain-credentials-for-windows-authentication"></a>Angeben von Domänenanmeldeinformationen für die Windows-Authentifizierung
Führen Sie die folgenden Schritte durch, um Anmeldeinformationen für die Domäne anzugeben, durch die Pakete anhand der Windows-Authentifizierung eine Verbindung mit lokalen Datenquellen oder Dateifreigaben herstellen können:

1.  Stellen Sie mit SQL Server Management Studio (SSMS) oder einem anderen Tool eine Verbindung mit der SQL-Datenbank her, die die SSIS-Katalogdatenbank (SSISDB) hostet. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SSIS-Katalogdatenbank (SSISDB) in Azure](ssis-azure-connect-to-catalog-database.md).

2.  Öffnen Sie ein Abfragefragefenster mit SSISDB als aktuelle Datenbank.

3.  Führen Sie die folgenden gespeicherten Prozeduren aus, und stellen Sie passende Anmeldeinformationen für die Domäne bereit:

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```

4.  Führen Sie die SSIS-Pakete aus. Die Pakete verwenden die Anmeldeinformationen, die Sie angegeben haben, um eine Verbindung mit den lokalen Datenquellen oder Dateifreigaben mithilfe der Windows-Authentifizierung herzustellen.

### <a name="view-domain-credentials"></a>Anzeigen von Anmeldeinformationen für eine Domäne
Führen Sie die folgenden Schritte aus, um die aktiven Anmeldeinformationen einer Domäne anzuzeigen:

1.  Stellen Sie mit SQL Server Management Studio (SSMS) oder einem anderen Tool eine Verbindung mit der SQL-Datenbank her, die die SSIS-Katalogdatenbank (SSISDB) hostet.

2.  Öffnen Sie ein Abfragefragefenster mit SSISDB als aktuelle Datenbank.

3.  Führen Sie die folgende gespeicherte Prozedur aus, und überprüfen Sie die Ausgabe:

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>Löschen von Anmeldeinformationen für eine Domäne
Führen Sie die folgenden Schritte aus, um die Anmeldeinformationen, die Sie angegeben haben, wie in diesem Artikel beschrieben, zu löschen und zu entfernen:

1.  Stellen Sie mit SQL Server Management Studio (SSMS) oder einem anderen Tool eine Verbindung mit der SQL-Datenbank her, die die SSIS-Katalogdatenbank (SSISDB) hostet.

2.  Öffnen Sie ein Abfragefragefenster mit SSISDB als aktuelle Datenbank.

3.  Führen Sie die folgende gespeicherte Prozedur aus:

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-an-on-premises-sql-server"></a>Herstellen einer Verbindung zu einer lokalen SQL Server-Instanz
Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie eine Verbindung mit einem lokalen SQL Server herstellen können:

1.  Suchen Sie einen Computer, der nicht in eine Domäne eingebunden ist, um diesen Test auszuführen.

2.  Führen Sie auf dem Computer, der nicht in eine Domäne eingebunden ist, folgenden Befehl aus, um SQL Server Management Studio (SSMS) mit den Anmeldeinformationen für die Domäne zu starten, die Sie verwenden möchten:

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  Überprüfen Sie über SSMS, ob Sie eine Verbindung mit dem lokalen SQL Server herstellen können, den Sie verwenden möchten.

### <a name="prerequisites"></a>Voraussetzungen
Um eine Verbindung mit einer lokalen SQL Server-Instanz von einem Paket aus herzustellen, das unter Azure ausgeführt wird, müssen Sie die folgenden Voraussetzungen erfüllen:

1.  Aktivieren Sie in SQL Server-Konfigurations-Manager das TCP/IP-Protokoll.
2.  Lassen Sie den Zugriff über die Windows-Firewall zu. Weitere Informationen finden Sie unter [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](https://docs.microsoft.com/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access).
3.  Stellen Sie sicher, dass Ihre Azure SSIS IR zu einem virtuellen Netzwerk gehört, das auch die lokale Instanz von SQL Server enthält, um eine Verbindung mit der Windows-Authentifizierung herzustellen.  Weitere Informationen finden Sie unter [Verknüpfen einer Azure SSIS Integration Runtime mit einem virtuellen Netzwerk](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network). Verwenden Sie dann `catalog.set_execution_credential`, um Anmeldeinformationen wie in diesem Artikel beschrieben bereitzustellen.

## <a name="connect-to-an-on-premises-file-share"></a>Herstellen einer Verbindung zu einer lokalen Dateifreigabe
Führen Sie die folgenden Schritte durch, um zu testen, ob Sie eine Verbindung mit einer lokalen Dateifreigabe herstellen können:

1.  Suchen Sie einen Computer, der nicht in eine Domäne eingebunden ist, um diesen Test auszuführen.

2.  Führen Sie den folgenden Befehl auf dem Computer aus, der nicht in eine Domäne eingebunden ist. Über diesen Befehl öffnen Sie zunächst ein Eingabeaufforderungsfenster mit den Anmeldeinformationen der Domäne, die Sie verwenden möchten, und testen dann die Konnektivität mit der Dateifreigabe, indem Sie eine Verzeichnisliste abrufen.

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  Überprüfen Sie, ob die Verzeichnisliste für die lokale Dateifreigabe zurückgegeben wird, die Sie verwenden möchten.

## <a name="connect-to-a-file-share-on-an-azure-vm"></a>Herstellen einer Verbindung zu einer Dateifreigabe auf einer Azure-VM
Führen Sie die folgenden Schritte durch, um eine Verbindung mit einer Dateifreigabe auf einer Azure-VM herzustellen:

1.  Stellen Sie mit SQL Server Management Studio (SSMS) oder einem anderen Tool eine Verbindung mit der SQL-Datenbank her, die die SSIS-Katalogdatenbank (SSISDB) hostet.

2.  Öffnen Sie ein Abfragefragefenster mit SSISDB als aktuelle Datenbank.

3.  Führen Sie die gespeicherte Prozedur `catalog.set_execution_credential` aus, wie in den folgenden Optionen beschrieben:

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="connect-to-a-file-share-in-azure-files"></a>Herstellen einer Verbindung mit einer Dateifreigabe in Azure Files
Weitere Informationen zu Azure Files finden Sie unter [Azure Files](https://azure.microsoft.com/services/storage/files/).

Führen Sie die folgenden Schritte durch, um eine Verbindung mit einer Dateifreigabe in Azure Files herzustellen:

1.  Stellen Sie mit SQL Server Management Studio (SSMS) oder einem anderen Tool eine Verbindung mit der SQL-Datenbank her, die die SSIS-Katalogdatenbank (SSISDB) hostet.

2.  Öffnen Sie ein Abfragefragefenster mit SSISDB als aktuelle Datenbank.

3.  Führen Sie die gespeicherte Prozedur `catalog.set_execution_credential` aus, wie in den folgenden Optionen beschrieben:

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>Nächste Schritte
- Stellen Sie ein Paket bereit. Weitere Informationen finden Sie unter [Deploy an SSIS project with SQL Server Management Studio (SSMS) (Bereitstellen eines SSIS-Projekts mit SQL Server Management Studio (SSMS))](../ssis-quickstart-deploy-ssms.md).
- Führen Sie ein Paket aus. Weitere Informationen finden Sie unter [Run an SSIS package with SQL Server Management Studio (SSMS) (Ausführen eines SSIS-Pakets mit SQL Server Management Studio (SSMS))](../ssis-quickstart-run-ssms.md).
- Planen Sie ein Paket. Weitere Informationen finden Sie unter [Planen der Ausführung eines SSIS-Pakets in Azure](ssis-azure-schedule-packages.md).
