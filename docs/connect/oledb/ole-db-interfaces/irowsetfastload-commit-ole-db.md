---
title: IRowsetFastLoad::Commit (OLE DB-Treiber) | Microsoft-Dokumentation
description: IRowsetFastLoad::Commit (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IRowsetFastLoad::Commit (OLE DB)
apitype: COM
helpviewer_keywords:
- Commit method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 6c932947a77d2170dd1e92c47c19f5ff3959cba9
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244453"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Markiert das Ende eines Batches eingefügter Zeilen und schreibt die Zeilen in die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle. Beispiele finden Sie unter [Massenkopieren von Daten mithilfe von IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) und [Senden von BLOB-Daten an SQL SERVER mit IROWSETFASTLOAD und ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT Commit(  
      BOOL fDone);  
```  
  
## <a name="arguments"></a>Argumente  
 *fDone*[in]  
 Wenn FALSE angegeben wird, behält das Rowset seine Gültigkeit und kann vom Consumer zum Einfügen zusätzlicher Zeilen verwendet werden. Wird TRUE angegeben, dann verliert das Rowset seine Gültigkeit, und der Consumer kann keine weiteren Einfügungen vornehmen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt, und alle eingefügten Daten wurden in die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle geschrieben.  
  
 E_FAIL  
 Es ist ein anbieterspezifischer Fehler aufgetreten. Rufen Sie Fehlerinformationen für den betreffenden Fehlertext vom Anbieter ab.  
  
 E_UNEXPECTED  
 Die Methode wurde für ein Rowset für das Massenkopieren aufgerufen, das zuvor von der **IRowsetFastLoad::Commit**-Methode für ungültig erklärt wurde.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein vom OLE DB-Treiber für SQL Server erstelltes Rowset für das Massenkopieren verhält sich wie ein Rowset für den verzögerten Updatemodus. Wenn der Benutzer Zeilendaten über das Rowset einfügt, dann werden die eingefügten Zeilen so behandelt wie ausstehende Einfügungen in einem Rowset, das **IRowsetUpdate** unterstützt.  
  
 Der Consumer muss die **Commit**-Methode für das Rowset für das Massenkopieren ebenso aufrufen, um die eingefügten Zeilen in die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle zu schreiben, wie mithilfe der **IRowsetUpdate::Update-Methode** ausstehende Zeilen an eine Instanz von SQL Server gesendet werden.  
  
 Wenn der Consumer seinen Verweis auf das Rowset für das Massenkopieren freigibt, ohne die **Commit**-Methode aufzurufen, gehen alle Zeilen verloren, die vorher nicht in die Tabelle geschrieben wurden.  
  
 Der Consumer kann die eingefügten Zeilen als Batch definieren, indem er die **Commit**-Methode aufruft und das *fDone*-Argument auf FALSE festlegt. Wenn *fDone* auf TRUE festgelegt wird, wird das Rowset ungültig. Ein ungültiges Rowset für das Massenkopieren unterstützt nur die **ISupportErrorInfo**-Schnittstelle und die **IRowsetFastLoad::Release**-Methode.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  
