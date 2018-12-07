---
title: TRUSTWORTHY-Datenbankeigenschaft | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: a20d3850b281519d05769de2af5b0fd2dd1cbe85
ms.sourcegitcommit: ba7fb4b9b4f0dbfe77a7c6906a1fde574e5a8e1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "52302803"
---
# <a name="trustworthy-database-property"></a>TRUSTWORTHY-Datenbankeigenschaft
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die TRUSTWORTHY-Datenbankeigenschaft gibt an, ob die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz die Datenbank und ihre Inhalte als vertrauenswürdig einstuft. Standardmäßig ist diese Einstellung OFF; sie kann jedoch mithilfe der ALTER DATABASE-Anweisung auf ON festgelegt werden. Beispiel: `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Um diese Option festlegen zu können, müssen Sie Mitglied der festen Serverrolle **sysadmin** sein.  
  
 Diese Eigenschaft kann zum Verringern bestimmter Risiken verwendet werden, die als Ergebnis des Anfügens einer Datenbank vorhanden sein können, die eines der folgenden Objekte enthält:  
  
-   Bösartige Assemblys mit einer EXTERNAL_ACCESS- oder UNSAFE-Berechtigungseinstellung. Weitere Informationen finden Sie unter [CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
-   Bösartige Module, die für die Ausführung als Benutzer mit hohen Privilegien definiert wurden. Weitere Informationen finden Sie unter [EXECUTE AS-Klausel &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 In beiden Fällen ist eine bestimmte Berechtigungsstufe erforderlich, und es liegt ein dementsprechender Schutz durch geeignete Mechanismen vor, wenn diese im Kontext einer Datenbank verwendet werden, die bereits an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angefügt ist. Wenn die Datenbank jedoch offline geschaltet wird, kann ein Benutzer, der Zugriff auf die Datenbankdatei besitzt, diese potenziell einer Instanz seiner Wahl von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beifügen und der Datenbank auf diese Weise bösartige Inhalte hinzufügen. Wenn Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]getrennt oder angefügt werden, werden bestimmte Berechtigungen für die Daten- und Protokolldateien festgelegt, die den Zugriff auf die Datenbankdateien einschränken.  
  
 Da eine Datenbank, die einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angefügt wird, nicht sofort vertrauenswürdig ist, darf sie erst auf Ressourcen außerhalb des Bereichs der Datenbank zugreifen, wenn sie explizit als vertrauenswürdig markiert wurde. Wenn Sie eine Datenbank sichern oder trennen, bei der die Option TRUSTWORTHY auf ON festgelegt ist, und Sie die Datenbank auf derselben oder einer anderen SQL Server-Instanz anschließen oder darauf wiederherstellen, wird die Eigenschaft TRUSTWORTHY daher nach Anschließen/Wiederherstellen auf OFF festgelegt. Für Module, die für den Zugriff auf Ressourcen außerhalb der Datenbank konzipiert wurden, und Assemblys mit der EXTERNAL_ACCESS- bzw. UNSAFE-Berechtigungseinstellung müssen zusätzliche Anforderungen erfüllt werden, damit diese erfolgreich ausgeführt werden.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
