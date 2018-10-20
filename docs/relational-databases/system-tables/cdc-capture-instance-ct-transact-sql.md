---
title: CDC. &lt;Capture_instance&gt;_CT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc
- cdc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.<capture_instance>_CT
ms.assetid: 979c8110-3c54-4e76-953c-777194bc9751
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 346fea411891f04e4b4742ff50c2dd9cce6f1587
ms.sourcegitcommit: 4c053cd2f15968492a3d9e82f7570dc2781da325
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "49336249"
---
# <a name="cdcltcaptureinstancegtct-transact-sql"></a>CDC. &lt;Capture_instance&gt;_CT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die Änderungstabelle, die erstellt wird, wenn Change Data Capture für eine Quelltabelle aktiviert wird. Für jeden Einfüge- oder Löschvorgang, der in der Quelltabelle ausgeführt wird, gibt die Tabelle eine Zeile zurück, für jeden Updatevorgang in der Quelltabelle gibt sie zwei Zeilen zurück. Wird der Name der Änderungstabelle bei der Aktivierung der Quelltabelle nicht angegeben, wird der Name abgeleitet. Das Format des Namens ist die cdc. *Capture_instance*_CT, in denen *Capture_instance* ist den Schemanamen der Quelltabelle und dem Quelltabellennamen im Format *Schema_table*. Z. B. wenn die Tabelle **Person.Address** in die **AdventureWorks** -Beispieldatenbank für Change Data Capture aktiviert ist, der Name der abgeleiteten Tabelle **cdc. Person_Address_CT**.  
  
 Es wird empfohlen, die Sie **die Systemtabellen nicht direkt Abfragen**. Führen Sie stattdessen die [CDC. fn_cdc_get_all_changes_ < Capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) und [CDC. fn_cdc_get_net_changes_ < Capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md) Funktionen.  
  

  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**__$start_lsn**|**binary(10)**|Protokollfolgenummer (LSN, Log Sequence Number), die dem Commit für die Änderung zugeordnet wurde.<br /><br /> Alle Änderungen, für die ein Commit in derselben Transaktion ausgeführt wurde, verwenden dieselbe Commit-LSN. Z. B. wenn ein Delete-Vorgang in der Quelltabelle zwei Zeilen entfernt, die Änderungstabelle enthält zwei Zeilen, die jeweils mit dem gleichen **__ $Start_lsn** Wert.|  
|**__ $end_lsn**|**binary(10)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hat diese Spalte immer den Wert NULL.|  
|**__$seqval**|**binary(10)**|Sequenzwert, der verwendet wird, um die Zeilenänderungen innerhalb einer Transaktion zu sortieren.|  
|**__$operation**|**int**|Identifiziert den Vorgang der Datenbearbeitungssprache (Data Manipulation Language, DML), der der Änderung zugeordnet ist. Kann einen der folgenden Werte annehmen:<br /><br /> 1 = Löschen<br /><br /> 2 = Einfügen<br /><br /> 3 = Aktualisieren (alte Werte)<br /><br /> Spaltendaten verfügen vor der Ausführung der UPDATE-Anweisung über Zeilenwerte.<br /><br /> 4 = Aktualisieren (neue Werte)<br /><br /> Spaltendaten verfügen nach der Ausführung der UPDATE-Anweisung über Zeilenwerte.|  
|**__$update_mask**|**varbinary(128)**|Eine Bitmaske, die basierend auf den Spaltenordnungszahlen der Änderungstabelle, die geänderte Spalten identifiziert.|  
|*\<erfasste Quelltabellenspalten>*|variiert|Bei den verbleibenden Spalten in der Änderungstabelle handelt es sich um die Spalten aus der Quelltabelle, die beim Erstellen der Aufzeichnungsinstanz als aufgezeichnete Tabellen identifiziert wurden. Wenn in der Liste der aufgezeichneten Spalten keine Spalten angegeben wurden, werden alle Spalten in der Quelltabelle in diese Tabelle aufgenommen.|  
|**__ $command_id** |**int** |Verfolgt die Reihenfolge der Vorgänge innerhalb einer Transaktion. |  
  
## <a name="remarks"></a>Hinweise  

Die `__$command_id` Spalte wurde die Spalte wurde in ein kumulatives Update in Versionen 2012 bis 2016 eingeführt. Informationen zu Version und herunterladen, finden Sie unter im Knowledge Base-Artikel 3030352 unter [behoben: die Änderungstabelle sortiert wird, ist nicht ordnungsgemäß nach aktualisierten Zeilen nach der Aktivierung von Change Data capture für eine Microsoft SQL Server-Datenbank](https://support.microsoft.com/help/3030352/fix-the-change-table-is-ordered-incorrectly-for-updated-rows-after-you).  Weitere Informationen finden Sie unter [CDC-Funktionen kann nach dem Upgrade auf die neueste CU für SQL Server 2012, 2014 und 2016 unterbrechen](https://blogs.msdn.microsoft.com/sql_server_team/cdc-functionality-may-break-after-upgrading-to-the-latest-cu-for-sql-server-2012-2014-and-2016/).

## <a name="captured-column-data-types"></a>Datentypen von aufgezeichneten Spalten  
 Die in dieser Tabelle enthaltenen aufgezeichneten Spalten haben denselben Datentyp und Wert wie die entsprechenden Quellspalten. Hierbei gelten folgende Ausnahmen:  
  
-   **Zeitstempel** als Spalten definiert sind **binary(8)**.  
  
-   **Identität** Spalten definiert werden, entweder als **Int** oder **Bigint**.  
  
 Die Werte in diesen Spalten sind jedoch mit den Quellspaltenwerten identisch.  
  
### <a name="large-object-data-types"></a>LOB (Large Object)-Datentypen  
 Spalten des Datentyps **Image**, **Text**, und **Ntext** werden immer zugewiesen eine **NULL** Wert fest, wenn __ $Operation = 1 oder \_ \_$operation = 3. Spalten des Datentyps **'varbinary(max)'**, **varchar(max)**, oder **nvarchar(max)** zugewiesen sind eine **NULL** Wert fest, wenn \_ \_$operation = 3, es sei denn, die Spalte während des Updates geändert wurde. Wenn \_ \_$operation = 1, werden diesen Spalten ihr Wert zum Zeitpunkt der Löschung zugewiesen. Berechnete Spalten, die in einer Aufzeichnungsinstanz, immer enthalten sind den Wert haben **NULL**.  
  
 Standardmäßig können einer aufgezeichneten Spalte in einer einzelnen Anweisung vom Typ INSERT, UPDATE, WRITETEXT oder UPDATETEXT maximal 65.536 Bytes oder 64 KB hinzugefügt werden. Sodass auch umfangreichere LOB-Daten unterstützt mithilfe der [Konfigurieren der max Text Repl Size Server Configuration Option](../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md) eine höhere Maximalgröße angeben. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption max text repl size](../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md).  
  
## <a name="data-definition-language-modifications"></a>Änderungen mithilfe der Datendefinitionssprache (Data Definition Language, DDL)  
 DDL-Änderungen an der Quelltabelle, wie das Hinzufügen oder Löschen von Spalten, in aufgezeichnet werden die [ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md) Tabelle. Diese Änderungen werden nicht auf die Änderungstabelle angewendet. Die Definition der Änderungstabelle bleibt also konstant. Werden Zeilen in die Änderungstabelle eingefügt, werden während des Aufzeichnungsvorgangs diejenigen Spalten ignoriert, die nicht in der Liste der aufgezeichneten Spalten, die der Quelltabelle zugeordnet ist, aufgeführt sind. Falls in der Liste der aufgezeichneten Spalten eine Spalte angezeigt wird, die sich nicht mehr in der Quelltabelle befindet, wird dieser Spalte ein NULL-Wert zugewiesen.  
  
 Ändern des Datentyps einer Spalte in der Quelltabelle wird auch in erfasst die [ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md) Tabelle. Durch diese Änderung wird die Definition der Änderungstabelle jedoch nicht geändert. Der Datentyp der aufgezeichneten Spalte in der Änderungstabelle wird geändert, wenn während des Aufzeichnungsvorgangs der Protokolldatensatz für die an der Quelltabelle vorgenommenen Änderungen gefunden wird.  
  
 Falls Sie den Datentyp einer aufgezeichneten Spalte in der Quelltabelle so ändern müssen, dass die Größe des Datentyps verringert wird, stellen Sie mithilfe des folgenden Verfahrens sicher, dass die entsprechende Spalte in der Änderungstabelle erfolgreich geändert werden kann.  
  
1.  Aktualisieren Sie in der Quelltabelle die Werte in der zu ändernden Spalte, sodass ihre Größe für die geplante Datentypgröße geeignet ist. Angenommen, Sie ändern, dass den Datentyp vom **Int** zu **Smallint**, aktualisieren Sie die Werte auf eine Größe, in der **Smallint** -Bereich von-32.768 bis 32.767.  
  
2.  Führen Sie denselben Updatevorgang in der Änderungstabelle für die entsprechende Spalte aus.  
  
3.  Ändern Sie die Quelltabelle, indem Sie den neuen Datentyp angeben. Die Datentypänderung wird erfolgreich an die Änderungstabelle weitergegeben.  
  
## <a name="data-manipulation-language-modifications"></a>Änderungen mithilfe der Datenbearbeitungssprache (Data Manipulation Language, DDL)  
 Wenn in einer Change Data Capture-aktivierten Quelltabelle Einfüge-, Update- und Löschvorgänge ausgeführt werden, wird im Datenbanktransaktionsprotokoll ein Datensatz dieser DML-Vorgänge angezeigt. Der Change Data Capture-Prozess Ruft Informationen zu diesen Änderungen aus dem Transaktionsprotokoll ab und fügt einer oder zwei Zeilen in die Änderungstabelle zur Aufzeichnung der Änderung. Die Einträge werden in derselben Reihenfolge in die Änderungstabelle eingefügt, in der sie an die Quelltabelle übergeben wurden, obwohl der Commit für Einträge in der Änderungstabelle normalerweise für Gruppen von Änderungen statt für einzelne Einträge ausgeführt werden muss.  
  
 Im änderungstabelleneintrag die **__ $Start_lsn** Spalte wird verwendet, um die Commit-LSN aufzuzeichnen, die die Änderung an der Quelltabelle zugeordnet ist und die **__ $Seqval Spalte** wird verwendet, um die Änderung innerhalb der Reihenfolge die Transaktion. In Kombination können diese Metadatenspalten verwendet werden, um sicherzustellen, dass die Reihenfolge der Änderungen beim Commit beibehalten wird. Da die Änderungsinformationen beim Aufzeichnungsprozess aus dem Transaktionsprotokoll abgerufen werden, werden die Einträge in der Änderungstabelle nicht synchron mit den entsprechenden Änderungen in der Quelltabelle angezeigt. Stattdessen werden die Änderungen asynchron angezeigt, nachdem die relevanten Änderungseinträge aus dem Transaktionsprotokoll vom Aufzeichnungsprozess verarbeitet wurden.  
  
 Bei Einfüge- und Löschvorgängen werden alle Bits in der Updatemaske festgelegt. Bei Updatevorgängen wird die Updatemaske sowohl in den alten als auch in den neuen Zeilen des Updates entsprechend den Spalten geändert, die während des Updates geändert wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sp_cdc_get_ddl_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)  
  
  
