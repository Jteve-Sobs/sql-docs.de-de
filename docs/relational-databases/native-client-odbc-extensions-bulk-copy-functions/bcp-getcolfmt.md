---
title: bcp_getcolfmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_getcolfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7e279af67313107d495e5ef864414e53997c3cff
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86010112"
---
# <a name="bcp_getcolfmt"></a>bcp_getcolfmt
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Zum Suchen des Spaltenformat-Eigenschaftswerts.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_getcolfmt (  
        HDBC hdbc,  
        INT field,  
        INT property,  
        void* pValue,  
        INT cbvalue,  
        INT* pcbLen);  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *Flächen*  
 Die Spaltenzahl, für die die Eigenschaft abgerufen wird.  
  
 *property*  
 Eine der Eigenschaftskonstanten.  
  
 *pValue*  
 Der Verweis auf den Puffer, von dem der Eigenschaftswert abgerufen werden soll.  
  
 *cbValue*  
 Die Länge des Puffers der Eigenschaft in Bytes.  
  
 *pcbLen*  
 Verweis auf Länge der Daten, die im Eigenschaftspuffer zurückgegeben werden.  
  
## <a name="returns"></a>Rückgabe  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Spalten Format-Eigenschaftswerte sind im Thema [bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md) aufgeführt. Die Spalten Format-Eigenschaftswerte werden durch Aufrufen der **bcp_setcolfmt** -Funktion festgelegt, und die **bcp_getcolfmt** -Funktion wird verwendet, um den Eigenschafts Wert des Spalten Formats zu suchen.  
  
 Verhaltensänderungen werden möglicherweise beim Herstellen einer Verbindung mit einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Server Computer (oder höher) im Vergleich zu früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Versionen beobachtet. Weitere Informationen finden Sie unter [Metadatenermittlung](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_getcolfmt-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Die Typen, die mit der **BCP_FMT_TYPE** -Eigenschaft für Datums-/Uhrzeittypen verwendet werden, sind wie in [Massen Kopier Änderungen für verbesserte Datums-und Uhrzeit Typen &#40;OLE DB und ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)angegeben.  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
