---
title: Direkte Ausführung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 725e89a937dbbd663f0e34bc24c1e8ee7e9a6eed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937270"
---
# <a name="direct-execution"></a>Direkte Ausführung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Die direkte Ausführung ist die grundlegendste Art und Weise, um eine Anweisung auszuführen. Eine Anwendung bildet eine Zeichenfolge mit Zeichen eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] Anweisung und übergibt sie zur Ausführung mit der **SQLExecDirect** Funktion. Wenn die Anweisung beim Server eingeht, kompiliert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sie zu einem Ausführungsplan, der unmittelbar ausgeführt wird.  
  
 Die direkte Ausführung wird im Allgemeinen von Anwendungen verwendet, die Anweisungen zur Laufzeit erstellen und ausführen. Es ist zugleich die effektivste Methode, Anweisungen, die nur einmal ausgeführt werden, auszuführen. Bei vielen Datenbanken muss jedoch die SQL-Anweisung bei jeder Ausführung analysiert und kompiliert werden, sodass ein zusätzlicher Aufwand entsteht, wenn die Anweisung mehrmals ausgeführt wird.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wurde die Leistung bei der direkten Ausführung von häufig ausgeführten Anweisungen in Mehrbenutzerumgebungen wesentlich verbessert. Durch den Einsatz von SQLExecDirect mit Parametermarkierungen für häufig ausgeführte SQL-Anweisungen wird zudem beinahe die gleiche Effizienz wie bei der vorbereiteten Ausführung erzielt.  
  
 Beim Verbinden mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verwendet [Sp_executesql](../../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md) zum Übertragen von SQL-Anweisung oder Batch angegeben **SQLExecDirect**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügt über eine Logik schnell eine SQL-Anweisung bestimmt, ob oder Batch ausgeführt wird, mit **Sp_executesql** entspricht der Anweisung oder der Batch, die einen Ausführungsplan, der bereits im Arbeitsspeicher generiert. Wenn eine Übereinstimmung gefunden wird, nutzt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den vorhandenen Plan, anstatt einen neuen Plan zu kompilieren. Dies bedeutet, die häufig mit ausgeführte SQL-Anweisungen ausgeführt **SQLExecDirect** in einem System mit vielen Benutzern profitieren von der Großteil der planwiederverwertungsvorteilen, die nur für gespeicherte Prozeduren, die in früheren Versionen von verfügbarwaren[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Die Vorteile der erneuten Nutzung von Ausführungsplänen können jedoch nur umgesetzt werden, wenn mehrere Benutzer die gleiche SQL-Anweisungen oder den gleichen Batch ausführen. Befolgen Sie diese Codierungskonventionen, um die Wahrscheinlichkeit zu erhöhen, dass die SQL-Anweisungen, die von unterschiedlichen Clients ausgeführt werden, sich soweit ähneln, dass die Ausführungspläne wiederverwendet werden können:  
  
-   Schließen Sie keine Datenkonstanten in die SQL-Anweisungen ein, verwenden Sie stattdessen an Programmvariablen gebundene Parametermarkierungen. Weitere Informationen finden Sie unter [Verwenden von Anweisungsparametern](../../../relational-databases/native-client-odbc-queries/using-statement-parameters.md).  
  
-   Verwenden Sie vollqualifizierte Objektnamen. Ausführungspläne werden nicht wiederverwendet, wenn Objektnamen nicht qualifiziert sind.  
  
-   Sorgen Sie dafür, dass Anwendungsverbindungen sofern möglich einen gemeinsamen Satz an Verbindungs- und Anweisungsoptionen verwenden. Ausführungspläne, die für eine Verbindung mit einem Optionssatz (z. B. ANSI_NULLS) generiert werden, werden nicht für Verbindungen mit einem anderen Optionssatz wiederverwendet. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber und der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter haben die gleichen Standardeinstellungen für diese Optionen.  
  
 Wenn alle Anweisungen mit einem ausgeführt **SQLExecDirect** werden diesen Konventionen codiert, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Ausführungspläne wiederverwenden, wenn die Möglichkeit entsteht.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Anweisungen &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
