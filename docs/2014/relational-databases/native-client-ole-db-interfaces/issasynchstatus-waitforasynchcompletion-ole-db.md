---
title: 'Issasynchstatus:: Waitforasynchcompletion (OLE DB) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af77f5f5519a49e2d9a744dceca2857cc88ce8e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63192314"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
  Wartet, bis der asynchron ausgeführte Vorgang abgeschlossen ist oder ein Timeout auftritt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT WaitForAsynchCompletion(   
  DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *dwMillisecTimeOut*[in]  
 Timeout in Millisekunden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_UNEXPECTED  
 Ein Rowset wird nicht verwendet, da **ITransaction::Commit** oder **ITransaction::Abort** aufgerufen oder das Rowset während der ursprünglichen Initialisierungsphase abgebrochen wurde.  
  
 DB_E_CANCELED  
 Die asynchrone Verarbeitung wurde während der Auffüllung des Rowsets oder Initialisierung des Datenquellobjekts abgebrochen.  
  
 DB_S_ASYNCHRONOUS  
 Der Vorgang wurde noch nicht abgeschlossen, obwohl das angegebene Timeout erreicht wurde.  
  
> [!NOTE]  
>  Zusätzlich zu den oben aufgelisteten Rückgabecodewerten unterstützt die **ISSAsynchStatus::WaitForAsynchCompletion** -Methode auch die Rückgabecodewerte, die von der wichtigsten OLEDB **ICommand::Execute** - und **IDBInitialize::Initialize** -Methode zurückgegeben werden.  
  
## <a name="remarks"></a>Hinweise  
 Die **ISSAsynchStatus::WaitForAsynchCompletion** -Methode gibt keine Werte zurück, bis der Timeoutwert (in Millisekunden) erreicht oder der ausstehende Vorgang abgeschlossen wurde. Das **Command** -Objekt weist eine **CommandTimeout** -Eigenschaft auf, die die Anzahl der Sekunden steuert, während denen eine Abfrage ausgeführt wird, bevor ein Timeout auftritt. Die **CommandTimeout**-Eigenschaft wird ignoriert, wenn sie in Verbindung mit der **ISSAsynchStatus::WaitForAsynchCompletion**-Methode verwendet wird.  
  
 Die Timeouteigenschaft wird für asynchrone Vorgänge ignoriert. Der Timeout-Parameter **ISSAsynchStatus::WaitForAsynchCompletion** gibt die maximale Zeitspanne an, die verstreicht, bevor die Steuerung an den Aufrufer zurückgegeben wird. Wenn dieses Timeout abläuft, wird DB_S_ASYNCHRONOUS zurückgegeben. Timeouts führen nie zum Abbruch asynchroner Vorgänge. Wenn die Anwendung einen asynchronen Vorgang, der nicht innerhalb des Timeouts abgeschlossen wurde, abbrechen muss, muss sie auf das Timeout warten und, falls DB_S_ASYNCHRONOUS zurückgegeben wird, anschließend den Vorgang explizit abbrechen.  
  
> [!NOTE]  
>  Wenn die OLE DB-Dienstkomponenten verwendet werden, wird möglicherweise S_OK zurückgegeben, wenn eigentlich DB_S_ASYNCHRONOUS erwartet wird. Daher sollten Anwendungen [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) aufrufen und den Abschluss prüfen, wenn S_OK oder DB_S_ASYNCHRONOUS zurückgegeben wird.  
  
 Wenn der *dwMillisecTimeOut* -Wert auf INFINITE festgelegt wird, blockiert die **ISSAsynchStatus::WaitForAsynchCompletion** -Methode so lange, bis der Vorgang abgeschlossen ist. Wenn der *dwMillisecTimeOut* -Wert auf 0 festgelegt ist, gibt die Methode umgehend den Status des ausstehenden Vorgangs zurück. Wenn das Timeout abläuft, bevor der Vorgang abgeschlossen ist, wird DB_S_ASYNCHRONOUS zurückgegeben.  
  
 Wenn der Vorgang abgeschlossen ist, bevor das Timeout abläuft, entspricht der zurückgegebene HRESULT-Wert dem vom Vorgang zurückgegebenen HRESULT-Wert (dem HRESULT-Wert, der zurückgegeben worden wäre, wenn der Vorgang synchron ausgeführt worden wäre).  
  
 Außerdem wurde dem DBPROPSET_SQLSERVERROWSET-Eigenschaftensatz die SSPROP_ISSAsynchStatus-Eigenschaft hinzugefügt. Anbieter, die die [ISSAsynchStatus](issasynchstatus-ole-db.md)-Schnittstelle unterstützen, müssen diese Eigenschaft mit dem Wert VARIANT_TRUE implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen asynchroner Vorgänge](../native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](issasynchstatus-ole-db.md)  
  
  
