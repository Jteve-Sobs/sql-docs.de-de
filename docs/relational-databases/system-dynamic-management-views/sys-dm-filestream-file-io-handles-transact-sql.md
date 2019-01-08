---
title: Sys.dm_filestream_file_io_handles (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25af20743a98ad674e24cf4ae028185b024697e5
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52395885"
---
# <a name="sysdmfilestreamfileiohandles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeigt die Dateihandles an, die dem Namespace-Besitzer (NSO) bekannt sind. Dateistromhandles, die ein Client durch Verwendung von **OpenSqlFilestream** erhalten hat, werden in dieser Sicht angezeigt.  
  
|Spalte|Typ|Description|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|Zeigt die Adresse der internen NSO-Struktur, die der Handle des Clients zugeordnet. Lässt NULL-Werte zu.|  
|**creation_request_id**|**int**|Zeigt ein Feld der REQ_PRE_CREATE-E/A-Anforderung an, die zur Erstellung dieser Handle verwendet wird. Lässt keine NULL-Werte zu.|  
|**creation_irp_id**|**int**|Zeigt ein Feld der REQ_PRE_CREATE-E/A-Anforderung an, die zur Erstellung dieser Handle verwendet wird. Lässt keine NULL-Werte zu.|  
|**handle_id**|**int**|Zeigt die eindeutige ID dieser Anforderung an, die vom Treiber zugewiesen ist. Lässt keine NULL-Werte zu.|  
|**creation_client_thread_id**|**varbinary(8)**|Zeigt ein Feld der REQ_PRE_CREATE-E/A-Anforderung an, die zur Erstellung dieser Handle verwendet wird. Lässt NULL-Werte zu.|  
|**creation_client_process_id**|**varbinary(8)**|Zeigt ein Feld der REQ_PRE_CREATE-E/A-Anforderung an, die zur Erstellung dieser Handle verwendet wird. Lässt NULL-Werte zu.|  
|**filestream_transaction_id**|**varbinary(128)**|Zeigt die ID der Transaktion an, die dem vorliegenden Handle zugeordnet ist. Hierbei handelt es sich um den Wert, der von der **get_filestream_transaction_context** -Funktion zurückgegeben wird. Verwenden Sie dieses Feld, um einen Join mit der **sys.dm_filestream_file_io_requests** -Sicht herzustellen. Lässt NULL-Werte zu.|  
|**access_type**|**nvarchar(60)**|Lässt keine NULL-Werte zu.|  
|**logical_path**|**nvarchar(256)**|Zeigt den logischen Pfadnamen der Datei an, die von dieser Handle geöffnet wurde. Hierbei handelt es sich um den gleichen Pfadnamen, der von der **.PathName** -Methode des **varbinary**(**max**)-Dateistroms zurückgegeben wird. Lässt NULL-Werte zu.|  
|**physical_path**|**nvarchar(256)**|Zeigt den tatsächlichen NTFS-Pfadnamen der Datei an. Hierbei handelt es sich um den gleichen Pfadnamen, der von der **.PhysicalPathName** -Methode des **varbinary**(**max**)-Dateistroms zurückgegeben wird. Die Aktivierung erfolgt durch Ablaufverfolgungsflag 5556. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [FileStream und FileTable dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
