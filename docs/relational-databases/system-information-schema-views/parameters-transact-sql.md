---
title: Parameter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- PARAMETERS_TSQL
- PARAMETERS
dev_langs:
- TSQL
helpviewer_keywords:
- PARAMETERS view
- INFORMATION_SCHEMA.PARAMETERS view
ms.assetid: 06ded0ca-7d21-4400-864a-b801e855b257
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 14001680cd4cf92086ab797f77e2233222d36b67
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590714"
---
# <a name="parameters-transact-sql"></a>PARAMETERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jeden Parameter einer benutzerdefinierten Funktion oder gespeicherten Prozedur zurück, auf die der aktuelle Benutzer in der aktuellen Datenbank zugreifen kann. Für Funktionen gibt diese Sicht auch eine Zeile mit Informationen zum Rückgabewert zurück.  
  
 Geben Sie zum Abrufen von Informationen aus diesen Sichten den vollqualifizierten Namen der **INFORMATION_SCHEMA.** _View_name_.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**SPECIFIC_CATALOG**|**Nvarchar (** 128 **)**|Katalogname der Routine, für die dies ein Parameter ist|  
|**SPECIFIC_SCHEMA**|**Nvarchar (** 128 **)**|Schemaname der Routine, für die dies ein Parameter ist<br /><br /> <strong>\*\* Wichtige \* \*</strong>  verwenden Sie keine INFORMATION_SCHEMA-Sichten, die um das Schema eines Objekts zu bestimmen. Die einzig zuverlässige Möglichkeit zum Finden des Schemas eines Objekts besteht darin, die sys.objects-Katalogsicht abzufragen.|  
|**"SPECIFIC_NAME"**|**Nvarchar (** 128 **)**|Name der Routine, für die dies ein Parameter ist|  
|**ORDINAL_POSITION**|**int**|Die Ordnungsposition des Parameters, beginnend bei 1. Für den Rückgabewerts einer Funktion ist dies 0.|  
|**PARAMETER_MODE**|**Nvarchar (** 10 **)**|Gibt IN zurück, wenn es ein Eingabeparameter ist, OUT, wenn es ein Ausgabeparameter ist, und INOUT, wenn es ein Eingabe/Ausgabeparameter ist.|  
|**IS_RESULT**|**Nvarchar (** 10 **)**|Gibt YES zurück, wenn das Ergebnis auf einer Routine beruht, die eine Funktion ist. Andernfalls Nein.|  
|**AS_LOCATOR**|**Nvarchar (** 10 **)**|Gibt YES zurück, wenn der Parameter als Lokator deklariert wurde. Andernfalls Nein.|  
|**PARAMETERNAME**|**Nvarchar (** 128 **)**|Der Name des Parameters. NULL, wenn er dem Rückgabewert einer Funktion entspricht.|  
|**DATA_TYPE**|**Nvarchar (** 128 **)**|Vom System bereitgestellter Datentyp|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Maximale Länge in Zeichen für binary-Datentypen oder Zeichendatentypen<br /><br /> -1 für **Xml** und große Werttypen. Andernfalls wird NULL zurückgegeben.|  
|**CHARACTER_OCTET_LENGTH**|**int**|Maximale Länge in Bytes für binary-Datentypen oder Zeichendatentypen<br /><br /> -1 für **Xml** und große Werttypen. Andernfalls wird NULL zurückgegeben.|  
|**COLLATION_CATALOG**|**Nvarchar (** 128 **)**|Gibt immer NULL zurück.|  
|**COLLATION_SCHEMA**|**Nvarchar (** 128 **)**|Gibt immer NULL zurück.|  
|**COLLATION_NAME**|**Nvarchar (** 128 **)**|Name der Sortierung des Parameters. Wenn es sich nicht um einen der Zeichentypen handelt, wird NULL zurückgegeben.|  
|**CHARACTER_SET_CATALOG**|**Nvarchar (** 128 **)**|Katalogname des Zeichensatzes des Parameters. Wenn es sich nicht um einen der Zeichentypen handelt, wird NULL zurückgegeben.|  
|**CHARACTER_SET_SCHEMA**|**Nvarchar (** 128 **)**|Gibt immer NULL zurück.|  
|**CHARACTER_SET_NAME**|**Nvarchar (** 128 **)**|Name des Zeichensatzes des Parameters. Wenn es sich nicht um einen der Zeichentypen handelt, wird NULL zurückgegeben.|  
|**"NUMERIC_PRECISION"**|**tinyint**|Genauigkeit für Spalten mit ungefähren numerischen Daten, exakten numerischen Daten, ganzzahligen Daten oder Währungsdaten. Andernfalls wird NULL zurückgegeben.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Basis der Genauigkeit für Spalten mit ungefähren numerischen Daten, exakten numerischen Daten, ganzzahligen Daten oder Währungsdaten. Andernfalls wird NULL zurückgegeben.|  
|**NUMERIC_SCALE**|**tinyint**|Anzahl der Dezimalstellen für Spalten mit ungefähren numerischen Daten, exakten numerischen Daten, ganzzahligen Daten oder Währungsdaten. Andernfalls wird NULL zurückgegeben.|  
|**DATETIME_PRECISION**|**smallint**|Genauigkeit in Bruchteilen von Sekunden, wenn der Parametertyp ist **"DateTime"** oder **Smalldatetime**. Andernfalls wird NULL zurückgegeben.|  
|**INTERVAL_TYPE**|**Nvarchar (** 30 **)**|NULL. Zur künftigen Verwendung reserviert.|  
|**INTERVAL_PRECISION**|**smallint**|NULL. Zur künftigen Verwendung reserviert.|  
|**USER_DEFINED_TYPE_CATALOG**|**Nvarchar (** 128 **)**|NULL. Zur künftigen Verwendung reserviert.|  
|**USER_DEFINED_TYPE_SCHEMA**|**Nvarchar (** 128 **)**|NULL. Zur künftigen Verwendung reserviert.|  
|**USER_DEFINED_TYPE_NAME**|**Nvarchar (** 128 **)**|NULL. Zur künftigen Verwendung reserviert.|  
|**SCOPE_CATALOG**|**Nvarchar (** 128 **)**|NULL. Zur künftigen Verwendung reserviert.|  
|**SCOPE_SCHEMA**|**Nvarchar (** 128 **)**|NULL. Zur künftigen Verwendung reserviert.|  
|**SCOPE_NAME**|**Nvarchar (** 128 **)**|NULL. Zur künftigen Verwendung reserviert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Informationsschemasichten &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  
