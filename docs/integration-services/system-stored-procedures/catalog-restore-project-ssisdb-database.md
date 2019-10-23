---
title: catalog.restore_project (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d131ebd8d532e0844774fc675165750832f964c9
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295461"
---
# <a name="catalogrestore_project-ssisdb-database"></a>catalog.restore_project (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Stellt die frühere Version eines Projekts im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog wieder her.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>Argumente  
 [ @folder_name = ] *folder_name*  
 Der Name des Ordners, der das Projekt enthält. Der *folder_name* ist **nvarchar(128)** .  
  
 [ @project _name = ] *project_name*  
 Der Name des Projekts. Der *project_name* ist **nvarchar(128)** .  
  
 [ @object_version_lsn = ] *object_version_lsn*  
 Die Version des Projekts. Der *object_version_lsn* ist **bigint**.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn der **project_name** gefunden wird, werden Projektdetails als *varbinary(MAX)* im Resultset zurückgegeben.  
  
 Wenn das Projekt nicht im angegebenen Ordner wiederhergestellt werden kann, wird**NO RESULT SET** zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung und MODIFY-Berechtigung für das Projekt  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 In der folgenden Liste werden einige Bedingungen beschrieben, die möglicherweise einen Fehler oder eine Warnung auslösen:  
  
-   Die Projektversion ist nicht vorhanden oder entspricht nicht dem Projektnamen.  
  
-   Das Projekt ist nicht vorhanden.  
  
-   Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.  
  
## <a name="remarks"></a>Remarks  
 Wenn ein Projekt wiederhergestellt wird, werden allen Parametern Standardwerte zugewiesen, und alle Umgebungsverweise bleiben unverändert. Die maximale Anzahl von Projektversionen, die im Katalog beibehalten werden, wird durch die Katalogeigenschaft **MAX_VERSIONS_PER_PROJECT**bestimmt, wie in der [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) -Sicht gezeigt.  
  
> [!WARNING]  
>  Umgebungsverweise sind möglicherweise nicht mehr gültig, nachdem ein Projekt wiederhergestellt wurde.  
  
  
