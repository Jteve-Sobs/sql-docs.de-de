---
title: PDOStatement::errorInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e45bebe8-ea4c-49b6-93db-cf1ae65f530c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15686a93c5e23a476968332479897d2fb5b90220
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67993071"
---
# <a name="pdostatementerrorinfo"></a>PDOStatement::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft erweiterte Fehlerinformationen des zuletzt ausgeführten Vorgangs des Anweisungshandles ab  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array PDOStatement::errorInfo();  
```  
  
## <a name="return-value"></a>Rückgabewert  
Ein Array mit Fehlerinformationen über den zuletzt ausgeführten Vorgang des Anweisungshandles Dieses Array besteht aus den folgenden Feldern:  
  
-   Der SQLSTATE-Fehlercode  
  
-   Der treiberspezifische Fehlercode  
  
-   Die treiberspezifische Fehlermeldung  
  
Wenn kein Fehler vorliegt oder wenn der SQLSTATE nicht festgelegt ist, werden die treiberspezifischen Felder NULL sein.  
  
## <a name="remarks"></a>Bemerkungen  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
In diesem Beispiel ist in der SQL-Anweisung ein Fehler aufgetreten, der dann gemeldet wird.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print_r ($stmt->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
