---
title: Erstellen benutzerdefinierter Aggregate | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: c278b746-6323-4b32-b460-239915acc067
author: rothja
ms.author: jroth
ms.openlocfilehash: d66db5586f5f80f8f0e8954d041befbcd4c5eba4
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053629"
---
# <a name="create-user-defined-aggregates"></a>Erstellen benutzerdefinierter Aggregate
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]
  Sie können ein Datenbankobjekt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellen, das in einer CLR-Assembly programmiert wird. Datenbankobjekte, die das reichhaltige Programmiermodell nutzen können, das von der CLR (Common Language Runtime) bereitgestellt wird, sind z. B. Trigger, gespeichert Prozeduren, Funktionen, Aggregatfunktionen und Typen.  
  
 Ebenso wie die integrierten Aggregatfunktionen, die in [!INCLUDE[tsql](../../includes/tsql-md.md)]bereitgestellt werden, führen benutzerdefinierte Aggregatfunktionen Berechnungen für eine Menge von Werten aus und geben einen einzelnen Wert zurück.  
  
 Das Erstellen einer benutzerdefinierten Aggregatfunktion in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst die folgenden Schritte:  
  
-   Definieren der benutzerdefinierten Aggregatfunktion als Klasse in einer von [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework unterstützten Sprache. Weitere Informationen zum Programmieren benutzerdefinierter Aggregate in der CLR finden Sie unter [Benutzerdefinierte CLR-Aggregate](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md). Kompilieren dieser Klasse mithilfe des entsprechenden Sprachcompilers, um eine Assembly zu erstellen.  
  
-   Registrieren der Assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der CREATE ASSEMBLY-Anweisung. Weitere Informationen zum Arbeiten mit Assemblys in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Assemblys &#40;Datenbank-Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md).  
  
-   Erstellen des benutzerdefinierten Aggregats, das auf die registrierte Assembly verweist, mithilfe der CREATE AGGREGATE-Anweisung.  
  
> [!NOTE]
>  Bei der Bereitstellung eines SQL Server-Projekts in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] wird eine Assembly in der Datenbank registriert, die für das Projekt angegeben wurde. Beim Bereitstellen des Projekts wird in der Datenbank auch ein benutzerdefiniertes Aggregat für alle Klassendefinitionen erstellt, die mit dem **SqlUserDefinedAggregate** -Attribut versehen sind. Weitere Informationen finden Sie unter [Deploying CLR Database Objects](../../relational-databases/clr-integration/deploying-clr-database-objects.md).  
> 
> [!NOTE]
>  Die Funktion zum Ausführen von CLR-Code ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] standardmäßig deaktiviert. Sie können Datenbankobjekte, die auf verwaltete Codemodule verweisen, erstellen, ändern oder löschen; diese Verweise werden jedoch nur dann in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt, wenn die [clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) -Option mithilfe von [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)aktiviert wird.  
  
 **So erstellen, ändern oder löschen Sie eine Assembly**  
  
-   [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
  
-   [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)  
  
-   [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  
 **So erstellen Sie ein benutzerdefiniertes Aggregat**  
  
-   [CREATE AGGREGATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-aggregate-transact-sql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierkonzepte für die Integration der Common Language Runtime &#40;CLR&#41;](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
