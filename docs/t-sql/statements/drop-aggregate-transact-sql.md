---
title: DROP AGGREGATE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_AGGREGATE_TSQL
- DROP AGGREGATE
dev_langs:
- TSQL
helpviewer_keywords:
- aggregate functions [SQL Server], removing
- removing user-defined functions
- dropping user-defined functions
- user-defined functions [CLR integration]
- deleting user-defined functions
- DROP AGGREGATE statement
ms.assetid: 84ffc4e7-c451-4f1f-9a67-7fc3a120e53f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7c96206e70c39d1d69cc30e8f7f464352dbe3522
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882427"
---
# <a name="drop-aggregate-transact-sql"></a>DROP AGGREGATE (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt eine benutzerdefinierte Aggregatfunktion aus der aktuellen Datenbank. Benutzerdefinierte Aggregatfunktionen werden mithilfe von [CREATE AGGREGATE](../../t-sql/statements/create-aggregate-transact-sql.md) erstellt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
DROP AGGREGATE [ IF EXISTS ] [ schema_name . ] aggregate_name  
```  
  
## <a name="arguments"></a>Argumente  
 *IF EXISTS*  
 **Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis zur [aktuellen Version](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Löscht das Aggregat nur, wenn diese bereits vorhanden ist.  
  
 *schema_name*  
 Der Name des Schemas, zu dem die benutzerdefinierte Aggregatfunktion gehört.  
  
 *aggregate_name*  
 Der Name der benutzerdefinierten Aggregatfunktion, die Sie löschen möchten.  
  
## <a name="remarks"></a>Bemerkungen  
 DROP AGGREGATE wird nicht ausgeführt, wenn mit einer Schemabindung erstellte Sichten, Funktionen oder gespeicherte Prozeduren vorhanden sind, die auf die benutzerdefinierte Aggregatfunktion verweisen, die Sie löschen möchten.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen von DROP AGGREGATE benötigt der Benutzer mindestens die ALTER-Berechtigung für das Schema, zu dem das benutzerdefinierte Aggregat gehört, oder die CONTROL-Berechtigung für das Aggregat.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das `Concatenate`-Aggregat gelöscht.  
  
```  
DROP AGGREGATE dbo.Concatenate;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE AGGREGATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-aggregate-transact-sql.md)   
 [Erstellen benutzerdefinierter Aggregate](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md)  
  
  
