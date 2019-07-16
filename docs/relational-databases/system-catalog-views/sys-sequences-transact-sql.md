---
title: Sys.sequences (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sequences_TSQL
- sys.sequences
- sequences
- sequences_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, sys. sequences catalog view
- sys.sequences catalog view
ms.assetid: 0e1b0e32-1cce-40f7-83c8-860ec660138a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 410f6dcca93614c42de4a703fd591bb1c9cbc59a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68060554"
---
# <a name="syssequences-transact-sql"></a>sys.sequences (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Sequenzobjekt in einer Datenbank.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|\<geerbte Spalten >||Erbt alle Spalten von [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**start_value**|**Sql_variant nicht NULL**|Der Startwert für das Sequenzobjekt. Wenn das Sequenzobjekt mit ALTER SEQUENCE neu gestartet wird, dient dieser Wert als Ausgangspunkt. Wenn das Sequenzobjekt Zyklen sie weiterhin die **Minimum_value** oder **Maximum_value**, nicht die **Start_value**.|  
|**increment**|**Sql_variant nicht NULL**|Der Wert, um den das Sequenzobjekt nach jedem generierten Wert inkrementiert wird.|  
|**minimum_value**|**NULL-sql_variant**|Der minimale Wert, der vom Sequenzobjekt generiert werden kann. Wenn dieser Wert erreicht wird, wird das Sequenzobjekt, das entweder einen Fehler zurück, beim Versuch, weitere Werte generieren oder neu starten, wenn die CYCLE-Option angegeben wird. Wenn kein MINVALUE angegeben wurde, gibt diese Spalte den minimalen Wert vom Datentyp des Sequenz-Generators unterstützt.|  
|**maximum_value**|**NULL-sql_variant**|Der maximale Wert, der vom Sequenzobjekt generiert werden kann. Nachdem dieser Wert erreicht wurde, wird vom Sequenzobjekt ein Fehler zurückgegeben, wenn versucht wird, weitere Werte zu generieren; wenn die CYCLE-Option angegeben wird, erfolgt ein Neustart. Wenn kein MAXVALUE angegeben wurde, wird von dieser Spalte der maximale Wert zurückgegeben, der vom Datentyp des Sequenz-Objekts unterstützt wird.|  
|**is_cycling**|**Bit nicht NULL**|Gibt 0 zurück, wenn NO CYCLE für das Sequenzobjekt angegeben wurde, und 1, wenn CYCLE angegeben wurde.|  
|**is_cached**|**Bit nicht NULL**|Gibt 0 zurück, wenn NO CACHE für das Sequenzobjekt angegeben wurde, und 1, wenn CACHE angegeben wurde.|  
|**cache_size**|**Int NULL**|Gibt die angegebene Cachegröße für das Sequenzobjekt zurück. Diese Spalte enthält NULL, wenn die Sequenz mit der NO CACHE-Option erstellt oder CACHE ohne Cachegröße angegeben wurde. Wenn der von der Cachegröße angegebene Wert die maximal möglichen Rückgabewerte des Sequenzobjekts übersteigt, wird die nicht abrufbare Cachegröße weiterhin angezeigt.|  
|**system_type_id**|**Tinyint nicht NULL**|Die ID des Systemtyps für den Datentyp des Sequenzobjekts ab.|  
|**user_type_id**|**Int nicht NULL**|Die ID des Datentyps für das Sequenzobjekt, wie vom Benutzer definiert.|  
|**precision**|**Tinyint nicht NULL**|Die maximale Genauigkeit des Datentyps.|  
|**scale**|**Tinyint nicht NULL**|Die maximalen Dezimalstellen des Typs. Die Dezimalstellenzahl wird zusammen mit der Genauigkeit zurückgegeben, damit Benutzer über vollständige Metadaten verfügen. Die Dezimalstellenzahl beträgt bei Sequenzobjekten immer 0, da nur ganzzahlige Typen zulässig sind.|  
|**Current_value**|**Sql_variant nicht NULL**|Der letzte zurückgegebene Wert. Das heißt, der Wert zurückgegeben, von der letzten Ausführung der NEXT VALUE FOR-Funktion oder der letzten Ausführung der **Sp_sequence_get_range** Verfahren. Gibt den START WITH-Wert zurück, wenn die Sequenz noch nie verwendet wurde.|  
|**is_exhausted**|**Bit nicht NULL**|0 gibt an, dass weitere Werte von der Sequenz generiert werden können. 1 gibt an, dass das Sequenzobjekt den MAXVALUE-Parameter erreicht hat und die Sequenz nicht auf CYCLE festgelegt wurde. Die NEXT VALUE FOR-Funktion gibt einen Fehler zurück, solange die Sequenz nicht mit ALTER SEQUENCE neu gestartet wird.|  
|**last_used_value**|**NULL-sql_variant**|Gibt den letzten Wert generiert, indem Sie die [Next Value For](../../t-sql/functions/next-value-for-transact-sql.md) Funktion. Gilt für SQL Server 2017 und höher.|  
  
## <a name="permissions"></a>Berechtigungen  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und späteren Versionen ist die Sichtbarkeit der Metadaten in Katalogsichten auf sicherungsfähige Elemente eingeschränkt, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sequenznummern](../../relational-databases/sequence-numbers/sequence-numbers.md)   
 [CREATE SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [NEXT VALUE FOR &#40;Transact-SQL&#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [sp_sequence_get_range &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md)  
  
  
