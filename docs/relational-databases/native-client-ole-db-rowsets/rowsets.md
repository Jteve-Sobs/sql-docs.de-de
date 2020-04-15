---
title: Rowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da51990e310b7903ce90d0369e30ff098103e141
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300248"
---
# <a name="rowsets"></a>Rowsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ein Rowset ist ein Satz von Zeilen, die Spalten mit Daten enthalten. Rowsets sind die zentralen Objekte, die es allen OLE DB-Datenanbietern ermöglichen, Resultsetdaten in tabellarischer Form verfügbar zu machen.  
  
 Nachdem ein Consumer mithilfe der **IDBCreateSession::CreateSession**-Methode eine Sitzung erstellt hat, kann er entweder mit der **IOpenRowset**-Schnittstelle oder der **IDBCreateCommand**-Schnittstelle ein Rowset erstellen. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt beide Schnittstellen. Diese beiden Methoden werden im Folgenden beschrieben.  
  
-   Erstellen Sie ein Rowset, indem Sie die **IOpenRowset::OpenRowset**-Methode aufrufen.  
  
     Dies entspricht dem Erstellen eines Rowsets über eine einzelne Tabelle. Die Methode öffnet ein Rowset, das alle Zeilen aus einer einzelnen Basistabelle enthält, und gibt es zurück. Eines der Argumente von **OpenRowset** ist eine Tabellen-ID, die die Tabelle identifiziert, aus der das Rowset erstellt werden soll.  
  
-   Erstellen Sie ein Befehlsobjekt, indem Sie die **IDBCreateCommand::CreateCommand**-Methode aufrufen.  
  
     Das Befehlsobjekt führt Befehle aus, die der Anbieter unterstützt. Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter kann der Consumer eine beliebige [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung angeben, beispielsweise eine SELECT-Anweisung oder einen Aufruf einer gespeicherten Prozedur. Die Schritte zum Erstellen eines Rowsets mit einem Befehlsobjekt sind folgende:  
  
    1.  Der Consumer ruft die **IDBCreateCommand::CreateCommand**-Methode der Sitzung auf, um ein Befehlsobjekt zu erhalten, das die **ICommandText**-Schnittstelle für das Befehlsobjekt anfordert. Diese **ICommandText**-Schnittstelle legt den eigentlichen Befehlstext fest und ruft ihn ab. Der Consumer gibt den Textbefehl ein, indem er die **ICommandText::SetCommandText**-Methode aufruft.  
  
    2.  Der Benutzer ruft die **ICommand::Execute**-Methode für den Befehl auf. Das Rowsetobjekt, das erstellt wird, wenn der Befehl ausgeführt wird, enthält das Resultset aus dem Befehl.  
  
 Der Consumer kann die **ICommandProperties**-Schnittstelle verwenden, um die Eigenschaften des Rowsets, das von dem in den **ICommand::Execute**-Schnittstellen ausgeführten Befehl zurückgegeben wurde, abzurufen oder festzulegen. Die am häufigsten angeforderten Eigenschaften sind die Schnittstellen, die das Rowset unterstützen muss. Zusätzlich zu Schnittstellen kann der Consumer Eigenschaften anfordern, die das Verhalten des Rowsets oder der Schnittstelle verändern.  
  
 Consumer geben Rowsets mit der **IRowset::Release**-Methode frei. Mit der Freigabe eines Rowsets werden alle Zeilenhandles freigegeben, die der Consumer für dieses Rowset besitzt. Accessoren werden jedoch bei der Freigabe eines Rowsets nicht freigegeben. Wenn Sie über eine **IAccessor**-Schnittstelle verfügen, muss diese noch freigegeben werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Erstellen eines Rowsets mit 'IopenRowset'](../../relational-databases/native-client-ole-db-rowsets/creating-a-rowset-with-iopenrowset.md)  
  
-   [Erstellen von Rowsets mit ICommand::Execute](../../relational-databases/native-client-ole-db-rowsets/creating-rowsets-with-icommand-execute.md)  
  
-   [Eigenschaften und Verhaltensweisen von Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
-   [Rowsets und SQL Server-Cursor](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)  
  
-   [Abrufen von Zeilen](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Abrufen einer einzelnen Zeile mit IRow](../../relational-databases/native-client-ole-db-rowsets/fetching-a-single-row-with-irow.md)  
  
-   [Lesezeichen](../../relational-databases/native-client-ole-db-rowsets/bookmarks.md)  
  
-   [Aktualisieren von Daten in Rowsets](../../relational-databases/native-client-ole-db-rowsets/updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
