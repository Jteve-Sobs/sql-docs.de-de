---
title: Sp_syscollector_create_collector_type (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collector_type
- sp_syscollector_create_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_create_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 568e9119-b9b0-4284-9cef-3878c691de5f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f7b50d9cf05f1242ae853f7aa24e7e681bdc245f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004168"
---
# <a name="spsyscollectorcreatecollectortype-transact-sql"></a>sp_syscollector_create_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Sammlertyp für den Datensammler. Ein sammlertyp ist ein logischer Wrapper für die [!INCLUDE[ssIS](../../includes/ssis-md.md)] Pakete, die den eigentlichen Mechanismus für das Sammeln von Daten und zum Hochladen der Daten in das Verwaltungs-Datawarehouse bereitstellen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_create_collector_type   
    [ [@collector_type_uid = ] 'collector_type_uid' OUTPUT ]  
    , [ @name = ] 'name'  
    , [ [ @parameter_schema = ] 'parameter_schema' ]  
    , [ [ @parameter_formatter = ] 'parameter_formatter' ]  
    , [ @collection_package_id = ] 'collection_package_id'  
    , [ @upload_package_id = ] 'upload_package_id'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @collector_type_uid =] '*Collector_type_uid*"  
 Ist die GUID für den sammlertyp. *Collector_type_uid* ist **Uniqueidentifier** und wenn es NULL ist, es wird automatisch erstellt und als Ausgabe zurückgegeben.  
  
 [ @name =] '*Namen*"  
 Der Name des Sammlertyps. *Namen* ist **Sysname** und muss angegeben werden.  
  
 [ @parameter_schema = ] '*parameter_schema*'  
 Das XML-Schema für diesen Sammlertyp. *Parameter_schema* ist **Xml** hat den Standardwert NULL.  
  
 [ @parameter_formatter =] '*Parameter_formatter*"  
 Die Vorlage, mit der das XML für die Eigenschaftenseite des Sammlungssatzes umgewandelt werden kann. *Parameter_formatter* ist **Xml** hat den Standardwert NULL.  
  
 [@collection_package_id = ] *collection_package_id*  
 Ein eindeutiger lokaler Bezeichner, der auf das [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Sammlungspaket verweist, das vom Sammlungssatz verwendet wird. *collection_package_id* is **uniqueidentifer** and is required.  
  
 [@upload_package_id = ] *upload_package_id*  
 Ein eindeutiger lokaler Bezeichner, der auf das [!INCLUDE[ssIS](../../includes/ssis-md.md)]-Uploadpaket verweist, das vom Sammlungssatz verwendet wird. *Upload_package_id* ist **Uniqueidentifier** und ist erforderlich.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Damit diese Prozedur ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_admin (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="example"></a>Beispiel  
 Dies erstellt den generischen T-SQL-Abfragesammlertyp.  
  
```  
EXEC sp_syscollector_create_collector_type  
@collector_type_uid = '302E93D1-3424-4be7-AA8E-84813ECF2419',  
@name = 'Generic T-SQL Query Collector Type',  
@parameter_schema = '<?xml version="1.0" encoding="utf-8"?>  
  <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="DataCollectorType">  
    <xs:element name="TSQLQueryCollector">  
      <xs:complexType>  
        <xs:sequence>  
          <xs:element name="Query" minOccurs="1" maxOccurs="unbounded">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element name="Value" type="xs:string" />  
                <xs:element name="OutputTable" type="xs:string" />  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
          <xs:element name="Databases" minOccurs="0" maxOccurs="1">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element name="Database" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
              </xs:sequence>  
              <xs:attribute name="UseSystemDatabases" type="xs:boolean" use="optional" />  
              <xs:attribute name="UseUserDatabases" type="xs:boolean" use="optional" />  
            </xs:complexType>  
          </xs:element>  
        </xs:sequence>  
      </xs:complexType>  
    </xs:element>  
  </xs:schema>',  
@collection_package_id = '292B1476-0F46-4490-A9B7-6DB724DE3C0B',  
@upload_package_id = '6EB73801-39CF-489C-B682-497350C939F0';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)  
  
  
