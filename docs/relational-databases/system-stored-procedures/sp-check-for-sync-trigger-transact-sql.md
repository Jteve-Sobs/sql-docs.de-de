---
title: Sp_check_for_sync_trigger (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef51624f3d14ef12be1c37b17727b70f5f31df10
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526422"
---
# <a name="spcheckforsynctrigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Bestimmt, ob ein benutzerdefinierter Trigger oder eine benutzerdefinierte gespeicherte Prozedur im Kontext eines Replikationstriggers aufgerufen wird, der für sofort aktualisierbare Abonnements verwendet wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@tabid =** ] '*Tabid*"  
 Die Objekt-ID der Tabelle, die auf sofort aktualisierbare Trigger überprüft wird. *Tabid* ist **Int** hat keinen Standardwert.  
  
 [ **@trigger_op =** ] '*Trigger_output_parameters*' Ausgabe  
 Gibt an, ob der Ausgabeparameter den Typ von Trigger zurückgeben muss, mit dem er aufgerufen wird. *Trigger_output_parameters* ist **char(10)** und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Ins**|INSERT-Trigger|  
|**Upd**|UPDATE-Trigger|  
|**Del**|DELETE-Trigger|  
|NULL (Standard)||  
  
`[ @fonpublisher = ] fonpublisher` Gibt den Speicherort, in dem die gespeicherte Prozedur ausgeführt wird. *Fonpublisher* ist **Bit**, hat den Standardwert 0. Bei 0 findet die Ausführung auf dem Abonnenten und bei 1 auf dem Verleger statt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 zeigt an, dass die gespeicherte Prozedur nicht im Kontext eines sofort aktualisierbaren Triggers aufgerufen wird. 1 gibt an, dass es im Kontext eines sofort aktualisierbaren Triggers aufgerufen wird, ist der Typ des Triggers, der zurückgegeben wird *@trigger_op*.  
  
## <a name="remarks"></a>Hinweise  
 **Sp_check_for_sync_trigger** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 **Sp_check_for_sync_trigger** wird verwendet, um die Koordination zwischen replikationstriggern und benutzerdefinierten Triggern. Diese gespeicherte Prozedur bestimmt, ob sie im Kontext eines Replikationstriggers aufgerufen wird. Sie können z. B. die Prozedur aufrufen **Sp_check_for_sync_trigger** im Text eines benutzerdefinierten Triggers. Wenn **Sp_check_for_sync_trigger** gibt **0**, der benutzerdefinierte Trigger setzt die Verarbeitung fort. Wenn **Sp_check_for_sync_trigger** gibt **1**, der benutzerdefinierte Trigger beendet wird. So wird sichergestellt, dass der benutzerdefinierte Trigger nicht ausgelöst wird, wenn der Replikationstrigger die Tabelle aktualisiert.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird Code dargestellt, der in einem Trigger in der Abonnententabelle verwendet werden kann.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>Beispiel  
 Der Code kann auch auf einen Trigger für eine Tabelle auf dem Verleger hinzugefügt werden; der Code ist ähnlich, aber den Aufruf von **Sp_check_for_sync_trigger** einen zusätzlichen Parameter enthält.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>Berechtigungen  
 **Sp_check_for_sync_trigger** gespeicherte Prozedur ausgeführt werden kann, von jedem Benutzer mit SELECT-Berechtigungen in der [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) -Systemsicht ab.  
  
## <a name="see-also"></a>Siehe auch  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
