---
title: Sp_adddistributor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributor
- sp_adddistributor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adddistributor
ms.assetid: 35415502-68d0-40f6-993c-180e50004f1e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8cf36a02d81b8732d80beb7c97d025a74138cd43
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716726"
---
# <a name="spadddistributor-transact-sql"></a>sp_adddistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Eintrag in der [sys.sysservers](../../relational-databases/system-compatibility-views/sys-sysservers-transact-sql.md) Tabelle (sofern es nicht), markiert ihn als Verteiler und speichert Eigenschafteninformationen. Diese gespeicherte Prozedur wird auf dem Verteiler für die master-Datenbank ausgeführt, um den Server als Verteiler zu registrieren und zu markieren. Im Falle eines Remoteverteilers wird sie zusätzlich auf dem Verleger für die master-Datenbank ausgeführt, um den Remoteverteiler zu registrieren.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adddistributor [ @distributor= ] 'distributor'   
    [ , [ @heartbeat_interval= ] heartbeat_interval ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @from_scripting= ] from_scripting ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @distributor = ] 'distributor'` Ist der verteilungsservername. *Verteiler* ist **Sysname**, hat keinen Standardwert. Dieser Parameter wird nur bei der Einrichtung eines Remoteverteilers verwendet. Er fügt die Verteilereigenschaften der **Msdb... MSdistributor** Tabelle.  
  
`[ @heartbeat_interval = ] heartbeat_interval` Ist die maximale Anzahl von Minuten an, denen ein Agent ohne Protokollierung einer verlaufsmeldung aufgenommen werden kann. *Heartbeat_interval* ist **Int**, hat den Standardwert von 10 Minuten. Ein Auftrag des SQL Server-Agents wird erstellt, der nach diesem Zeitraum ausgeführt wird, um den Status der ausgeführten Replikations-Agents zu überprüfen.  
  
`[ @password = ] 'password']` Das Kennwort des der **Distributor_admin** Anmeldung. *Kennwort* ist **Sysname**, hat den Standardwert NULL. Bei NULL oder einer leeren Zeichenfolge wird das Kennwort auf einen Zufallswert festgelegt. Das Kennwort muss konfiguriert sein, wenn der erste Remoteverteiler hinzugefügt wird. **Distributor_admin** Anmeldung und *Kennwort* werden gespeichert, für den verbindungsservereintrag für eine *Verteiler* RPC-Verbindung, einschließlich lokaler Verbindungen. Wenn *Verteiler* ist lokal, das Kennwort für **Distributor_admin** auf einen neuen Wert festgelegt ist. Für Verleger mit einem Remoteverteiler der gleiche Wert für *Kennwort* muss angegeben werden, wenn die Ausführung **Sp_adddistributor** auf sowohl dem Verleger und Verteiler. [Sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md) können verwendet werden, um das Verteilerkennwort zu ändern.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_adddistributor** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistributor-transa_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_adddistributor**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributor_property &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)  
  
  
