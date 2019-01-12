---
title: Sp_serveroption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_serveroption_TSQL
- sp_serveroption
dev_langs:
- TSQL
helpviewer_keywords:
- 7343 (Database Engine error)
- sp_serveroption
ms.assetid: 47d04a2b-dbf0-4f15-bd9b-81a2efc48131
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1d947f319c56c29c0d3dbe4ce88c38055c59dfc5
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124110"
---
# <a name="spserveroption-transact-sql"></a>sp_serveroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt Serveroptionen für Remoteserver und Verbindungsserver fest.  
  
 
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_serveroption [@server = ] 'server'   
      ,[@optname = ] 'option_name'       
      ,[@optvalue = ] 'option_value' ;  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@server =** ] **"**_Server_**"**  
 Der Name des Servers für den die Option festgelegt werden soll. *server* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 [  **@optname =** ] **"**_Optionsname_**"**  
 Die Option, die für den angegebenen Server festgelegt werden soll. *Option_name* ist **Varchar (** 35 **)**, hat keinen Standardwert. *Option_name* kann eines der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**Sortierung kompatibel**|Betrifft die Ausführung verteilter Abfragen für Verbindungsserver. Wenn diese Option, um festgelegt ist **"true"**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird davon ausgegangen, dass alle Zeichen auf dem Verbindungsserver mit dem lokalen Server, bezüglich Zeichensatz und Sortierreihenfolge (Sortierreihenfolge) kompatibel sind. Dies ermöglicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Vergleiche für Zeichenspalten an den Provider zu senden. Wird diese Option nicht festgelegt, werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Vergleiche für Zeichenspalten immer lokal ausgewertet.<br /><br /> Diese Option sollte nur festgelegt werden, wenn sicher ist, dass die Datenquelle, die dem Verbindungsserver entspricht, den gleichen Zeichensatz und die gleiche Sortierreihenfolge wie der lokale Server verwendet.|  
|**Sortierungsname**|Gibt den Namen der Sortierung von der Remotedatenquelle verwendet wird, wenn **Remotesortierung verwenden** ist **"true"** und die Datenquelle ist keiner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenquelle. Der Name muss eine von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützte Sortierung sein.<br /><br /> Verwenden Sie diese Option, wenn auf eine OLE DB-Datenquelle zugegriffen wird, die keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle ist, deren Sortierung jedoch mit einer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sortierungen übereinstimmt.<br /><br /> Der Verbindungsserver muss eine einzige Sortierung unterstützen, die für alle Spalten in diesem Server verwendet wird. Legen Sie diese Option nicht fest, wenn der Verbindungsserver mehrere Sortierungen in einer einzelnen Datenquelle unterstützt oder wenn festgestellt wird, dass die Sortierung des Verbindungsservers nicht mit einer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sortierungen übereinstimmt.|  
|**Verbindungstimeout**|Timeout Varied Sekunden für die Verbindung mit einem verknüpften Server.<br /><br /> Wenn **0**, verwenden Sie die **Sp_configure** Standard.|  
|**Datenzugriff**|Aktiviert und deaktiviert den Zugriff auf verteilte Abfragen für Verbindungsserver. Kann verwendet werden, nur für **sys.server** Einträge hinzugefügt, die über **Sp_addlinkedserver**.|  
|**dist**|Der Verteiler.|  
|**Verzögerte schemaüberprüfung**|Bestimmt, ob das Schema von Remotetabellen überprüft wird.<br /><br /> Wenn **"true"**, überspringen Sie die schemaüberprüfung von Remotetabellen zu Beginn der Abfrage.|  
|**pub**|Herausgeber.|  
|**Abfragetimeout**|Der Timeoutwert für Abfragen auf einem Verbindungsserver.<br /><br /> Wenn **0**, verwenden Sie die **Sp_configure** Standard.|  
|**rpc**|Aktiviert RPC von dem betreffenden Server.|  
|**RPC-Ausgabe**|Aktiviert RPC zu dem betreffenden Server.|  
|**sub**|Der Abonnent ist.|  
|**System**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Remotesortierung verwenden**|Bestimmt, ob die Sortierung einer Remotespalte oder eines lokalen Servers verwendet wird.<br /><br /> Wenn **"true"**, die Sortierung der Remotespalten wird zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellen und der im angegebenen Sortierung **Sortierungsname** dient für nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellen.<br /><br /> Wenn **"false"**, verwenden verteilte Abfragen immer die standardsortierung des lokalen Servers, während **Sortierungsname** und die Sortierung der Remotespalten werden ignoriert. Der Standardwert ist **false**. (Die **"false"** Wert ist mit der im verwendeten sortierungssemantik kompatibel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.)|  
|**Remote Proc Transaction promotion**|Verwenden Sie diese Option, um die Aktionen einer Server-zu-Server-Prozedur durch eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator-Transaktion (MS DTC) zu schützen. Wenn diese Option auf true festgelegt ist (oder ON) Aufruf einer remote gespeicherten Prozedur wird eine verteilte Transaktion gestartet und bei MS DTC eingetragen. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, die die remote gespeicherte Prozedur aufruft, wird als Transaktionsurheber bezeichnet und steuert die Beendigung der Transaktion. Wenn im Anschluss eine COMMIT TRANSACTION- oder ROLLBACK TRANSACTION-Anweisung für die Verbindung ausgegeben wird, fordert die steuernde Instanz MS DTC auf, die Beendigung der verteilten Transaktion auf den beteiligten Computern zu verwalten.<br /><br /> Nachdem eine verteilte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Transaktion gestartet wurde, können Aufrufe remote gespeicherter Prozeduren für weitere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanzen erfolgen, die als Verbindungsserver definiert wurden. Alle Verbindungsserver werden in der verteilten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Transaktion eingetragen, und MS DTC stellt sicher, dass die Transaktion für jeden Verbindungsserver abgeschlossen wird.<br /><br /> Wenn diese Option auf FALSE (oder OFF) festgelegt ist, wird eine lokale Transaktion beim Aufruf einer remote gespeicherten Prozedur für einen Verbindungsserver nicht zu einer verteilten Transaktion höher gestuft.<br /><br /> Falls die Transaktion vor dem Server-zu-Server-Prozeduraufruf bereits eine verteilte Transaktion ist, hat diese Option keine Auswirkung. Der Prozeduraufruf für einen Verbindungsserver wird unter der gleichen verteilten Transaktion ausgeführt.<br /><br /> Falls vor dem Server-zu-Server-Prozeduraufruf keine Transaktion in der Verbindung aktiv ist, hat diese Option keine Auswirkung. Die Prozedur wird dann für einen Verbindungsserver ohne aktive Transaktionen ausgeführt.<br /><br /> Der Standardwert für diese Option ist TRUE (oder ON).|  
  
 [  **@optvalue =**] **"**_Option_value_**"**  
 Gibt an, ob die *Optionsname* aktiviert werden soll (**"true"** oder **auf**) oder deaktiviert (**"false"** oder **aus**). *Option_value* ist **Varchar (** 10 **)**, hat keinen Standardwert.  
  
 *Option_value* möglicherweise eine nicht negative ganze Zahl, für die **Verbindungstimeout** und **Abfragetimeout** Optionen. Für die **Sortierungsname** Option *Option_value* kann eine Name-Sortierung oder NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Wenn die **Sortierreihenfolge kompatibel** Option auf "true" gesetzt ist **Sortierungsname** automatisch auf NULL festgelegt. Wenn **Sortierungsname** auf einen Wert ungleich NULL festgelegt ist **Sortierreihenfolge kompatibel** automatisch auf "false" festgelegt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert ALTER ANY LINKED SERVER-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Verbindungsserver, der einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz (`SEATTLE3`) entspricht, so konfiguriert, dass seine Sortierung mit der Sortierung der lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz kompatibel ist.  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilte Abfragen, gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [Sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [Sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
