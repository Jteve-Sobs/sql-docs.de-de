---
title: Datenquellenobjekte (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f3ad8fa44e5222406f16be09a6157f96fac6b345
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128682"
---
# <a name="data-source-objects-ole-db"></a>Datenquellenobjekte (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client verwendet die Laufzeit die Datenquelle für die Gruppe der OLE DB-Schnittstellen verwendet, um einen Link zu einem Datenspeicher, z. B. herzustellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Erstellen einer Instanz das Datenquellenobjekt des Anbieters ist die erste Aufgabe von einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Consumers.  
  
 Jeder OLE DB-Anbieter deklariert einen Klassenbezeichner (CLSID) für sich. Die CLSID für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist der C /C++ -GUID CLSID_SQLNCLI10 (das Symbol in den richtigen sqlncli_clsid wird progid in der Datei sqlncli.h aufgelöst, die Sie referenzieren). Mit der CLSID verwendet der Consumer die OLE-Funktion **CoCreateInstance** zum Erstellen einer Instanz des Datenquellenobjekts.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ist eine in-Process-Server. Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieterobjekten werden erstellt mithilfe des CLSCTX_INPROC_SERVER-Makros zu den ausführbaren Kontext anzugeben.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellenobjekt für Native Client OLE DB-Anbieter macht die OLE DB-Initialisierungsschnittstellen bereit, mit denen den Consumer die Verbindung zu vorhandenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
 Jede Verbindung, die über die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter legt die folgenden Optionen automatisch fest:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Dieses Beispiel verwendet das klassenbezeichnermakro zum Erstellen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieterdaten Datenquellenobjekts und zum Abrufen eines Verweises auf die **IDBInitialize** Schnittstelle.  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 Mit der erfolgreichen Erstellung einer Instanz von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter-Datenquellenobjekts kann die Consumeranwendung fortfahren, durch die Datenquelle initialisiert und Sitzungen erstellt werden. OLE DB-Sitzungen präsentieren die Schnittstellen, die Datenzugriff und -bearbeitung ermöglichen.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter stellt die erste Verbindung zu einer angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Teil einer erfolgreichen datenquelleninitialisierung. Die Verbindung wird beibehalten, solange eine Referenz auf einer beliebigen Datenquellen-Initialisierungsschnittstelle beibehalten wird oder bis die Methode **IDBInitialize::Uninitialize** aufgerufen wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Datenquelleneigenschaften &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Eigenschaften von Datenquelleninformationen](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Initialisierungs- und Autorisierungseigenschaften](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sitzungen](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [OLE DB-Anbieter von SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Persistente Datenquellenobjekte](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
