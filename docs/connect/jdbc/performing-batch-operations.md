---
title: Ausführen von Batchvorgängen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1a576d95-7da6-4b7b-8b32-59e5b4d354c4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4923354c5f6dc013d9fee0284279bb5b6b887556
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801818"
---
# <a name="performing-batch-operations"></a>Ausführen von Batchvorgängen
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Um die Leistung bei mehreren Updates einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zu verbessern, bietet [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die Möglichkeit, mehrere Updates als einzelne Arbeitseinheit (auch Batch genannt) zu übermitteln.  
  
 Zum Übermitteln von Batchupdates können die Klassen [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) und [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) verwendet werden. Mit der [addBatch](../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)-Methode können Sie einen Befehl hinzufügen. Mit der [clearBatch](../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md)-Methode können Sie die Liste der Befehle löschen. Mit der [executeBatch](../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md)-Methode können Sie alle zu verarbeitenden Befehle übermitteln. In einem Batch können nur DDL- (Data Definition Language) und DML-Anweisungen (Data Manipulation Language) ausgeführt werden, die eine einfache Updatezählung zurückgeben.  
  
 Die executeBatch-Methode gibt ein Array mit **ganzzahligen** Werten zurück, die der Updatezählung der einzelnen Befehle entsprechen. Wenn Sie einen der Befehle fehlschlägt, eine BatchUpdateException ausgelöst, und verwenden Sie die GetUpdateCounts-Methode der-Klasse BatchUpdateException das Update Array mit updatezählungen abrufen. Wenn ein Befehl fehlschlägt, wird die Verarbeitung der restlichen Befehle vom Treiber fortgesetzt. Wenn ein Befehl einen Syntaxfehler enthält, schlagen die Anweisungen im Batch allerdings fehl.  
  
> [!NOTE]  
>  Wenn keine Updatezählungen verwendet werden müssen, können Sie zuerst eine SET NOCOUNT ON-Anweisung an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeben. Dadurch wird das Verkehrsaufkommen im Netzwerk verringert und zusätzlich die Leistung der Anwendung verbessert.  
  
 Erstellen Sie als Beispiel die folgende Tabelle in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank:  
  
```sql
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 Im folgenden Beispiel wird eine offene Verbindung zur [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]-Beispieldatenbank an die Funktion übergeben, mit der addBatch-Methode werden die auszuführenden Anweisungen erstellt, und die executeBatch-Methode wird aufgerufen, um den Batch an die Datenbank zu übermitteln.  
  
```java
public static void executeBatchUpdate(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('X', 100)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Y', 200)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Z', 300)");  
      int[] updateCounts = stmt.executeBatch();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Anweisungen mit dem JDBC-Treiber](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
