---
title: Abrufen einer einzelnen Zeile mit IRow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [SQL Server Native Client]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 07c803ca-299a-42c5-ba02-360b9631d15f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dff71f35374df8988e73b958c8b4d476c28b8fbf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064022"
---
# <a name="fetching-a-single-row-with-irow"></a>Abrufen einer einzelnen Zeile mit IRow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Die **IRow** -schnittstellenimplementierung die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter wurde vereinfacht, um die Leistung zu steigern. **IRow** lässt den direkten Zugriff auf Spalten eines einzelnen Zeilenobjekts zu. Wenn Sie vorab wissen, dass das Ergebnis einer Befehlsausführung genau eine Zeile erzeugt, dann lassen sich mit **IRow** die Spalten dieser Zeile abrufen. Wenn das Resultset mehrere Zeilen umfasst, macht **IRow** nur die erste Zeile verfügbar.  
  
 Die **IRow**-Implementierung lässt keine Navigation in der Zeile zu. Jede Spalte in der Zeile erfolgt nur einmal mit einer Ausnahme: Eine Spalte kann nur einmal auf die Spaltengröße zu ermitteln und wieder zum Abrufen der Daten zugegriffen werden.  
  
> [!NOTE]  
>  **IRow::Open** unterstützt nur das Öffnen von Objekten des Typs DBGUID_STREAM und DBGUID_NULL.  
  
 IID_IRow muss übergeben werden, um ein Zeilenobjekt mithilfe der **ICommand::Execute**-Methode zu erhalten. Die **IMultipleResults**-Schnittstelle muss zur Behandlung mehrerer Resultsets verwendet werden. **IMultipleResults** unterstützt **IRow** und **IRowset**. **IRowset** wird für Massenvorgänge verwendet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von IRow::GetColumns](../../relational-databases/native-client-ole-db-rowsets/using-irow-getcolumns.md)  
  
-   [Abrufen von BLOB-Daten mit IRow](https://msdn.microsoft.com/library/badbd6ac-20aa-4891-a14f-48d38e7f30de)  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
