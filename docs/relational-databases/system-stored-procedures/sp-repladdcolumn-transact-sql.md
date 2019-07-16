---
title: Sp_repladdcolumn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repladdcolumn_TSQL
- sp_repladdcolumn
helpviewer_keywords:
- sp_repladdcolumn
ms.assetid: d6220f9f-c738-4f9c-bcf8-419994e86c81
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1b01a48e15c06f021b41b3bded35a0cd2739313c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006914"
---
# <a name="sprepladdcolumn-transact-sql"></a>sp_repladdcolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt eine Spalte zu einem vorhandenen Tabellenartikel hinzu, der veröffentlicht worden ist. Dadurch kann die neue Spalte zu allen Verlegern hinzugefügt werden, die diese Tabelle veröffentlichen, oder die Spalte kann ausschließlich zu einer bestimmten Veröffentlichung hinzugefügt werden, die die Tabelle veröffentlicht. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!IMPORTANT]
>  Diese gespeicherte Prozedur wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität unterstützt. Sie sollten nur mit verwendet werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Herausgeber und [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Wiederveröffentlichungsabonnenten. Diese Prozedur sollte nicht für Spalten mit Datentypen verwendet werden, die in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher eingeführt wurden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_repladdcolumn [ @source_object = ] 'source_object', [ @column = ] 'column' ]  
    [ , [ @typetext = ] 'typetext' ]  
    [ , [ @publication_to_add = ] 'publication_to_add' ]  
    [ , [ @from_agent = ] from_agent ]  
    [ , [ @schema_change_script = ] 'schema_change_script' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @source_object =] '*Source_object*"  
 Ist der Name des Tabellenartikels, der die hinzuzufügende neue Spalte enthält. *Source_object* ist **Nvarchar (358**), hat keinen Standardwert.  
  
 [ @column =] '*Spalte*"  
 Ist der Name der Spalte in der für die Replikation hinzuzufügenden Tabelle. *Spalte* ist **Sysname**, hat keinen Standardwert.  
  
 [ @typetext =] '*Typetext*"  
 Entspricht der Definition der Spalte, die hinzugefügt wird. *TypeText* ist **nvarchar(3000)** , hat keinen Standardwert. Z. B. wenn Order_filled-Spalte hinzugefügt wird, und es ist ein einzelnes Feld, das keine NULL-Zeichen und hat den Standardwert des **N**, ist order_filled der *Spalte* Parameter, während die Definition der Spalte **char(1) NOT NULL CONSTRAINT Constraint_name DEFAULT ' n '** wäre die *Typetext* Parameterwert.  
  
 [ @publication_to_add =] '*Publication_to_add*"  
 Ist der Name der Veröffentlichung, der die neue Spalte hinzugefügt wird. *Publication_to_add* ist **nvarchar(4000)** , hat den Standardwert **alle**. Wenn **alle**, und klicken Sie dann alle Veröffentlichungen, die mit dieser Tabelle betroffen sind. Wenn *Publication_to_add* angegeben ist, wird nur dieser Veröffentlichung die neue Spalte hinzugefügt wurde.  
  
 [ @from_agent =] *From_agent*  
 Gibt an, ob die gespeicherte Prozedur von einem Replikations-Agent ausgeführt wird. *From_agent* ist **Int**, hat den Standardwert **0**, der Wert des **1** wird verwendet, wenn diese gespeicherte Prozedur von einem Replikations-Agent, und in ausgeführt wird jeder andere Fall, dass den Standardwert von **0**verwendet werden soll.  
  
 [ @schema_change_script =] '*Schema_change_script*"  
 Gibt den Namen und Pfad eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Skripts an, das zum Ändern der systemgenerierten bzw. benutzerdefinierten gespeicherten Prozeduren dient. *Schema_change_script* ist **nvarchar(4000)** , hat den Standardwert NULL. Mithilfe der Replikation ist es möglich, mindestens eine der bei der Transaktionsreplikation verwendeten Standardprozeduren durch benutzerdefinierte gespeicherte Prozeduren zu ersetzen. *Schema_change_script* wird ausgeführt, nachdem eine schemaänderung erfolgt, um zu einem replizierten Tabellenartikel, die mithilfe von Sp_repladdcolumn und kann verwendet werden, um einen der folgenden Schritte aus:  
  
-   Wenn benutzerdefinierte gespeicherte Prozeduren automatisch erneut generiert werden, *Schema_change_script* dienen kann, löschen diese benutzerdefinierten gespeicherten Prozeduren, und Ersetzen Sie sie durch eine benutzerdefinierte benutzerdefinierte gespeicherte Prozeduren, die das neue Schema unterstützen.  
  
-   Wenn benutzerdefinierte gespeicherte Prozeduren nicht automatisch erneut generiert werden, *Schema_change_script*können verwendet werden, um diese gespeicherten Prozeduren neu zu generieren, oder erstellen Sie benutzerdefinierte gespeicherte Prozeduren.  
  
 [ @force_invalidate_snapshot =] *Force_invalidate_snapshot*  
 Aktiviert oder deaktiviert die Möglichkeit, eine Momentaufnahme für ungültig zu erklären. *Force_invalidate_snapshot* ist eine **Bit**, hat den Standardwert **1**.  
  
 **1** gibt an, dass Änderungen am Mergeartikel die Momentaufnahme ungültig ist, wird möglicherweise Wenn dies zutrifft, wird ein Wert von **1** die Berechtigung für das Auftreten der neuen Momentaufnahme erteilt.  
  
 **0** gibt an, dass Änderungen am Artikel bewirken nicht, die Momentaufnahme ungültig wird.  
  
 [ @force_reinit_subscription =] *Force_reinit_subscription*  
 Aktiviert oder deaktiviert die Möglichkeit, das Abonnement erneut zu initialisieren. *Force_reinit_subscription* ist eine **Bit** hat den Standardwert **0**.  
  
 **0** gibt an, dass Änderungen am Artikel bewirken nicht, das Abonnement erneut initialisiert werden.  
  
 **1** gibt an, dass Änderungen am Artikel bewirken, dass das Abonnement erneut initialisiert werden, können und wenn dies der Fall, der Wert ist **1** erteilt die Berechtigung für die Initialisierung des Abonnements erfolgen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle sysadmin und der festen Datenbankrolle db_owner können sp_repladdcolumn ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Als veraltet markierte Funktionen in SQL Server-Replikation](../../relational-databases/replication/deprecated-features-in-sql-server-replication.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
