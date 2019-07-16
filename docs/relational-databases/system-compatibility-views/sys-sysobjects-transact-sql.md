---
title: Sys.sysobjects (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysobjects_TSQL
- sysobjects
- sysobjects_TSQL
- sys.sysobjects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysobjects compatibility view
- sysobjects system table
ms.assetid: 44fdc387-67b0-4139-8bf5-ed26cf640cd1
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 26d4860c7ea434aecb0255134178b73fb7c01be4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67995608"
---
# <a name="syssysobjects-transact-sql"></a>sys.sysobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jedes in einer Datenbank erstellte Objekt, wie z. B. Einschränkungen, Standardwerte, Protokolle, Regeln und gespeicherte Prozeduren.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|NAME|**sysname**|Objektname|  
|id|**int**|Objekt-ID|  
|xtype|**char(2)**|Objekttyp. Einer der folgenden Objekttypen ist möglich:<br /><br /> AF = Aggregatfunktion (CLR)<br /><br /> C = CHECK-Einschränkung<br /><br /> D = Standard- oder DEFAULT-Einschränkung<br /><br /> F = FOREIGN KEY-Einschränkung<br /><br /> L = Protokoll<br /><br /> FN = Skalarfunktion<br /><br /> FS = Assemblyskalarfunktion (CLR)<br /><br /> FT = Assembly-Tabellenwertfunktion (CLR)<br /><br /> IF = Inline-Tabellenfunktion<br /><br /> IT = Interne Tabelle<br /><br /> P = Gespeicherte Prozedur<br /><br /> PC = Gespeicherte Assemblyprozedur (CLR)<br /><br /> PK = PRIMARY KEY-Einschränkung (Typ ist K)<br /><br /> RF = Gespeicherte Replikationsfilterprozedur<br /><br /> S = Systemtabelle<br /><br /> SN = Synonym<br /><br /> SQ = Dienstwarteschlange<br /><br /> TA = Assembly-DML-Trigger (CLR)<br /><br /> TF = Tabellenfunktion<br /><br /> TR = SQL-DML-Trigger<br /><br /> TT = Tabellentyp<br /><br /> U = Benutzertabelle<br /><br /> UQ = UNIQUE-Einschränkung (Typ ist K)<br /><br /> V = Sicht<br /><br /> X = Erweiterte gespeicherte Prozedur|  
|uid|**smallint**|Schema-ID des Objektbesitzers. Bei Datenbanken, die von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wurden, ist die Schema-ID gleich der Benutzer-ID des Besitzers. Führt zu einem Überlauf oder gibt NULL zurück, wenn die Anzahl von Benutzern und Rollen 32.767 übersteigt.<br /><br /> **\*\* Wichtige \* \***  bei Verwendung eines der folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DDL-Anweisungen, verwenden Sie die [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) -Katalogsicht anstelle von sys.sysobjects.<br /><br /> ERSTELLEN SIE &#124; ALTER &#124; DROP USER<br /><br /> ERSTELLEN SIE &#124; ALTER &#124; DROP ROLE<br /><br /> ERSTELLEN SIE &#124; ALTER &#124; DROP APPLICATION ROLE<br /><br /> CREATE SCHEMA<br /><br /> ALTER AUTHORIZATION ON OBJECT|  
|info|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|base_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|replinfo|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|parent_obj|**int**|Objekt-ID des übergeordneten Objekts. Dazu zählt beispielsweise die Tabellen-ID, wenn es sich um einen Trigger oder eine Einschränkung handelt.|  
|crdate|**datetime**|Datum, an dem das Objekt erstellt wurde.|  
|ftcatid|**smallint**|Bezeichner des Volltextkatalogs für alle Benutzertabellen, die für die Volltextindizierung registriert sind; 0 für alle nicht registrierten Benutzertabellen.|  
|schema_ver|**int**|Versionsnummer, die jedes Mal erhöht wird, wenn sich das Schema für eine Tabelle ändert. Es wird immer 0 zurückgegeben.|  
|stats_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|Typ|**char(2)**|Objekttyp. Folgende Werte sind möglich:<br /><br /> AF = Aggregatfunktion (CLR)<br /><br /> C = CHECK-Einschränkung<br /><br /> D = Standard- oder DEFAULT-Einschränkung<br /><br /> F = FOREIGN KEY-Einschränkung<br /><br /> FN = Skalarfunktion<br /><br /> FS = Assemblyskalarfunktion (CLR)<br /><br /> FT = Assembly-Tabellenwertfunktion (CLR), IF = Inline-Tabellenfunktion<br /><br /> IT = Interne Tabelle<br /><br /> K = PRIMARY KEY- oder UNIQUE-Einschränkung<br /><br /> L = Protokoll<br /><br /> P = Gespeicherte Prozedur<br /><br /> PC = Gespeicherte Assemblyprozedur (CLR)<br /><br /> R = Regel<br /><br /> RF = Gespeicherte Replikationsfilterprozedur<br /><br /> S = Systemtabelle<br /><br /> SN = Synonym<br /><br /> SQ = Dienstwarteschlange<br /><br /> TA = Assembly-DML-Trigger (CLR)<br /><br /> TF = Tabellenfunktion<br /><br /> TR = SQL-DML-Trigger<br /><br /> TT = Tabellentyp<br /><br /> U = Benutzertabelle<br /><br /> V = Sicht<br /><br /> X = Erweiterte gespeicherte Prozedur|  
|userstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|sysstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|indexdel|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|refdate|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|version|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|deltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|instrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|updtrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|seltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|category|**int**|Wird für Veröffentlichung, Einschränkungen und Identität verwendet.|  
|Cache|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Siehe auch  
 [Zuordnen von Systemtabellen zu Systemsichten &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
