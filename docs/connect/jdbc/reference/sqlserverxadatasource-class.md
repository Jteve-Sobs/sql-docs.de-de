---
title: SQLServerXADataSource-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5725da0138ecec2e24f93e16af97a1d3c8a67681
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776025"
---
# <a name="sqlserverxadatasource-class"></a>SQLServerXADataSource-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine intern verwendete Factory für [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)-Objekte dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **Implementiert** javax.sql.XADataSource  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>Remarks  
 Ein Objekt, von dem die SQLServerXADataSource-Schnittstelle implementiert wird, ist normalerweise bei einem Bezeichnungsdienst registriert, der JNDI (Java Naming and Directory Interface) verwendet.  
  
 Die SQLServerXADataSource-Klasse stellt Datenbankverbindungen zur Verwendung in verteilten (XA-)Transaktionen bereit. Die SQLServerXADataSource-Klasse unterstützt außerdem Verbindungspools aus physikalischen Verbindungen. Die SQLServerXADataSource und SQLServerXAConnection-Schnittstellen, die in das Paket "javax.SQL" definiert sind, werden von implementiert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Ein SQLServerXAConnection-Objekt ist eine Poolverbindung, die Teil einer verteilten Transaktion sein kann. Genauer gesagt, erweitert SQLServerXAConnection die SQLServerPooledConnection-Schnittstelle durch Hinzufügen der Methode [GetXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md). Von dieser Methode wird ein [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)-Objekt erzeugt, das von einem Transaktions-Manager zur Koordination der Arbeit an dieser Verbindung mit den anderen Teilnehmern an der verteilten Transaktion verwendet werden kann. Da sie die SQLServerPooledConnection-Schnittstelle erweitert werden, unterstützen SQLServerXAConnection-Objekte alle Methoden von SQLServerPooledConnection-Objekten. Sie sind wiederverwendbare physikalische Verbindungen mit einer zu Grunde liegenden Datenquelle und erzeugen logische Verbindungshandles, die an eine JDBC-Anwendung zurückgegeben werden können.  
  
 SQLServerXAConnection-Objekte werden von einem SQLServerXADataSource-Objekt erstellt. SQLServerConnectionPoolDataSource und SQLServerXADataSource-Objekte sind ähnlich, da sie beide unterhalb einer Datenquellenebene implementiert sind, die in der JDBC-Anwendung sichtbar ist. Dank dieser Architektur kann [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verteilte Transaktionen auf eine Weise unterstützen, die für die Anwendung transparent ist. SQLServerXADataSource kann für die Integration mit [!INCLUDE[msCoName](../../../includes/msconame_md.md)]-DTC (Distributed Transaction Coordinator) konfiguriert werden, um echte verteilte Transaktionsverarbeitung zu ermöglichen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXADataSource-Elemente](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
