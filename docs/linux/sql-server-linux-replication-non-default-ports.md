---
title: Konfigurieren von SQL Server-Replikation momentaufnahmefreigaben Ordner unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie SQLServer-Replikation von Momentaufnahmen Ordner Freigaben unter Linux konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4fd7c819af4c700af17a4b85fad2a4cc75e3e820
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705133"
---
# <a name="configure-replication-with-non-default-ports"></a>Konfigurieren der Replikation mit nicht standardmäßigen ports

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie können mit SQL Server auf Linux-Instanzen Lauschen an einem beliebigen Port konfiguriert werden, mit der Mssql-Conf-Einstellung network.tcpport Replikation konfigurieren. Der Port muss, um den Namen des Servers während der Konfiguration angefügt werden soll, wenn die folgenden Bedingungen erfüllt sind:

1. Einrichten der Replikation umfasst eine Instanz von SQL Server unter Linux
2. Jede Instanz (Windows oder Linux) lauscht an einem nicht standardmäßigen Port. 

Der Servername einer Instanz von ausgeführt wird, @ finden@servername auf der Instanz.

## <a name="examples"></a>Beispiele

"Server1" lauscht an Port 1500 für Linux. Führen Sie zum Konfigurieren von "Server1" für die Verteilung `sp_adddistributor` mit `@distributor`. Zum Beispiel: 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

"Server1" lauscht an Port 1500 für Linux. Um einen Verleger für den Verteiler konfigurieren, führen Sie `sp_adddistpublisher` mit `@publisher`. Zum Beispiel:

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

"Server2" Lauscht auf Port 6549 unter Linux. Führen Sie zum Konfigurieren von "Server2" als einen Abonnenten `sp_addsubscription` mit `@subscriber`. Zum Beispiel:

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

"Server3" Lauscht auf Port 6549 auf Windows, die mit Server3 Servernamen und Instanznamen des MSSQL2017. Um "Server3" als einen Abonnenten zu konfigurieren, führen die `sp_addsubscription` mit `@subscriber`. Zum Beispiel:

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>Nächste Schritte

[Konzepte: SQL Server-Replikation unter Linux](sql-server-linux-replication.md)

[Gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

