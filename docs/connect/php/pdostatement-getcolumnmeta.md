---
title: 'Pdostatement:: Getcolumnmeta | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 57bc8d1e6112a64f99864ce08f7adb81db6df781
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799117"
---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft die Metadaten für eine Spalte ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>Parameter  
*$conn* (ganze Zahl): Die nullbasierte Nummer der Spalte, deren Metadaten Sie abrufen möchten.  
  
## <a name="return-value"></a>Rückgabewert  
Ein assoziatives Array (Schlüssel und Wert), das die Metadaten für die Spalte enthält. Im Abschnitt „Anmerkungen“ finden Sie eine Beschreibung für die Felder im Array.  
  
## <a name="remarks"></a>Remarks  
Die folgende Tabelle beschreibt die Felder im durch „getColumnMeta“ zurückgegebenen Array.  
  
|NAME|VALUES|  
|--------|----------|  
|native_type|Gibt den PHP-Typ der Spalte an Immer Zeichenfolge.|  
|driver:decl_type|Gibt den SQL-Typ an, der verwendet wird, um den Spaltenwert in der Datenbank darzustellen Falls die Spalte im Resultset das Ergebnis einer Funktion ist, wird dieser Wert nicht von PDOStatement::getColumnMeta zurückgegeben.|  
|flags|Gibt die Flags (Kennzeichnungen), die für diese Spalte eingerichtet wurden, an Immer 0.|  
|NAME|Gibt den Namen der Spalte in der Datenbank an|  
|-Tabelle|Gibt den Namen derjenigen Tabelle in der Datenbank an, welche die Spalte enthält Immer leer.|  
|Länge|Gibt die Länge der Spalte an|  
|precision|Gibt die numerische Genauigkeit dieser Spalte an|  
|pdo_type|Gibt den Typ dieser Spalte an, wie durch die PDO::PARAM_* Konstanten widergespiegelt. Immer PDO::PARAM_STR (2).|  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
