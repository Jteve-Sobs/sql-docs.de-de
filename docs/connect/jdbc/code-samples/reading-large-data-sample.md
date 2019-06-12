---
title: Beispiel zum Lesen großer Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8fe0e62d12f9bb7f4336e338c4d6594d9a94268e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66770016"
---
# <a name="reading-large-data-sample"></a>Beispiel zum Lesen umfangreicher Daten

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] veranschaulicht, wie ein großer Wert in einer Spalte mithilfe der [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)-Methode aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank abgerufen wird.

Die Codedatei für dieses Beispiel heißt „ReadLargeData.java“ und befindet sich unter folgendem Pfad:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Anforderungen

Zum Ausführen dieser Beispielanwendung benötigen Sie Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Nehmen Sie außerdem die Datei „mssql-jdbc.jar“ in den Klassenpfad auf. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zum Auswählen der richtigen JAR-Datei finden Sie unter [Systemanforderungen für den JDBC-Treiber](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Beispiel

Im folgenden Beispielcode wird eine Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Datenbank hergestellt. Im Beispielcode werden anschließend Beispieldaten erstellt, und die Tabelle Production.Document wird mithilfe einer parametrisierten Abfrage aktualisiert.

Außerdem wird im Beispielcode veranschaulicht, wie der Modus für die adaptive Pufferung mithilfe der Methode [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) der Klasse [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) abgerufen wird. Beachten Sie, dass ab Version 2.0 des JDBC-Treibers die responseBuffering-Verbindungseigenschaft standardmäßig auf "adaptive" festgelegt ist.

Anschließend wird im Beispielcode eine SQL-Anweisung mit dem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt verwendet. Die SQL-Anweisung wird ausgeführt, und die zurückgegebenen Daten werden in ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt eingefügt.

Schließlich durchläuft der Beispielcode die Datenzeilen im Resultset und greift mithilfe der [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)-Methode auf einige der Daten zu.

[!code[JDBC#UsingAdaptiveBuffering1](../../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit umfangreichen Daten](../../../connect/jdbc/code-samples/working-with-large-data.md)
