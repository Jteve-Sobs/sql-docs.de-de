---
title: Sp_enumdsn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_enumdsn
- sp_enumdsn_TSQL
helpviewer_keywords:
- sp_enumdsn
ms.assetid: 171cbc7d-7406-4cb0-8602-9405243bfd1d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5f58a16b3d4d393a94dc5e42413ddfeb2a8eb5d9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62520923"
---
# <a name="spenumdsn-transact-sql"></a>sp_enumdsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste aller definierten ODBC- und OLE DB-Datenquellennamen für einen Server zurück, der unter einem bestimmten [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzerkonto ausgeführt wird. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_enumdsn  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Datenquellenname**|**sysname**|Name der Datenquelle.|  
|**Beschreibung**|**varchar(255)**|Beschreibung der Datenquelle.|  
|**Typ**|**int**|Typ der Datenquelle:<br /><br /> **1** = ODBC DSN<br /><br /> **3** = OLE DB-Datenquelle|  
|**Name des Anbieters**|**varchar(255)**|Name des OLE DB-Anbieters. Der Wert ist NULL für einen ODBC-DSN.|  
  
## <a name="remarks"></a>Hinweise  
 Jede [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienst verfügt über einen Benutzerkontext. Dabei handelt es sich um eine Gruppe von Registrierungseinträgen, die Definitionen der ODBC-Datenquellen für den Benutzer enthält. Der Benutzerkontext ergibt sich aus dem Benutzernamen, unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
 Wenn beispielsweise der Server unter dem Benutzerkontext des Systemkontos ausgeführt wird, werden alle diesem Konto zugeordneten System-DSNs gemeldet. Wird der Server unter einem privaten Benutzerkonto ausgeführt, so werden nur die für dieses Konto definierten DSNs zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_enumdsn**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_dsninfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dsninfo-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
