---
title: database_mirroring_endpoints (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring_endpoints_TSQL
- database_mirroring_endpoints
- sys.database_mirroring_endpoints
- database_mirroring_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], endpoint
- HADR [SQL Server], endpoint
- database mirroring [SQL Server], catalog views
- sys.database_mirroring_endpoints catalog view
ms.assetid: f2285199-97ad-473c-a52d-270044dd862b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bcbe9d23bab18e47b69f82812f604a94d4c5ce9c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022767"
---
# <a name="sysdatabasemirroringendpoints-transact-sql"></a>sys.database_mirroring_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für den Datenbankspiegelungs-Endpunkt einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Der datenbankspiegelungs-Endpunkt unterstützt Sitzungen zwischen Datenbank-spiegelungspartnern und Zeugen und Sitzungen zwischen dem primären Replikat einer Always On-verfügbarkeitsgruppe und dessen sekundären Replikaten.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**\<geerbte Spalten >**|-|Erbt Spalten von **sys.endpoints** (Weitere Informationen finden Sie unter [sys.endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)).|  
|**Rolle**|**tinyint**|Spiegelungsrolle. Folgende Werte sind möglich:<br /><br /> **0** = keine<br /><br /> **1** = Partner<br /><br /> **2** = Witness<br /><br /> **3** = all<br /><br /> Hinweis: Dieser Wert ist nur für die datenbankspiegelung relevant.|  
|**role_desc**|**nvarchar(60)**|Beschreibung der Spiegelungsrolle. Folgende Werte sind möglich:<br /><br /> **NONE**<br /><br /> **PARTNER**<br /><br /> **ZEUGE**<br /><br /> **ALL**<br /><br /> Hinweis: Dieser Wert ist nur für die datenbankspiegelung relevant.|  
|**is_encryption_enabled**|**bit**|**1** bedeutet, datenverschlüsselung aktiviert ist.<br /><br /> **0** bedeutet, dass die Verschlüsselung deaktiviert ist.|  
|**connection_auth**|**tinyint**|Der Typ von Verbindungsauthentifizierung, der für Verbindungen mit diesem Endpunkt erforderlich ist. Folgende Werte sind möglich:<br /><br /> **1** -NTLM<br /><br /> **2** – KERBEROS<br /><br /> **3** -AUSHANDLUNG<br /><br /> **4** -ZERTIFIKAT<br /><br /> **5** -NTLM, ZERTIFIKAT<br /><br /> **6** -KERBEROS, ZERTIFIKAT<br /><br /> **7** -AUSHANDELN, ZERTIFIKAT<br /><br /> **8** -ZERTIFIKAT, NTLM<br /><br /> **9** -ZERTIFIKAT, KERBEROS<br /><br /> **10** -ZERTIFIKAT, AUSHANDELN|  
|**connection_auth_desc**|**Nvarchar (60)**|Beschreibung des Authentifizierungstyps, der für Verbindungen mit diesem Endpunkt erforderlich ist. Folgende Werte sind möglich:<br /><br /> NTLM<br /><br /> KERBEROS<br /><br /> NEGOTIATE<br /><br /> CERTIFICATE<br /><br /> NTLM, CERTIFICATE<br /><br /> KERBEROS, CERTIFICATE<br /><br /> NEGOTIATE, CERTIFICATE<br /><br /> CERTIFICATE, NTLM<br /><br /> CERTIFICATE, KERBEROS<br /><br /> CERTIFICATE, NEGOTIATE|  
|**certificate_id**|**int**|Gegebenenfalls ID des für die Authentifizierung verwendeten Zertifikats.<br /><br /> 0 = Windows-Authentifizierung wird verwendet.|  
|**encryption_algorithm**|**tinyint**|Verschlüsselungsalgorithmus. Folgende Werte sind möglich:<br /><br /> **0** -KEINE<br /><br /> **1** -RC4<br /><br /> **2** -AES<br /><br /> **3** -KEINER, RC4<br /><br /> **4** -KEINER, AES<br /><br /> **5** -RC4, AES<br /><br /> **6** -AES, RC4<br /><br /> **7** -KEINER, RC4, AES<br /><br /> **8** -KEINER, AES, RC4|  
|**encryption_algorithm_desc**|**nvarchar(60)**|Beschreibung des Verschlüsselungsalgorithmus. Folgende Werte sind möglich:<br /><br /> Keine<br /><br /> RC4<br /><br /> AES<br /><br /> NONE, RC4<br /><br /> NONE, AES<br /><br /> RC4, AES<br /><br /> AES, RC4<br /><br /> NONE, RC4, AES<br /><br /> NONE, AES, RC4|  
  
## <a name="remarks"></a>Hinweise  
  
> [!NOTE]  
>  Der RC4-Algorithmus wird nur aus Gründen der Abwärtskompatibilität unterstützt. Neues Material kann nur mit RC4 oder RC4_128 verschlüsselt werden, wenn die Datenbank den Kompatibilitätsgrad 90 oder 100 besitzt. (Nicht empfohlen.) Verwenden Sie stattdessen einen neueren Algorithmus, z. B. einen der AES-Algorithmen. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher mit RC4 oder RC4_128 verschlüsseltes Material in jedem Kompatibilitätsgrad entschlüsselt werden kann.  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Geben Sie die Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQLServer&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)   
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [sys.database_mirroring &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Häufig gestellte Fragen zu Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
