---
title: 'Issasynchstatus:: Waitforasynchcompletion (OLE DB) | Microsoft-Dokumentation'
description: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
apitype: COM
helpviewer_keywords:
- WaitForAsynchCompletion method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 6df61043aae6f86ab4c632c58323e4d670cfcd7c
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030027"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a>ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

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
 Die asynchrone Verarbeitung wurde während der Auffüllung des Rowsets oder der Initialisierung des Datenquellobjekts abgebrochen.  
  
 DB_S_ASYNCHRONOUS  
 Der Vorgang wurde noch nicht abgeschlossen, obwohl das angegebene Timeout erreicht wurde.  
  
> [!NOTE]  
>  Zusätzlich zu den oben aufgelisteten Rückgabecodewerten unterstützt die **ISSAsynchStatus::WaitForAsynchCompletion** -Methode auch die Rückgabecodewerte, die von der wichtigsten OLEDB **ICommand::Execute** - und **IDBInitialize::Initialize** -Methode zurückgegeben werden.  
  
## <a name="remarks"></a>Remarks  
 Die **ISSAsynchStatus::WaitForAsynchCompletion** -Methode gibt keine Werte zurück, bis der Timeoutwert (in Millisekunden) erreicht oder der ausstehende Vorgang abgeschlossen wurde. Das **Command** -Objekt weist eine **CommandTimeout** -Eigenschaft auf, die die Anzahl der Sekunden steuert, während denen eine Abfrage ausgeführt wird, bevor ein Timeout auftritt. Die **CommandTimeout**-Eigenschaft wird ignoriert, wenn sie in Verbindung mit der **ISSAsynchStatus::WaitForAsynchCompletion**-Methode verwendet wird.  
  
 Die Timeouteigenschaft wird für asynchrone Vorgänge ignoriert. Der Timeout-Parameter **ISSAsynchStatus::WaitForAsynchCompletion** gibt die maximale Zeitspanne an, die verstreicht, bevor die Steuerung an den Aufrufer zurückgegeben wird. Wenn dieses Timeout abläuft, wird DB_S_ASYNCHRONOUS zurückgegeben. Timeouts führen nie zum Abbruch asynchroner Vorgänge. Wenn die Anwendung einen asynchronen Vorgang, der nicht innerhalb des Timeouts abgeschlossen wurde, abbrechen muss, muss sie auf das Timeout warten und, falls DB_S_ASYNCHRONOUS zurückgegeben wird, anschließend den Vorgang explizit abbrechen.  
  
> [!NOTE]  
>  Wenn die OLE DB-Dienstkomponenten verwendet werden, wird möglicherweise S_OK zurückgegeben, wenn eigentlich DB_S_ASYNCHRONOUS erwartet wird. Daher sollten Anwendungen [ISSAsynchStatus::GetStatus](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) aufrufen und den Abschluss prüfen, wenn S_OK oder DB_S_ASYNCHRONOUS zurückgegeben wird.  
  
 Wenn der *dwMillisecTimeOut* -Wert auf INFINITE festgelegt wird, blockiert die **ISSAsynchStatus::WaitForAsynchCompletion** -Methode so lange, bis der Vorgang abgeschlossen ist. Wenn der *dwMillisecTimeOut* -Wert auf 0 festgelegt ist, gibt die Methode umgehend den Status des ausstehenden Vorgangs zurück. Wenn das Timeout abläuft, bevor der Vorgang abgeschlossen ist, wird DB_S_ASYNCHRONOUS zurückgegeben.  
  
 Wenn der Vorgang abgeschlossen ist, bevor das Timeout abläuft, entspricht der zurückgegebene HRESULT-Wert dem vom Vorgang zurückgegebenen HRESULT-Wert (dem HRESULT-Wert, der zurückgegeben worden wäre, wenn der Vorgang synchron ausgeführt worden wäre).  
  
 Außerdem wurde dem DBPROPSET_SQLSERVERROWSET-Eigenschaftensatz die SSPROP_ISSAsynchStatus-Eigenschaft hinzugefügt. Anbieter, die die [ISSAsynchStatus](../../oledb/ole-db-interfaces/issasynchstatus-ole-db.md)-Schnittstelle unterstützen, müssen diese Eigenschaft mit dem Wert VARIANT_TRUE implementieren.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Ausführen asynchroner Vorgänge](../../oledb/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
