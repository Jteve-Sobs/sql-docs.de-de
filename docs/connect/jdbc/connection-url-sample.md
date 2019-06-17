---
title: Verbindungs-URL-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 96fabc42-59d1-4cc0-93c5-db00cbe55e95
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f13f175dc6f50818b5eef6b142f4d211103a4b3c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803156"
---
# <a name="connection-url-sample"></a>Verbindungs-URL - Beispiel

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Diese Beispielanwendung für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] veranschaulicht, wie unter Verwendung einer Verbindungs-URL eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank hergestellt wird. Darüber hinaus wird gezeigt, wie Daten mithilfe einer SQL-Anweisung aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank abgerufen werden.

Die Codedatei für dieses Beispiel heißt „ConnectURL.java“ und befindet sich im folgenden Pfad:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\connections
```

## <a name="requirements"></a>Anforderungen

Wenn Sie diese Beispielanwendung ausführen möchten, müssen Sie die Datei „mssql-jdbc.jar“ in den Klassenpfad aufnehmen. Sie benötigen darüber hinaus Zugriff auf die [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank. Weitere Informationen zum Festlegen des Klassenpfads finden Sie unter [mit dem JDBC-Treiber](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] enthält die Klassenbibliotheksdateien „mssql-jdbc“ für die jeweilige Verwendung mit Ihren bevorzugten JRE-Einstellungen (Java Runtime Environment). Weitere Informationen zum Auswählen der richtigen JAR-Datei finden Sie unter [Systemanforderungen für den JDBC-Treiber](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Beispiel

Im folgenden Beispielcode werden verschiedene Verbindungseigenschaften für die Verbindungs-URL festgelegt. Anschließend wird die Methode „getConnection“ der Klasse „DriverManager“ aufgerufen, um ein [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt zurückzugeben.

Danach wird mithilfe der [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)-Methode des SQLServerConnection-Objekts ein [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt erstellt. Anschließend wird die [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md)-Methode aufgerufen, um die SQL-Anweisung auszuführen.

Schließlich wird das von der Methode executeQuery zurückgegebene [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt verwendet, um die von der SQL-Anweisung zurückgegebenen Ergebnisse zu durchlaufen.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class ConnectURL {
    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=AdventureWorks;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement();) {
            String SQL = "SELECT TOP 10 * FROM Person.Contact";
            ResultSet rs = stmt.executeQuery(SQL);

            // Iterate through the data in the result set and display it.
            while (rs.next()) {
                System.out.println(rs.getString("FirstName") + " " + rs.getString("LastName"));
            }
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen

[Verbinden und Abrufen von Daten](../../connect/jdbc/connecting-and-retrieving-data.md)
