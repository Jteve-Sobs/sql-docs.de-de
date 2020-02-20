---
title: Verwenden von Sicherungspunkten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d860e368fe66ce926687fd343fe9f23704cfc7d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026130"
---
# <a name="using-savepoints"></a>Verwenden von Sicherungspunkten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Sicherungspunkte bieten einen Mechanismus, um für Teile einer Transaktion ein Rollback auszuführen. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie mit der Anweisung „SAVE TRANSACTION Sicherungspunktname“ einen Sicherungspunkt erstellen. Später können Sie die Anweisung "ROLLBACK TRANSACTION Sicherungspunktname" ausführen, um ein Rollback bis zum Sicherungspunkt auszuführen, anstatt ein Rollback bis zum Beginn der Transaktion auszuführen.

Sicherungspunkte sind in Situationen von Nutzen, wenn die Wahrscheinlichkeit gering ist, dass Fehler auftreten. Die Verwendung eines Sicherungspunkts, um für einen Teil einer Transaktion im Falle eines seltenen Fehlers einen Rollback auszuführen, kann effizienter sein, als jede Transaktion vor dem Ausführen einer Aktualisierung daraufhin testen zu lassen, ob die Aktualisierung gültig ist. Aktualisierungen und Rollbacks sind kostspielige Operationen. Sicherungspunkte sind also nur dann effektiv, wenn die Wahrscheinlichkeit eines Fehlers gering und die Kosten für die Vorabüberprüfung der Gültigkeit einer Aktualisierung relativ hoch sind.

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] unterstützt die Verwendung von Sicherungspunkten über die [setSavepoint](../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)-Methode der [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Klasse. Mit der setSavepoint-Methode können Sie in der aktuellen Transaktion einen benannten oder unbenannten Sicherungspunkt erstellen. Die Methode gibt ein [SQLServerSavepoint](../../connect/jdbc/reference/sqlserversavepoint-class.md)-Objekt zurück. In einer Transaktion können mehrere Sicherungspunkte erstellt werden. Um ein Rollback einer Transaktion bis zu einem bestimmten Sicherungspunkt auszuführen, können Sie das SQLServerSavepoint-Objekt an die [rollback-Methode (java.sql.Savepoint)](../../connect/jdbc/reference/rollback-method-java-sql-savepoint.md) übergeben.

Im folgenden Beispiel wird beim Ausführen einer lokalen Transaktion mit zwei getrennten Anweisungen ein Sicherungspunkt im `try`-Block verwendet. Die Anweisungen werden für die Production.ScrapReason-Tabelle in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank ausgeführt. Für den Rollback der zweiten Anweisung wird ein Sicherungspunkt verwendet. Dies führt dazu, dass nur für die erste Anweisung ein Commit in der Datenbank ausgeführt wird.

[!code[JDBC#UsingSavepoints1](../../connect/jdbc/codesnippet/Java/using-savepoints_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Ausführen von Transaktionen mit dem JDBC-Treiber](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)
