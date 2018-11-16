---
title: ROUTINE_COLUMNS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- ROUTINE_COLUMNS_TSQL
- ROUTINE_COLUMNS
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINE_COLUMNS view
- INFORMATION_SCHEMA.ROUTINE_COLUMNS view
ms.assetid: 91dbc61b-e4c0-4826-976c-b2fce88b7793
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 862d07d3a27549f8bb0b45a807d1a04c7b13e364
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51659629"
---
# <a name="routinecolumns-transact-sql"></a>ROUTINE_COLUMNS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Spalte, die von den Tabellenwertfunktionen zurückgegeben wird, auf die der aktuelle Benutzer in der aktuellen Datenbank zugreifen kann.  
  
 Geben Sie zum Abrufen von Informationen aus dieser Sicht den vollqualifizierten Namen der **INFORMATION_SCHEMA. *** View_name*.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**Nvarchar (** 128 **)**|Katalog- oder Datenbankname der Tabellenwertfunktion|  
|**TABLE_SCHEMA**|**Nvarchar (** 128 **)**|Name des Schemas, das die Tabellenwertfunktion enthält<br /><br /> **\*\* Wichtige \* \***  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**TABLE_NAME**|**Nvarchar (** 128 **)**|Name der Tabellenwertfunktion|  
|**COLUMN_NAME**|**Nvarchar (** 128 **)**|Name der Spalte.|  
|**ORDINAL_POSITION**|**int**|Identifikationsnummer der Spalte|  
|**COLUMN_DEFAULT**|**Nvarchar (** 4000 **)**|Standardwert der Spalte|  
|**IS_NULLABLE**|**Varchar (** 3 **)**|Ist NULL in dieser Spalte zulässig, wird YES zurückgegeben. Andernfalls Nein.|  
|**DATA_TYPE**|**Nvarchar (** 128 **)**|Vom System bereitgestellter Datentyp|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Maximale Länge (in Zeichen) für binäre Daten, Zeichendaten, Text- und Tmage-Daten<br /><br /> -1 für **Xml** und große Werttypen. Andernfalls wird NULL zurückgegeben. Weitere Informationen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**int**|Maximale Länge (in Bytes) für binäre Daten, Zeichendaten, Text- und Image-Daten.<br /><br /> -1 für **Xml** und große Werttypen. Andernfalls wird NULL zurückgegeben.|  
|**"NUMERIC_PRECISION"**|**tinyint**|Genauigkeit für Spalten mit ungefähren numerischen Daten, exakten numerischen Daten, ganzzahligen Daten oder Währungsdaten. Andernfalls wird NULL zurückgegeben.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Basis der Genauigkeit für Spalten mit ungefähren numerischen Daten, exakten numerischen Daten, ganzzahligen Daten oder Währungsdaten. Andernfalls wird NULL zurückgegeben.|  
|**NUMERIC_SCALE**|**tinyint**|Anzahl der Dezimalstellen für Spalten mit ungefähren numerischen Daten, exakten numerischen Daten, ganzzahligen Daten oder Währungsdaten. Andernfalls wird NULL zurückgegeben.|  
|**DATETIME_PRECISION**|**smallint**|Untertypcode für **"DateTime"** und ISO**Ganzzahl** -Datentypen. Für andere Datentypen wird NULL zurückgegeben.|  
|**CHARACTER_SET_CATALOG**|**Varchar (** 6 **)**|Gibt **master**. Hiermit wird die Datenbank, in dem der Zeichensatz befindet ist die Spalte Zeichendaten, oder **Text** -Datentyp. Andernfalls wird NULL zurückgegeben.|  
|**CHARACTER_SET_SCHEMA**|**Varchar (** 3 **)**|Gibt immer NULL zurück.|  
|**CHARACTER_SET_NAME**|**Nvarchar (** 128 **)**|Gibt den eindeutigen Namen für den Zeichensatz, falls diese Spalte Zeichendaten oder **Text** -Datentyp. Andernfalls wird NULL zurückgegeben.|  
|**COLLATION_CATALOG**|**Varchar (** 6 **)**|Gibt immer NULL zurück.|  
|**COLLATION_SCHEMA**|**Varchar (** 3 **)**|Gibt immer NULL zurück.|  
|**COLLATION_NAME**|**Nvarchar (** 128 **)**|Gibt den eindeutigen Namen für die Sortierreihenfolge zurück, wenn die Spalte Zeichendaten oder **Text** -Datentyp. Andernfalls wird NULL zurückgegeben.|  
|**DOMAIN_CATALOG**|**Nvarchar (** 128 **)**|Falls die Spalte Daten des Aliastyps enthält, wird in dieser Spalte der Name der Datenbank angezeigt, in der der benutzerdefinierte Datentyp erstellt wurde. Andernfalls wird NULL zurückgegeben.|  
|**DOMAIN_SCHEMA**|**Nvarchar (** 128 **)**|Falls die Spalte Daten eines benutzerdefinierten Typs enthält, wird in dieser Spalte der Name des Schemas angezeigt, das den benutzerdefinierten Datentyp enthält. Andernfalls wird NULL zurückgegeben.<br /><br /> **\*\* Wichtige \* \***  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**DOMÄNENNAME**|**Nvarchar (** 128 **)**|Falls die Spalte Daten eines benutzerdefinierten Typs enthält, wird in dieser Spalte der Name des benutzerdefinierten Datentyps angezeigt. Andernfalls wird NULL zurückgegeben.|  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informationsschemasichten &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
