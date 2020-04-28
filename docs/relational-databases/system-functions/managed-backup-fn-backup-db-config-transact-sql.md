---
title: managed_backup. fn_backup_db_config (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_backup_db_config
- smart_admin.fn_backup_db_config_TSQL
- fn_backup_db_config
- fn_backup_db_config_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_db_config
- fn_backup_db_config
ms.assetid: 7c755d8a-64dd-44b2-be5e-735d30758900
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a23f8eb64ae99b999cdf6b16f1c888383a88c147
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68067782"
---
# <a name="managed_backupfn_backup_db_config-transact-sql"></a>managed_backup. fn_backup_db_config (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gibt keine, eine oder mehrere Zeilen mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Konfigurationseinstellungen zurück. Gibt eine Zeile für die angegebene Datenbank oder die Informationen für alle Datenbanken zurück, die auf der Instanz mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfiguriert sind.  
  
 Verwenden Sie diese gespeicherte Prozedur, um die aktuellen [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Konfigurationseinstellungen für eine Datenbank oder alle Datenbanken in einer SQL Server-Instanz zu überprüfen oder zu ermitteln.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
managed_backup.fn_backup_db_config ('database_name' | '' | NULL)  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumentation  
 @db_name  
 Der Name der Datenbank. Der @db_name Parameter ist vom **Datentyp sysname**. Wenn eine leere Zeichenfolge oder ein NULL-Wert an diesen Parameter übergeben wird, werden die Informationen über alle Datenbanken in der SQL Server-Instanz zurückgegeben.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|db_name|SYSNAME|Datenbankname.|  
|db_guid|UNIQUEIDENTIFIER|Ein Bezeichner, der die Datenbank eindeutig identifiziert.|  
|is_availability_database|BIT|Gibt an, ob die Datenbank einer Verfügbarkeitsgruppe angehört. Der Wert 1 gibt an, dass die Datenbank eine Verfügbarkeitsdatenbank ist, der Wert 0, dass dies nicht der Fall ist.|  
|is_dropped|BIT|Der Wert 1 gibt an, dass es sich um eine gelöschte Datenbank handelt.|  
|credential_name|SYSNAME|Der Name der SQL-Anmeldeinformationen, der zur Authentifizierung beim Speicherkonto verwendet wird. Ein NULL-Wert gibt an, dass keine SQL-Anmeldeinformationen festgelegt sind.|  
|retention_days|INT|Die aktuelle Beibehaltungsdauer in Tagen. Ein NULL-Wert gibt an, dass [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nie für diese Datenbank konfiguriert wurde.|  
|is_managed_backup_enabled|INT|Gibt an, ob [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] derzeit für diese Datenbank aktiviert ist. Der Wert 1 gibt an, dass [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] derzeit aktiviert ist, der Wert 0 gibt an, dass [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] für diese Datenbank deaktiviert ist.|  
|storage_url|Nvarchar (1024)|Die URL des Speicherkontos.|  
|Encryption_algorithm|NCHAR (20)|Gibt den aktuellen Verschlüsselungsalgorithmus zurück, der beim Verschlüsseln der Sicherung verwendet werden soll.|  
|Encryptor_type|NCHAR(15)|Gibt die Verschlüsselungseinstellung zurück: Zertifikat oder Asymmetrischer Schlüssel.|  
|Encryptor_name|NCHAR(max_length_of_cert/asymm_key_name)|Der Name des Zertifikats oder des asymmetrischen Schlüssels.|  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **db_backupoperator** -Daten Bank Rolle mit **ALTER ANY CREDENTIAL** -Berechtigungen. Dem Benutzer sollte die **View any Definition** -Berechtigung nicht verweigert werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] Konfiguration für "TestDB" zurückgegeben.  
  
 Wählen Sie für jeden Codeausschnitt "tsql" im Sprachattributfeld aus.  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config('TestDB')  
```  
  
 Im folgenden Beispiel wird die [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]-Konfiguration für alle Datenbanken in der Instanz von SQL Server zurückgegeben, für die sie ausgeführt wird.  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config (NULL)  
```  
  
  
