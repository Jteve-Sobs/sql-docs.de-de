---
title: Entfernen einer erweiterten gespeicherten Prozedur aus SQLServer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
ms.openlocfilehash: f69de90386263df8b2be4638e257dcf58cf5dad7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064297"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Entfernen einer erweiterten gespeicherten Prozedur aus SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 So löschen Sie jede Funktion der erweiterten gespeicherten Prozedur in einer benutzerdefinierten erweiterten gespeicherten Prozedur-DLL einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss vom Systemadministrator ausgeführt der **Sp_dropextendedproc** gespeicherte Systemprozedur, die den Namen eines der Funktion und den Namen der DLL an, in dem sich die Funktion befindet. Angenommen, dieser Befehl entfernt die Funktion **Xp_hello**befindet sich in einer DLL, die mit dem Namen xp_hello.dll befindet, vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 Beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **Sp_dropextendedproc** erweiterte gespeicherte Systemprozeduren nicht gelöscht. Stattdessen sollte der Systemadministrator EXECUTE-Berechtigung für die erweiterte gespeicherte Prozedur zum Verweigern der **öffentliche** Rolle.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
