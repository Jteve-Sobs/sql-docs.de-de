---
title: Sys. server_sql_modules (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.server_sql_modules
- sys.server_sql_modules_TSQL
- server_sql_modules_TSQL
- server_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_sql_modules catalog view
ms.assetid: 9ef9a8b9-c470-4a61-b0c4-ee24ad871d63
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 95583de206841bb3ed3ccff42809c028443c63ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62743952"
---
# <a name="sysserversqlmodules-transact-sql"></a>sys.server_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält den SQL-Modulsatz für Trigger vom Typ TR auf Serverebene. Sie können diese Beziehung mit sys.server_triggers verknüpfen. Das Tupel (object_id) ist der Schlüssel der Beziehung.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Ein FOREIGN KEY-Verweis zurück auf den Trigger auf Serverebene, wo dieses Modul definiert ist.|  
|**definition**|**nvarchar(max)**|Der SQL-Text, der dieses Modul definiert.<br /><br /> NULL = Verschlüsselt.|  
|**uses_ansi_nulls**|**bit**|Beim Erstellen des Moduls war die Option SET ANSI NULLS auf ON festgelegt.|  
|**uses_quoted_identifier**|**bit**|Beim Erstellen des Moduls war die Option SET QUOTED IDENTIFIER auf ON festgelegt.|  
|**execute_as_principal_id**|**int**|ID des Serverprinzipals, der mit EXECUTE AS verwendet wird.<br /><br /> NULL als Standard oder bei EXECUTE AS CALLER<br /><br /> ID des angegebenen Prinzipals bei führen AS SELF EXECUTE AS-Prinzipal-2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
