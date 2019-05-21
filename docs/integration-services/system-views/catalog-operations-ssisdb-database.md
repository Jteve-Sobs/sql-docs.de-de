---
title: catalog.operations (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- operations view [Integration Services]
- catalog.operations view [Integration Services]
ms.assetid: 9455c5b1-60ff-45fc-8599-cc3abbd6daf5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3692261ca636f85b7e0ebb03812eb31bdd2164b9
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65714408"
---
# <a name="catalogoperations-ssisdb-database"></a>catalog.operations (SSISDB-Datenbank)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt die Details aller Vorgänge im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Katalog an.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|operation_id|**bigint**|Der eindeutige Bezeichner (ID) des Vorgangs.|  
|operation_type|**smallint**|Der Typ des Vorgangs.|  
|created_time|**datetimeoffset**|Der Zeitpunkt, zu dem der Vorgang erstellt wurde.|  
|object_type|**smallint**|Der Typ des von dem Vorgang betroffenen Objekts. Bei dem Objekt kann es sich um einen Ordner (`10`), ein Projekt (`20`), ein Paket (`30`), eine Umgebung (`40`) oder eine Instanz der Ausführung (`50`) handeln.|  
|object_id|**bigint**|Die ID des von dem Vorgang betroffenen Objekts.|  
|object_name|**nvarchar(260)**|Der Name des Objekts.|  
|status|**ssNoversion**|Der Status des Vorgangs. Die möglichen Werte lauten "erstellt" (`1`), "wird ausgeführt" (`2`), "abgebrochen" (`3`), "fehlerhaft" (`4`), "ausstehend" (`5`), "unerwartet beendet" (`6`), "erfolgreich" (`7`), "wird beendet" (`8`) und "abgeschlossen" (`9`).|  
|start_time|**datetimeoffset**|Der Zeitpunkt, zu dem der Vorgang begonnen wurde.|  
|end_time|**datetimeoffsset**|Der Zeitpunkt, zu dem der Vorgang beendet wurde.|  
|caller_sid|**varbinary(85)**|Die Sicherheits-ID (SID) des Benutzers, wenn für die Anmeldung Windows-Authentifizierung verwendet wurde.|  
|caller_name|**nvarchar(128)**|Der Name des Kontos, das den Vorgang ausgeführt hat.|  
|process_id|**ssNoversion**|Ggf. die Prozess-ID des externen Prozesses.|  
|stopped_by_sid|**varbinary(85)**|Die SID des Benutzers, der den Vorgang beendet hat.|  
|stopped_by_name|**nvarchar(128)**|Der Name des Benutzers, der den Vorgang beendet hat.|  
|server_name|**nvarchar(128)**|Die Informationen zu Windows Server und zu Instanzen für eine angegebene Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|machine_name|**nvarchar(128)**|Der Name des Computers, auf dem die Serverinstanz ausgeführt wird.|  
  
## <a name="remarks"></a>Remarks  
 In dieser Sicht wird eine Zeile für jeden Vorgang im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Katalog angezeigt. Sie ermöglicht es dem Administrator, alle logischen Operationen aufzuzählen, die auf dem Server ausgeführt wurden, z. B. das Bereitstellen eines Projekts oder das Ausführen eines Pakets.  
  
 In dieser Sicht werden die folgenden Vorgangstypen angezeigt, wie in der Spalte **operation_type** aufgelistet:  
  
|Wert von**operation_type** |Beschreibung von**operation_type** |Beschreibung von**object_id** |Beschreibung von**object_name** |  
|-------------------------------|-------------------------------------|--------------------------------|----------------------------------|  
|`1`|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Initialisierung|**NULL**|**NULL**|  
|`2`|Beibehaltungsdauer<br /><br /> (SQL-Agent-Auftrag)|**NULL**|**NULL**|  
|`3`|MaxProjectVersion<br /><br /> (SQL-Agent-Auftrag)|**NULL**|**NULL**|  
|`101`|**deploy_project**<br /><br /> (Gespeicherte Prozedur)|Projekt-ID|Projektname|  
|`106`|**restore_project**<br /><br /> (Gespeicherte Prozedur)|Projekt-ID|Projektname|  
|`200`|**create_execution** und **start_execution**<br /><br /> (Gespeicherte Prozeduren)|Projekt-ID|**NULL**|  
|`202`|**stop_operation**<br /><br /> (Gespeicherte Prozedur)|Projekt-ID|**NULL**|  
|`300`|**validate_project**<br /><br /> (Gespeicherte Prozedur)|Projekt-ID|Projektname|  
|`301`|**validate_package**<br /><br /> (Gespeicherte Prozedur)|Projekt-ID|Paketname|  
|`1000`|**configure_catalog**<br /><br /> (Gespeicherte Prozedur)|**NULL**|**NULL**||  
  
## <a name="permissions"></a>Berechtigungen  
 Diese Sicht erfordert eine der folgenden Berechtigungen:  
  
-   READ-Berechtigung für den Vorgang  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
> [!NOTE]  
>  Wenn Sie über die Berechtigung verfügen, einen Vorgang auf dem Server auszuführen, verfügen Sie auch über die Berechtigung, Informationen zu dem Vorgang anzuzeigen. Sicherheit auf Zeilenebene wird erzwungen. Es werden nur Zeilen angezeigt, zu deren Anzeige Sie berechtigt sind.  
  
  
