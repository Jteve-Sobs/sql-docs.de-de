---
title: MSSQL_ENG020596 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: e50ddcc92b2000ae5aa4894966565651c722162a
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362393"
---
# <a name="mssql_eng020596"></a>MSSQL_ENG020596
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Meldungsdetails  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|20596|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Nur '%s' und Mitglieder der db_owner-Rolle können den anonymen Agent löschen.|  
  
## <a name="explanation"></a>Erklärung  
 Sie besitzen nicht die erforderlichen Berechtigungen, um den Agent für das anonyme Abonnement zu löschen. Der Anmeldename, der zum Aufrufen von [sp_dropanonymousagent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md) verwendet wird, muss Mitglied der festen **sysadmin**-Serverrolle auf dem Verteiler bzw. Mitglied der festen **db_owner**-Datenbankrolle in der Verteilungsdatenbank sein, oder der Benutzer muss derjenige sein, der die erstmalige Ausführung des Agents initialisiert hat.  
  
## <a name="user-action"></a>Benutzeraktion  
 Melden Sie sich mit den entsprechenden Anmeldeinformationen an, und führen Sie **sp_dropanonymousagent**aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
