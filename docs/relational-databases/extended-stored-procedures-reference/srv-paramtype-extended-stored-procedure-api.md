---
title: srv_paramtype (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramtype
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramtype
ms.assetid: badc6d36-8a87-42b5-b28c-9c4f5ded8552
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 073cc3f3e93bfcbce1b8914bbf3061dc7fde161d
ms.sourcegitcommit: edf7372cb674179f03a330de5e674824a8b4118f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53246669"
---
# <a name="srvparamtype-extended-stored-procedure-api"></a>srv_paramtype (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Gibt den Datentyp des Aufrufparameters für eine remote gespeicherte Prozedur zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_paramtype (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall das Handle, das den Aufruf der remote gespeicherten Prozedur erhalten hat). Die Struktur enthält Informationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren die Kommunikation und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *n*  
 Gibt die Anzahl der Parameter an. Der erste Parameter ist 1.  
  
## <a name="returns"></a>Rückgabewert  
 Ein Tokenwert für den Datentyp des Parameters. Informationen zu Datentypen finden Sie unter [Datentypen (API für erweiterte gespeicherte Prozeduren)](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md). Wenn es keinen *n*-ten Parameter oder keine remote gespeicherte Prozedur gibt, wird –1 zurückgegeben.  
  
 Diese Funktion gibt die folgenden Werte zurück, wenn der Parameter einem der Datentypen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] entspricht.  
  
|Neue Datentypen|Rückgabewert|  
|--------------------|------------------|  
|**BITN**|SRVBIT|  
|**BIGVARCHAR**|VARCHAR|  
|**BIGCHAR**|CHAR|  
|**BIGBINARY**|BINARY|  
|**BIGVARBINARY**|VARBINARY|  
|**NCHAR**|CHAR|  
|**NVARCHAR**|VARCHAR|  
|**NTEXT**|-1|  
  
## <a name="remarks"></a>Remarks  
 Wenn eine remote gespeicherte Prozedur mit Parametern aufgerufen wird, werden die Parameter entweder mit ihrem Namen oder mit ihrer Position übergeben (unbenannt). Werden beim Aufruf einer remote gespeicherten Prozedur einige Parameter über ihren Namen und andere über ihre Position übergeben, so tritt ein Fehler auf. Der SRV_RPC-Handler wird trotzdem aufgerufen, doch es sind scheinbar keine Parameter vorhanden, und **srv_rpcparams** gibt 0 zurück.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://www.microsoft.com/en-us/msrc?rtc=1).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_paraminfo (API für erweiterte gespeicherte Prozeduren)](../../relational-databases/extended-stored-procedures-reference/srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams (API für erweiterte gespeicherte Prozeduren)](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
