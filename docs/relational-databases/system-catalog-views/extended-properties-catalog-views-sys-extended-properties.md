---
title: Sys. extended_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.extended_properties
- sys.extended_properties_TSQL
- extended_properties
- extended_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.extended_properties catalog view
ms.assetid: 439b7299-dce3-4d26-b1c7-61be5e0df82a
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7ffac91aef6e7b761705e477a9d5b433d6e3f2fe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008518"
---
# <a name="extended-properties-catalog-views---sysextendedproperties"></a>Erweiterte Katalogsichten Eigenschaften – Sys. extended_properties
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Gibt eine Zeile für jede erweiterte Eigenschaft in der aktuellen Datenbank zurück.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|class|**tinyint**|Identifiziert die Elementklasse, für die die Eigenschaft vorhanden ist. Kann einen der folgenden Werte annehmen:<br /><br /> 0 = Datenbank<br /><br /> 1 = Objekt oder Spalte<br /><br /> 2 = Parameter<br /><br /> 3 = Schema<br /><br /> 4 = Datenbankprinzipal<br /><br /> 5 = Assembly<br /><br /> 6 = Typ<br /><br /> 7 = Index<br /><br /> 10 = XML-Schemaauflistung<br /><br /> 15 = Nachrichtentyp<br /><br /> 16 = Dienstvertrag<br /><br /> 17 = Dienst<br /><br /> 18 = Remotedienstbindung<br /><br /> 19 = Route<br /><br /> 20 = Datenspeicher (Dateigruppe oder Partitionsschema)<br /><br /> 21 = Partitionsfunktion<br /><br /> 22 = Datenbankdatei<br /><br /> 27 = Planhinweisliste|  
|class_desc|**nvarchar(60)**|Beschreibung der Klasse, für die die erweiterte Eigenschaft vorhanden ist. Kann einen der folgenden Werte annehmen:<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN<br /><br /> Parameter<br /><br /> SCHEMA<br /><br /> DATABASE_PRINCIPAL<br /><br /> ASSEMBLY<br /><br /> TYPE<br /><br /> INDEX<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> MESSAGE_TYPE<br /><br /> SERVICE_CONTRACT<br /><br /> SERVICE<br /><br /> REMOTE_SERVICE_BINDING<br /><br /> ROUTE<br /><br /> DATASPACE<br /><br /> PARTITION_FUNCTION<br /><br /> DATABASE_FILE<br /><br /> PLAN_GUIDE|  
|major_id|**int**|ID des Elements, für das die erweiterte Eigenschaft vorhanden ist, interpretiert gemäß der entsprechenden Klasse. Bei den meisten Elementen ist dies die ID, die gilt für die Klasse darstellt. Die Interpretation von Haupt-IDs, die nicht dem Standard entsprechen, lautet wie folgt:<br /><br /> Wenn Klasse 0 ist, ist Major_id immer 0.<br /><br /> Klasse ist 1, 2 oder 7 Major_id Object_id.|  
|minor_id|**int**|Sekundäre ID des Elements, für das die erweiterte Eigenschaft vorhanden ist, interpretiert gemäß der entsprechenden Klasse. Bei den meisten Elementen ist dies der Wert 0; andernfalls lautet die ID wie folgt:<br /><br /> Wenn Klasse = 1, Minor_id die Column_id ist, wenn Spalte; andernfalls 0, wenn Objekt.<br /><br /> Wenn Klasse = 2, Minor_id ist die Parameter_id.<br /><br /> Wenn Klasse 7 = Minor_id ist die Index_id.|  
|NAME|**sysname**|Der Name, Klasse, Major_id und Minor_id eindeutig.|  
|Wert|**sql_variant**|Wert der erweiterten Eigenschaft|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Eigenschaften von Katalogsichten für erweiterte &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/f39fd324-efd4-4468-884c-bf77ed1a026f)   
 [sys.fn_listextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)  
  
  
