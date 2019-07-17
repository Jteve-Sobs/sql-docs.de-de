---
title: linked_logins (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dfde20205de71a302c7ba8151fc6171cecc05a08
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140681"
---
# <a name="syslinkedlogins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile pro Verbindungsserver-Anmeldungszuordnung zurück und wird von Remoteprozeduraufrufen (Remote Procedure Call, RPC) und verteilten Abfragen vom lokalen Server zum entsprechenden Verbindungsserver verwendet.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID des Servers in **sys.servers**.|  
|**local_principal_id**|**int**|Serverprinzipal, für den die Zuordnung gilt.<br /><br /> 0 = Platzhalter oder public.|  
|**uses_self_credential**|**bit**|Wenn der Wert 1 ist, gibt die Zuordnung für die Sitzung an, dass die eigenen Anmeldeinformationen verwendet werden sollen. Ist der Wert 0, verwendet die Sitzung den Namen und das Kennwort, die bereitgestellt sind.|  
|**remote_name**|**sysname**|Remotebenutzername, der beim Herstellen einer Verbindung verwendet wird. Das Kennwort wird auch gespeichert, jedoch nicht in den Katologsichtschnittstellen verfügbar gemacht.|  
|**modify_date**|**datetime**|Datum, an dem die verknüpfte Anmeldung zuletzt geändert wurde.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Verbindungsserver-Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  
