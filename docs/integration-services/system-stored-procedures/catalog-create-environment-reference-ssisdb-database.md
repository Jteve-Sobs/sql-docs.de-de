---
description: catalog.create_environment_reference (SSISDB-Datenbank)
title: catalog.create_environment_reference (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dcca4fd25fd201c9b278107dce188b6cab12d866
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477117"
---
# <a name="catalogcreate_environment_reference-ssisdb-database"></a>catalog.create_environment_reference (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Erstellt einen Umgebungsverweis für ein Projekt im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.create_environment_reference [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @environment_name = ] environment_name  
     , [ @reference_type = ] reference_type  
  [  , [ @environment_folder_name = ] environment_folder_name ]  
  [  , [ @reference_id = ] reference_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @folder_name = ] *folder_name*  
 Der Name des Ordners des Projekts, das auf die Umgebung verweist. Der *folder_name* ist **nvarchar(128)** .  
  
 [ @project_name = ] *project_name*  
 Der Name des Projekts, das auf die Umgebung verweist. Der *project_name* ist **nvarchar(128)** .  
  
 [ @environment_name = ] *environment_name*  
 Der Name der Umgebung, auf die verwiesen wird. Der *environment_name* ist **nvarchar(128)** .  
  
 [ @reference_type = ] *reference_type*  
 Gibt an, ob sich die Umgebung im gleichen Ordner wie das Projekt (relativer Verweis) oder in einem anderen Ordner (absoluter Verweis) befinden kann. Verwenden Sie den Wert `R` , um einen relativen Verweis anzugeben. Verwenden Sie den Wert `A` , um einen absoluten Verweis anzugeben. Der *reference_type* ist **char(1)** .  
  
 [ @environment_folder_name = ] *environment_folder_name*  
 Der Name des Ordners, in dem sich die Umgebung befindet, auf die verwiesen wird. Dieser Wert ist für absolute Verweise erforderlich. Der *environment_folder_name* ist **nvarchar(128)** .  
  
 [ @reference_id = ] *reference_id*  
 Gibt den eindeutigen Bezeichner für den neuen Verweis zurück. Dieser Parameter ist optional. Der *reference_id* ist **bigint**.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung und MODIFY-Berechtigung für das Projekt und READ-Berechtigung für die Umgebung  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Der Ordnername ist ungültig.  
  
-   Der Projektname ist ungültig.  
  
-   Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.  
  
-   Im `A` -Parameter wird mit dem Zeichen *A* ein absoluter Verweis angegeben, jedoch wurde im *environment_folder_name* -Parameter nicht der Name des Ordners angegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Projekt kann über relative oder absolute Umgebungsverweise verfügen. Relative Verweise verweisen mit dem Namen auf die Umgebung und erfordern, dass sich diese im gleichen Ordner wie das Projekt befindet. Absolute Verweise verweisen mit Name und Ordner auf die Umgebung und verweisen möglicherweise auf Umgebungen, die sich in einem anderen Ordner als das Projekt befinden. Ein Projekt kann auf mehrere Umgebungen verweisen.  
  
  
