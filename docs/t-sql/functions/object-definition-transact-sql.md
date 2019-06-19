---
title: OBJECT_DEFINITION (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OBJECT_DEFINITION_TSQL
- OBJECT_DEFINITION
dev_langs:
- TSQL
helpviewer_keywords:
- viewing source text
- source text [SQL Server]
- displaying source text
- OBJECT_DEFINITION function
ms.assetid: 2ac837c7-eca9-4d29-b06e-72e30450c68d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: a681af6603cdb7c69f91222e03b8a5c326ea2ffe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944057"
---
# <a name="objectdefinition-transact-sql"></a>OBJECT_DEFINITION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Quelltext der Definition eines angegebenen Objekts zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
OBJECT_DEFINITION ( object_id )  
```  
  
## <a name="arguments"></a>Argumente  
 *object_id*  
 Die ID des zu verwendenden Objekts. *object_id* ist vom Datentyp **int**; und es wird davon ausgegangen, dass dadurch ein Objekt im aktuellen Datenbankkontext dargestellt wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 **nvarchar(max)**  
  
## <a name="exceptions"></a>Ausnahmen  
 Gibt NULL bei einem Fehler zurück oder wenn ein Aufrufer nicht über Berechtigungen zum Anzeigen des Objekts verfügt.  
  
 Ein Benutzer kann nur die Metadaten sicherungsfähiger Elemente anzeigen, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Dies bedeutet, dass Metadaten ausgebende integrierte Funktionen, z. B. OBJECT_DEFINITION, möglicherweise NULL zurückgeben, wenn dem Benutzer für das Objekt keine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] setzt voraus, dass sich *object_id* im aktuellen Datenbankkontext befindet. Die Sortierung der Objektdefinition entspricht immer der des aufrufenden Datenbankkontexts.  
  
 OBJECT_DEFINITION gilt für folgende Objekttypen:  
  
-   C = CHECK-Einschränkung  
  
-   D = Standard (Einschränkung oder eigenständig)  
  
-   P = Gespeicherte SQL-Prozedur  
  
-   FN = SQL-Skalarfunktion  
  
-   R = Regel  
  
-   RF = Replikationsfilterprozedur  
  
-   TR = SQL-Trigger (DML-Trigger mit Schemabereich oder DDL-Trigger entweder im Datenbank- oder Serverbereich)  
  
-   IF = SQL-Inlinefunktion mit Tabellenrückgabe  
  
-   TF = SQL-Tabellenwertfunktionen  
  
-   V = Sicht  
  
## <a name="permissions"></a>Berechtigungen  
 Definitionen von Systemobjekten sind öffentlich sichtbar. Die Definition von Benutzerobjekten ist für den Objektbesitzer sichtbar oder für Berechtigte, die über eine der folgenden Berechtigungen verfügen: ALTER, CONTROL, TAKE OWNERSHIP oder VIEW DEFINITION. Über diese Berechtigungen verfügen implizit Mitglieder der festen Datenbankrollen **db_owner**, **db_ddladmin**und **db_securityadmin** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-the-source-text-of-a-user-defined-object"></a>A. Zurückgeben des Quelltexts eines benutzerdefinierten Objekts  
 Im folgenden Beispiel wird die Definition des benutzerdefinierten Triggers `uAddress`im `Person` -Schema zurückgegeben. Die integrierte Funktion `OBJECT_ID` wird verwendet, um die Objekt-ID des Triggers der `OBJECT_DEFINITION` -Anweisung zurückzugeben.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'Person.uAddress')) AS [Trigger Definition];   
GO  
```  
  
### <a name="b-returning-the-source-text-of-a-system-object"></a>B. Zurückgeben des Quelltexts eines Systemobjekts  
 Im folgenden Beispiel wird die Definition der gespeicherten Systemprozedur `sys.sp_columns`zurückgegeben.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECT_DEFINITION (OBJECT_ID(N'sys.sp_columns')) AS [Object Definition];  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Metadata Functions &#40;Transact-SQL&#41; (Metadatenfunktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)  
  
  
