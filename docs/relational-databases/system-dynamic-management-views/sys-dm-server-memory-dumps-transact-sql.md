---
title: sys. dm_server_memory_dumps (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_server_memory_dumps_TSQL
- dm_server_memory_dumps_TSQL
- dm_server_memory_dumps
- sys.dm_server_memory_dumps
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_memory_dumps dynamic management view
ms.assetid: 41782719-f54d-4e11-941a-c050c7576e23
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 643cd663510877760893bf33944f01dac93d4ded
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821006"
---
# <a name="sysdm_server_memory_dumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Speicherabbilddatei zurück, die von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]erzeugt wurde. Verwenden Sie diese dynamische Verwaltungssicht, um potenzielle Probleme zu beheben.  
 
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Einfügen**|**nvarchar(256)**|Der Pfad und der Name der Speicherabbilddatei. Lässt keine NULL-Werte zu.|  
|**creation_time**|**datetimeoffset(7)**|Das Datum und die Uhrzeit, zu der die Datei erstellt wurde. Lässt keine NULL-Werte zu.|  
|**size_in_bytes**|**bigint**|Größe der Datei in Bytes. Lässt NULL-Werte zu.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Bei dem Speicherabbild (Dump) kann es sich um einen Minidump, einen Dump aller Threads oder um einen vollständigen Dump handeln. Die Dateien haben die Erweiterung ".mdmp".  
  
## <a name="security"></a>Sicherheit  
 Dumpdateien können vertrauliche Informationen enthalten. Zum Schutz vertraulicher Informationen können Sie eine Zugriffssteuerungsliste verwenden, um den Zugriff auf die Dateien einzuschränken oder die Dateien in einen Ordner mit eingeschränktem Zugriff zu kopieren. Bevor Sie Ihre Debugdateien beispielsweise an Microsoft Support Services senden, wird empfohlen, vertrauliche Informationen zu entfernen.  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung.  
  
  
