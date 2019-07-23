---
title: 'PDOStatement:: ROWCOUNT | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0569f26a-2376-4c20-8813-bd3c87d0ae9f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a9f6f7045c0729dad4fbb7d2875a645d370a1a5e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935994"
---
# <a name="pdostatementrowcount"></a>PDOStatement::rowCount
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt die Anzahl der Zeilen zurück, die durch die letzte Anweisung hinzugefügt, gelöscht oder geändert wurden  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int PDOStatement::rowCount ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
Die Anzahl der hinzugefügten, gelöschten oder geänderten Zeilen.  
  
## <a name="remarks"></a>Remarks  
Falls die letzte SQL-Anweisung, die durch die zugeordnete PDO-Anweisung ausgeführt wurde, eine SELECT-Anweisung war, gibt ein PDO::CURSOR_FWDONLY-Cursor den Wert -1 zurück. A PDO::CURSOR_SCROLLABLE -Cursor gibt die Anzahl der Zeilen in dem Resultset zurück.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel zeigt zwei Verwendungen von „rowCount“. Die erste gibt die Anzahl der Zeilen zurück, die der Tabelle hinzugefügt wurden. Die zweite Verwendung zeigt, dass „rowCount“ die Anzahl der Zeilen in einem Resultset ausgeben kann, wenn Sie einen bildlauffähigen Cursor spezifizieren.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table2(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
  
echo "\n\n";  
  
$con = null;  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
print $stmt->rowCount();  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
