---
title: Berechtigungshierarchie (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 05cc0d47053d8ddef0962c4aceee75e61b8b4b64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211952"
---
# <a name="permissions-hierarchy-database-engine"></a>Berechtigungshierarchie (Datenbank-Engine)
  In [!INCLUDE[ssDE](../../../includes/ssde-md.md)] wird eine hierarchische Auflistung der Entitäten verwaltet, die mit Berechtigungen gesichert werden können. Diese Entitäten werden als *sicherungsfähige Elemente*bezeichnet. Die wichtigsten sicherungsfähigen Elemente sind Server und Datenbanken, diskrete Berechtigungen können jedoch auf einer viel differenzierteren Ebene festgelegt werden. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reguliert die Aktionen von Prinzipalen auf sicherungsfähigen Elementen, indem überprüft wird, ob ihnen entsprechende Berechtigungen gewährt wurden.  
  
 In der folgenden Abbildung werden die Beziehungen zwischen den [!INCLUDE[ssDE](../../../includes/ssde-md.md)] -Berechtigungshierarchien dargestellt.  
  
 ![Diagramm mit Datenbank-Engine-Berechtigungshierarchien](../../database-engine/media/wj-security-layers.gif "Diagramm mit Datenbank-Engine-Berechtigungshierarchien")  
  
## <a name="chart-of-sql-server-permissions"></a>Diagramm der SQL Server-Berechtigungen  
 Ein Diagramm mit einem Diagramm mit allen [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Berechtigungen im PDF-Format finden [https://go.microsoft.com/fwlink/?LinkId=229142](https://go.microsoft.com/fwlink/?LinkId=229142)Sie unter.  
  
## <a name="working-with-permissions"></a>Arbeiten mit Berechtigungen  
 Berechtigungen können mit den bekannten [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfragen GRANT, DENY und REVOKE geändert werden. Informationen über Berechtigungen finden Sie in den Katalogsichten [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) und [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) . Zudem wird die Abfrage von Berechtigungsinformationen mithilfe von integrierten Funktionen unterstützt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern von SQL Server](securing-sql-server.md)   
 [Berechtigungen &#40;Datenbank-Engine&#41;](permissions-database-engine.md)   
 [Sicherungs fähige Elemente](securables.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](authentication-access/principals-database-engine.md)   
 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)   
 [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL-&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)   
 [sys. server_permissions &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql)   
 [sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)  
  
  
