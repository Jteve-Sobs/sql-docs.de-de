---
title: Sys. sp_rda_set_rpo_duration (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f46dd0bbedfebec5e21800b477a23d664446bf24
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982953"
---
# <a name="syssprdasetrpoduration-transact-sql"></a>sys.sp_rda_set_rpo_duration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Legt die Anzahl der Stunden der migrierten Daten, die von SQL Server beibehalten in einer Stagingtabelle aus, um sicherzustellen, eine vollständige Wiederherstellung von Azure-Remotedatenbank, wenn ein Punkt in der Time-Wiederherstellung erforderlich ist.    
    
 Weitere Informationen finden Sie unter [Stretch Database reduziert das Risiko eines Datenverlusts für Ihre Azure-Daten, indem migrierte Zeilen vorübergehend beibehalten werden](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO).  
   
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>Syntax    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>Argumente    
 [ @duration_hrs = ] *duration_hrs*    
 Die Anzahl der Stunden (ein nicht-Null-Integer-Wert) der migrierten Daten, die Sie für die aktuelle Datenbank für Stretch-aktivierten SQL Server beibehalten möchten. Der Standardwert und der minimale Wert beträgt 8 Stunden.    
 
 > [!NOTE]
 > Höhere Werte erfordern mehr Speicherplatz auf SQL Server.
    
## <a name="permissions"></a>Berechtigungen    
 Benötigen Sie Db_owner-Berechtigungen.    
    
## <a name="remarks"></a>Hinweise    
 Rufen Sie den aktuellen Wert mit [sp_rda_get_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md).    
    
## <a name="see-also"></a>Siehe auch    
 [sys.sp_rda_get_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [Wiederherstellen von Stretch-aktivierten Datenbanken (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
