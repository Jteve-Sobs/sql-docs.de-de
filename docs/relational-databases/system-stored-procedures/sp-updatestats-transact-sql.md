---
title: Sp_updatestats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 51fd5471ac678a1d61986aaa9219eec923c38485
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535762"
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Ausführungen `UPDATE STATISTICS` für alle benutzerdefinierten und internen Tabellen in der aktuellen Datenbank.  
  
Weitere Informationen zu `UPDATE STATISTICS`, finden Sie unter [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Weitere Informationen zu Statistiken finden Sie unter [Statistik](../../relational-databases/statistics/statistics.md).  
    
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="arguments"></a>Argumente  
`[ @resample = ] 'resample'` Gibt an, dass **Sp_updatestats** die RESAMPLE-Option von der [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) Anweisung. Wird **'resample'** nicht angegeben, aktualisiert **sp_updatestats** Statistiken mithilfe der Standardstichprobe. **resample** ist vom Datentyp **varchar(8)** . Der Standardwert ist NO.  
  
## <a name="remarks"></a>Hinweise  
 **Sp_updatestats** führt `UPDATE STATISTICS`, durch Angabe der `ALL` -Schlüsselwort, für alle benutzerdefinierten und internen Tabellen in der Datenbank. Sp_updatestats zeigt Meldungen über den Fortschritt an. Nach Abschluss des Updates wird gemeldet, dass die Statistiken für alle Tabellen aktualisiert wurden.  
  
sp_updatestats aktualisiert Statistiken für deaktivierte nicht gruppierte Indizes und nicht für deaktivierte gruppierte Indizes.  
  
Für datenträgerbasierte Tabellen **Sp_updatestats** aktualisiert Statistiken, die auf der Grundlage der **Modification_counter** Informationen in der **Sys. dm_db_stats_properties** -Katalogsicht Aktualisieren von Statistiken, in denen mindestens eine Zeile geändert wurde. Statistiken für speicheroptimierte Tabellen werden immer aktualisiert, wenn **sp_updatestats**ausgeführt wird. Deshalb sollte **sp_updatestats** nicht häufiger als nötig ausgeführt werden.  
  
**sp_updatestats** kann die Neukompilierung von gespeicherten Prozeduren oder anderem kompilierten Code auslösen. Allerdings kann **sp_updatestats** unter Umständen keine Neukompilierung verursachen, wenn nur ein Abfrageplan für die Tabellen, auf die verwiesen wird, und die Indizes möglich ist. Eine Neukompilierung wäre in diesen Fällen nicht erforderlich, selbst wenn die Statistiken aktualisiert werden.  
  
Bei Datenbanken mit einem Kompatibilitätsgrad unter 90 wird beim Ausführen von **sp_updatestats** die letzte NORECOMPUTE-Einstellung für bestimmte Statistiken nicht beibehalten. Bei Datenbanken mit einem Kompatibilitätsgrad von 90 oder höher behält Sp_updatestats die letzte NORECOMPUTE-Option für bestimmte Statistiken bei. Weitere Informationen zum Deaktivieren und erneuten Aktivieren von Statistikupdates finden Sie unter [Statistiken](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Setzt die Mitgliedschaft in der festen Serverrolle **sysadmin** oder den Besitz der Datenbank (**dbo**) voraus.  

## <a name="examples"></a>Beispiele  
Im folgenden Beispiel werden die Statistiken für Tabellen in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank aktualisiert.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  

## <a name="automatic-index-and-statistics-management"></a>Automatische Verwaltung von Index und Statistiken
Nutzen Sie Lösungen wie [Adaptive Index Defrag](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag), um die Indexdefragmentierung und das Aktualisieren der Statistiken für eine oder mehrere Datenbanken automatisch zu verwalten. Dieser Vorgang entscheidet unter anderem anhand des Fragmentierungsgrads automatisch, ob ein Index neu organisiert oder neu erstellt wird und aktualisiert Statistiken mit einem linearen Schwellenwert.

## <a name="see-also"></a>Siehe auch  
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Gespeicherte Systemprozeduren](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
 
