---
title: Sp_article_validation (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_article_validation_TSQL
- sp_article_validation
helpviewer_keywords:
- sp_article_validation
ms.assetid: 44e7abcd-778c-4728-a03e-7e7e78d3ce22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 849564fcda37c022413d9e0758abe50279497a0b
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125110"
---
# <a name="sparticlevalidation-transact-sql"></a>sp_article_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Initiiert eine Datenüberprüfungsanforderung für den angegebenen Artikel. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank und auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_article_validation [ @publication = ] 'publication'  
    [ , [ @article = ] 'article' ]  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @subscription_level = ] subscription_level ]  
    [ , [ @reserved = ] reserved ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=**] **"**_Veröffentlichung_**"**  
 Der Name der Veröffentlichung, in der der Artikel vorhanden ist. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@article=**] **"**_Artikel_**"**  
 Der Name des zu überprüfenden Artikels. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@rowcount_only=**] *Type_of_check_requested*  
 Gibt an, ob nur die Zeilenanzahl für die Tabelle zurückgegeben wird. *Type_of_check_requested* ist **Smallint**, hat den Standardwert **1**.  
  
 Wenn **0**, eine Zeilenzählung und eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 kompatible prüfsummenberechnung.  
  
 Wenn **1**, nur eine Zeilenzählung durchgeführt.  
  
 Wenn **2**, Zeilenanzahl und binäre Prüfsumme.  
  
 [  **@full_or_fast=**] *Full_or_fast*  
 Die Methode, mit der die Zeilenanzahl berechnet wird. *Full_or_fast* ist **Tinyint**, und kann einen der folgenden Werte sein.  
  
|**Wert**|**Beschreibung**|  
|---------------|---------------------|  
|**0**|Führt eine vollständige Zählung mit COUNT(*).|  
|**1**|Führt eine schnelle Zählung von **sysindexes.rows**. Zählen der Zeilen im **"sysindexes"** ist schneller als das Zählen von Zeilen in der eigentlichen Tabelle. Allerdings **"sysindexes"** verzögert aktualisiert wird und die Zeilenanzahl möglicherweise nicht ganz genau.|  
|**2** (Standardwert)|Führt die bedingte schnelle Zählung durch zunächst versucht wird, die schnelle Methode. Ergeben sich mit der schnellen Methode Unterschiede, wird die Methode für die vollständige Zählung verwendet. Wenn *Expected_rowcount* NULL ist und die gespeicherte Prozedur wird verwendet, um den Wert abzurufen, wird immer eine vollständige Zählung mit COUNT(*) verwendet.|  
  
 [  **@shutdown_agent=**] *Shutdown_agent*  
 Gibt an, wenn der Verteilungs-Agent sofort nach dem Abschluss der Überprüfung heruntergefahren werden soll. *Shutdown_agent* ist **Bit**, hat den Standardwert **0**. Wenn **0**, den Verteilungs-Agent nicht heruntergefahren. Wenn **1**, den Verteilungs-Agent nach der Überprüfung des Artikels beendet.  
  
 [  **@subscription_level=**] *Subscription_level*  
 Gibt an, ob die Überprüfung von einem Satz von Abonnenten abgerufen wird. *Subscription_level* ist **Bit**, hat den Standardwert **0**. Wenn **0**, Überprüfung auf alle Abonnenten angewendet. Wenn **1**, Überprüfung wird nur angewendet, um eine Teilmenge der Abonnenten durch Aufrufe von angegeben **Sp_marksubscriptionvalidation** in die aktuell geöffnete Transaktion.  
  
 [  **@reserved=**] *reserviert*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@publisher**=] **"**_Verleger_**"**  
 Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, bei der Überprüfung auf Anforderung eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_article_validation** wird in Transaktionsreplikationen verwendet.  
  
 **Sp_article_validation** bewirkt, dass Überprüfungsinformationen für den angegebenen Artikel gesammelt werden und eine überprüfungsanforderung in das Transaktionsprotokoll geschrieben. Wenn der Verteilungs-Agent diese Anforderung empfängt, vergleicht er die Überprüfungsinformationen in der Anforderung mit der Abonnententabelle. Die Ergebnisse der Überprüfung werden im Replikationsmonitor und in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Warnungen angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Benutzer mit allen Berechtigungen für die Quelltabelle auswählen, für die zu überprüfende Artikel kann **Sp_article_validation**.  
  
## <a name="see-also"></a>Siehe auch  
 [Überprüfen von replizierten Daten](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [Sp_marksubscriptionvalidation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)   
 [Sp_publication_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [Sp_table_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
