---
title: Unterstützen lokaler Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b75104940cca183005f8a465ea19d0a517247c25
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213818"
---
# <a name="supporting-local-transactions"></a>Unterstützen lokaler Transaktionen
  Eine Sitzung begrenzt den Transaktionsbereich für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter lokale Transaktion. Wenn Sie auf die Richtung eines Consumers das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter sendet eine Anforderung an eine verbundene Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Anforderung besteht, eine Arbeitseinheit für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter. Lokale Transaktionen umschließen stets eine oder mehrere Arbeitseinheiten in einem einzigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-anbietersitzung.  
  
 Über das standardmäßige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Autocommit-Modus eine einzelne Arbeitseinheit als Bereich einer lokalen Transaktion behandelt. Nur eine Einheit nimmt an der lokalen Transaktion teil. Wenn eine Sitzung erstellt wird, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter beginnt eine Transaktion für die Sitzung. Nach der erfolgreichen Verarbeitung einer Arbeitseinheit wird ein Commit für die Arbeit ausgeführt. Bei Auftreten eines Fehlers wird ein Rollback für den begonnenen Teil der Arbeit ausgeführt, und der Fehler wird dem Consumer gemeldet. In beiden Fällen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter beginnt eine neue lokale Transaktion für die Sitzung aus, damit die gesamte Arbeit in einer Transaktion durchgeführt wird.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Consumer kann eine bessere Kontrolle über den lokalen Transaktionsbereich weiterleiten, mit der **ITransactionLocal** Schnittstelle. Wenn eine Consumersitzung eine Transaktion initiiert, werden alle Arbeitseinheiten der Sitzung zwischen dem Anfangspunkt der Transaktion und eventuellen Aufrufen der Methode **Commit** oder der Methode **Abort** als eine unteilbare Einheit behandelt. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird implizit eine Transaktion, wenn Sie dazu aufgefordert werden, vom Consumer beginnt. Wenn der Consumer keine Beibehaltung anfordert, kehrt die Sitzung zum Verhalten der übergeordneten Transaktionsebene zurück, in der Regel ist das der Autocommitmodus.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt **ITransactionLocal:: StartTransaction** Parameter wie folgt.  
  
|Parameter|Description|  
|---------------|-----------------|  
|*isoLevel*[in]|Die innerhalb dieser Transaktion zu verwendende Isolationsstufe. In lokalen Transaktionen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt die folgenden:<br /><br /> -ISOLATIONLEVEL_UNSPECIFIED<br />-   ISOLATIONLEVEL_CHAOS<br />-ISOLATIONLEVEL_READUNCOMMITTED<br />-ISOLATIONLEVEL_READCOMMITTED<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_CURSORSTABILITY<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_SERIALIZABLE FESTGELEGT IST<br />-   ISOLATIONLEVEL_ISOLATED<br />-ISOLATIONLEVEL_SNAPSHOT **beachten:**  Beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT gilt für die *IsoLevel* Argument, und zwar unabhängig davon, ob die versionsverwaltung für die Datenbank aktiviert ist. Jedoch tritt ein Fehler auf, wenn der Benutzer versucht, eine Anweisung auszuführen und die Versionsverwaltung nicht aktiviert und/oder die Datenbank nicht schreibgeschützt ist. Zudem tritt bei einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version, die älter als [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ist, der Fehler XACT_E_ISOLATIONLEVEL auf, wenn ISOLATIONLEVEL_SNAPSHOT als *isoLevel* angegeben wird.|  
|*isoFlags*[in]|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt einen Fehler für einen anderen Wert als 0 (null) zurück.|  
|*pOtherOptions*[in]|Wenn nicht NULL ist, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter das Optionsobjekt anfordert, von der Schnittstelle. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt xact_e_notimeout zurück, wenn des optionsobjekts *UlTimeout* Member ist nicht 0 (null). Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ignoriert den Wert von der *SzDescription* Member.|  
|*pulTransactionLevel*[out]|Wenn nicht NULL ist, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt die Schachtelungsebene der Transaktion zurück.|  
  
 Für lokale Transaktionen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert **ITransaction:: Abort** Parameter wie folgt.  
  
|Parameter|Description|  
|---------------|-----------------|  
|*pboidReason*[in]|Wird bei Festlegung ignoriert. Kann daher auch NULL sein.|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Bei "FALSE" die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird für die Sitzung den Autocommit-Modus zurückgesetzt.|  
|*fAsync*[in]|Asynchroner Abbruch wird nicht von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt xact_e_notsupported zurück, wenn der Wert nicht "false" ist.|  
  
 Für lokale Transaktionen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert **ITransaction:: Commit** Parameter wie folgt.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*fRetaining*[in]|Wenn der Wert TRUE lautet, wird eine neue Transaktion implizit für die Sitzung begonnen. Für die Transaktion muss vom Consumer ein Commit ausgeführt werden oder sie muss beendet werden. Bei "FALSE" die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wird für die Sitzung den Autocommit-Modus zurückgesetzt.|  
|*grfTC*[in]|Asynchrone Rückkehr und die Rückkehr zu Phase eins werden nicht unterstützt, indem die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter gibt xact_e_notsupported zurück, für jeden Wert xact_e_notsupported.|  
|*grfRM*[in]|Muss den Wert 0 (null) haben.|  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Rowsets in der Sitzung bleiben bei einem lokalen Commit- oder Abbruchvorgang je nach den Werten für die Rowseteigenschaften DBPROP_ABORTPRESERVE und dbprop_commitpreserve beibehalten. Standardmäßig sind diese Eigenschaften beide VARIANT_FALSE und alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter Rowsets in der Sitzung verloren, befolgen einen Abbruch oder Commit-Vorgang.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter implementiert nicht die **ITransactionObject** Schnittstelle. Bei einem Versuch des Consumers, einen Verweis auf die Schnittstelle abzurufen, wird E_NOINTERFACE zurückgegeben.  
  
 Im folgenden Beispiel wird **ITransactionLocal** verwendet.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Transaktionen](transactions.md)   
 [Arbeiten mit der Momentaufnahmeisolation](../native-client/features/working-with-snapshot-isolation.md)  
  
  
