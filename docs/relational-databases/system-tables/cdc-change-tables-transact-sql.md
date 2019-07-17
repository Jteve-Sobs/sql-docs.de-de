---
title: CDC. change_tables (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.change_tables
- cdc.change_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.change_tables
ms.assetid: 3525a5f5-8d8b-46a8-b334-4b7cd9fb7c21
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4432d4c45bdecc6f5e1804427770d005adde0cd5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081277"
---
# <a name="cdcchangetables-transact-sql"></a>cdc.change_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile pro Änderungstabelle in der Datenbank zurück. Eine Änderungstabelle wird erstellt, wenn Change Data Capture für eine Quelltabelle aktiviert ist. Es wird empfohlen, die Systemtabellen nicht direkt abzufragen. Führen Sie stattdessen die [Sys. sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md) gespeicherte Prozedur.  
  |Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID der Änderungstabelle. Ist innerhalb einer Datenbank eindeutig.|  
|**version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] gibt diese Spalte immer den Wert 0 zurück.|  
|**source_object_id**|**int**|ID der Quelltabelle, für die Change Data Capture aktiviert ist.|  
|**capture_instance**|**sysname**|Name der Aufzeichnungsinstanz, der zur Benennung von instanzspezifischen Nachverfolgungsobjekten verwendet wird. Der Name wird standardmäßig vom Namen des Quellschemas sowie vom Namen der Quelltabelle im Format abgeleitet *Schemaname_sourcename*.|  
|**start_lsn**|**binary(10)**|Protokollfolgenummer (Log Sequence Number, LSN), die den unteren Endpunkt zum Abfragen der in der Änderungstabelle enthaltenen Änderungsdaten darstellt.<br /><br /> NULL = Der untere Endpunkt wurde nicht erstellt.|  
|**end_lsn**|**binary(10)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> Für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] gibt diese Spalte immer NULL zurück.|  
|**supports_net_changes**|**bit**|Unterstützung zum Abfragen von Nettoänderungen ist für die Änderungstabelle aktiviert.|  
|**has_drop_pending**|**bit**|Der Aufzeichnungsprozess hat die Benachrichtigung erhalten, dass die Quelltabelle gelöscht wurde.|  
|**role_name**|**sysname**|Der Name der Datenbankrolle, die zum Steuern des Zugriffs verwendet werden, um Daten zu ändern.<br /><br /> NULL = Eine Rolle wird nicht verwendet.|  
|**index_name**|**sysname**|Name des Indexes, mit dessen Hilfe Zeilen in der Quelltabelle eindeutig identifiziert werden. **Index_name** ist entweder der Name des Primärschlüsselindexes der Quelltabelle oder der Name eines eindeutigen Indexes angegeben, wenn Change Data Capture für die Quelltabelle aktiviert wurde.<br /><br /> NULL = Bei der Aktivierung von Change Data Capture verfügte die Quelltabelle über keinen Primärschlüssel, und es wurde auch kein eindeutiger Index angegeben.<br /><br /> Hinweis: Wenn Change Data Capture für eine Tabelle aktiviert ist, in denen ein Primärschlüssel vorhanden ist, verwendet die Change Data Capture-Funktion den Index unabhängig davon, ob nettoänderungen aktiviert sind oder nicht. Nachdem Change Data Capture aktiviert wurde, kann der Primärschlüssel nicht mehr geändert werden. Besitzt die Tabelle keinen Primärschlüssel, können Sie immer noch Change Data Capture aktivieren, jedoch nur dann, wenn Nettoänderungen auf false festgelegt wurden. Nachdem Change Data Capture aktiviert wurde, können Sie einen Primärschlüssel erstellen. Sie können den Primärschlüssel auch ändern, denn Change Data Capture verwendet den Primärschlüssel nicht.|  
|**filegroup_name**|**sysname**|Name der Dateigruppe, in der sich die Änderungstabelle befindet.<br /><br /> NULL = Die Änderungstabelle befindet sich in der Standarddateigruppe der Datenbank.|  
|**create_date**|**datetime**|Datum, an dem die Quelltabelle aktiviert wurde.|  
|**partition_switch**|**bit**|Gibt an, ob die **SWITCH PARTITION** -Befehl **ALTER TABLE** ausgeführt werden kann, für eine Tabelle, die für Change Data Capture aktiviert ist. 0 bedeutet, dass der Partitionswechsel blockiert wird. Für nicht partitionierte Tabellen wird stets 1 zurückgegeben.|  
  
## <a name="see-also"></a>Siehe auch  
 [Sys. sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
