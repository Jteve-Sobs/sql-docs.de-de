---
title: Installieren von SQL Server-Agent unter Linux
description: Dieser Artikel beschreibt, wie Sie SQL Server-Agent für Linux zu installieren.
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: c27a31a5e6b9ed771df82e942087d7be88270038
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032468"
---
# <a name="install-sql-server-agent-on-linux"></a>Installieren von SQL Server-Agent unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 Der [SQL Server-Agent](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) führt geplante SQL Server-Aufträge aus. Ab SQL Server 2017 CU4, SQL Server-Agent ist im Lieferumfang der **Mssql-Server** Packen und ist standardmäßig deaktiviert. Weitere Informationen zu den Features, die für diese Version von SQL Server-Agent zusammen mit Informationen zu Versionen unterstützt, finden Sie unter den [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md).

 Installieren/Aktivieren von SQL Server-Agent:
- [Aktivieren Sie für Versionen 2017 CU4 und höher SQL Server-Agent](#EnableAgentAfterCU4)
- [Installieren Sie für Versionen 2017 CU3 und darunter, SQL Server-Agent](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">Aktivieren Sie für Versionen 2017 CU4 und höher SQL Server-Agent</a>

 Um SQL Server-Agent zu aktivieren, führen Sie die folgenden Schritte aus.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Wenn Sie ein von 2017 CU3 Upgrade oder unten mit Agent installiert ist, SQL Server-Agent wird automatisch aktiviert und dem vorherigen, Agent-Pakete werden deinstalliert.  

## <a name="InstallAgentBelowCU4">Installieren Sie für Versionen 2017 CU3 und darunter, SQL Server-Agent</a>

> [!NOTE]
> Die nachfolgenden installationsanweisungen gelten für SQL Server-Versionen 2017 CU3 und niedriger. Vor der Installation von SQL Server-Agent zuerst [Installieren von SQL Server](sql-server-linux-setup.md#platforms). Auf diese Weise werden die Schlüssel und Repositorys konfiguriert, die bei der Installation des **mssql-server-agent**-Pakets verwendet werden.

Installieren Sie SQL Server-Agent für Ihre Plattform:
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">Installation unter RHEL</a>

Gehen Sie wie folgt vor, um **mssql-server-agent** unter Red Hat Enterprise Linux zu installieren. 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

Falls **mssql-server-agent** bereits installiert ist, können Sie mit den folgenden Befehlen auf die neueste Version aktualisieren:

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

Falls Sie eine Offline-Installation durchführen möchten, finden Sie den Downloadlink für das SQL Server-Agent-Paket in den [Anmerkungen zur Version](sql-server-linux-release-notes.md). Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

### <a name="ubuntu">Installation unter Ubuntu</a>

Gehen Sie wie folgt vor, um **mssql-server-agent** unter Ubuntu zu installieren. 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Falls **mssql-server-agent** bereits installiert ist, können Sie mit den folgenden Befehlen auf die neueste Version aktualisieren:

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Falls Sie eine Offline-Installation durchführen möchten, finden Sie den Downloadlink für das SQL Server-Agent-Paket in den [Anmerkungen zur Version](sql-server-linux-release-notes.md). Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

### <a name="SLES">Installation unter SLES</a>

Gehen Sie wie folgt vor, um **mssql-server-agent** unter SUSE Linux Enterprise Server zu installieren. 

Installieren Sie **Mssql-Server-Agent** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

Falls **mssql-server-agent** bereits installiert ist, können Sie mit den folgenden Befehlen auf die neueste Version aktualisieren:

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

Falls Sie eine Offline-Installation durchführen möchten, finden Sie den Downloadlink für das SQL Server-Agent-Paket in den [Anmerkungen zur Version](sql-server-linux-release-notes.md). Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zum Erstellen, Planen und Ausführen von Aufträgen mithilfe des SQL Server-Agents finden Sie unter [„Erstellen und Ausführen von SQL Server-Agent-Aufträgen unter Linux“](sql-server-linux-run-sql-server-agent-job.md).
