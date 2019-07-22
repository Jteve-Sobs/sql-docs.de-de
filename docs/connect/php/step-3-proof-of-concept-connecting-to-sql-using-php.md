---
title: 'Schritt 3: Proof of Concept für Verbindungen mit SQL Server mithilfe von PHP | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a7451a85-18e5-4fd0-bbcb-2f15a1117290
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d685c15b4cc30dc093a47b37e6bfc29368e91f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68014798"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-php"></a>Schritt 3: Machbarkeitsnachweis für Verbindungen mit SQL mithilfe von PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="step-1--connect"></a>Schritt 1: verbinden  
  
  
Diese **OpenConnection** -Funktion wird in allen folgenden Funktionen in der Nähe des oberen Aufrufs aufgerufen.  
  
  
```php 
    function OpenConnection()  
    {  
        try  
        {  
            $serverName = "tcp:myserver.database.windows.net,1433";  
            $connectionOptions = array("Database"=>"AdventureWorks",  
                "Uid"=>"MyUser", "PWD"=>"MyPassword");  
            $conn = sqlsrv_connect($serverName, $connectionOptions);  
            if($conn == false)  
                die(FormatErrors(sqlsrv_errors()));  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-2--execute-query"></a>Schritt 2: Ausführen der Abfrage  
  
Die [sqlsrv_query ()](https://php.net/manual/en/function.sqlsrv-query.php) -Funktion kann verwendet werden, um ein Resultset aus einer Abfrage für die SQL-Datenbank abzurufen. Diese Funktion akzeptiert im Wesentlichen alle Abfragen und das Verbindungs Objekt und gibt ein Resultset zurück, das mit der Verwendung von [sqlsrv_fetch_array ()](https://php.net/manual/en/function.sqlsrv-fetch-array.php)durchlaufen werden kann.  
  
```php  
    function ReadData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
            $tsql = "SELECT [CompanyName] FROM SalesLT.Customer";  
            $getProducts = sqlsrv_query($conn, $tsql);  
            if ($getProducts == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
            $productCount = 0;  
            while($row = sqlsrv_fetch_array($getProducts, SQLSRV_FETCH_ASSOC))  
            {  
                echo($row['CompanyName']);  
                echo("<br/>");  
                $productCount++;  
            }  
            sqlsrv_free_stmt($getProducts);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
  
## <a name="step-3--insert-a-row"></a>Schritt 3: Einfügen einer Zeile  
  
In diesem Beispiel erfahren Sie, wie Sie eine [Insert](../../t-sql/statements/insert-transact-sql.md) -Anweisung sicher ausführen, Parameter übergeben, die Ihre Anwendung vor dem SQL- [einschleusungs](../../relational-databases/tables/primary-and-foreign-key-constraints.md) Wert schützen.    
  
  
```php 
    function InsertData()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            $tsql = "INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate) OUTPUT            INSERTED.ProductID VALUES ('SQL Server 1', 'SQL Server 2', 0, 0, getdate())";  
            //Insert query  
            $insertReview = sqlsrv_query($conn, $tsql);  
            if($insertReview == FALSE)  
                die(FormatErrors( sqlsrv_errors()));  
            echo "Product Key inserted is :";  
            while($row = sqlsrv_fetch_array($insertReview, SQLSRV_FETCH_ASSOC))  
            {     
                echo($row['ProductID']);  
            }  
            sqlsrv_free_stmt($insertReview);  
            sqlsrv_close($conn);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="step-4--rollback-a-transaction"></a>Schritt 4: Rollback einer Transaktion  
  
  
Dieses Codebeispiel veranschaulicht die Verwendung von Transaktionen, in denen Sie folgende Vorgänge ausführen:  
  
-Begin a Transaction  
  
-Einfügen einer Zeile mit Daten, Aktualisieren einer anderen Daten Zeile  
  
-Committen Sie die Transaktion, wenn die INSERT-und Update-Vorgänge erfolgreich ausgeführt wurden, und führen Sie ein Rollback der Transaktion aus, wenn  
  
  
```php 
    function Transactions()  
    {  
        try  
        {  
            $conn = OpenConnection();  
  
            if (sqlsrv_begin_transaction($conn) == FALSE)  
                die(FormatErrors(sqlsrv_errors()));  
  
            $tsql1 = "INSERT INTO SalesLT.SalesOrderDetail (SalesOrderID,OrderQty,ProductID,UnitPrice)  
            VALUES (71774, 22, 709, 33)";  
            $stmt1 = sqlsrv_query($conn, $tsql1);  
  
            /* Set up and execute the second query. */  
            $tsql2 = "UPDATE SalesLT.SalesOrderDetail SET OrderQty = (OrderQty + 1) WHERE ProductID = 709";  
            $stmt2 = sqlsrv_query( $conn, $tsql2);  
  
            /* If both queries were successful, commit the transaction. */  
            /* Otherwise, rollback the transaction. */  
            if($stmt1 && $stmt2)  
            {  
                   sqlsrv_commit($conn);  
                   echo("Transaction was commited");  
            }  
            else  
            {  
                sqlsrv_rollback($conn);  
                echo "Transaction was rolled back.\n";  
            }  
            /* Free statement and connection resources. */  
            sqlsrv_free_stmt( $stmt1);  
            sqlsrv_free_stmt( $stmt2);  
        }  
        catch(Exception $e)  
        {  
            echo("Error!");  
        }  
    }  
```  
  
## <a name="additional-examples"></a>Zusätzliche Beispiele  
  
[Beispielanwendung (SQLSRV-Treiber)](../../connect/php/example-application-sqlsrv-driver.md)  

[Beispielanwendung (PDO_SQLSRV-Treiber)](../../connect/php/example-application-pdo-sqlsrv-driver.md)
