---
title: Datentypen und XML-Massenladen das Ladeverhalten (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 820d2b083544542d1c1414f978105fe992b0ce36
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915144"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Datentypen und XML-Massenladenverhalten (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die Datentypen, die im Zuordnungsschema angegeben werden (XSD-oder XDR und **SQL: DataType**) werden im Allgemeinen ignoriert werden, mit Ausnahme der in den folgenden Fällen:  
  
 Bei XSD:  
  
-   Wenn der Typ ist **"DateTime"** oder **Zeit**, Sie müssen angeben, die **SQL: DataType** da XML-Massenladen, die vor dem Senden der Daten an Microsoft Datenkonvertierungausführt[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Wenn Sie beim Massenladen in eine Spalte vom sind **Uniqueidentifier** geben [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und der XSD-Wert ist eine GUID mit geschweiften Klammern ({und}), Sie müssen angeben, **SQL: datatype = "Uniqueidentifier"** auf Entfernen Sie die geschweiften Klammern ein, bevor der Wert in die Spalte eingefügt wird. Wenn **SQL: DataType** nicht angegeben ist, wird der Wert in geschweiften Klammern gesendet, und der Vorgang schlägt fehl.  
  
 Weitere Informationen zu **SQL: DataType**, finden Sie unter [Datentypumwandlungen und die SQL: DataType-Anmerkung &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 Bei XDR:  
  
-   Wenn die **dt: Type** ist **"DateTime"** , **Zeit**, **dateTime.tz**, oder **time.tz**, müssen Sie beide angeben die **dt: Type** und **SQL: DataType** -Datentypen, da XML-Massenladen eine Datenkonvertierung durchführt, bevor die Daten gesendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Wenn Ihre XML-Daten vom Typ **Uuid**, **SQL: DataType** muss angegeben werden; **dt: Type = "Uuid"** ist auch erforderlich, es sei denn, die Daten um Zeichenfolgendaten handelt. Wenn Sie keinen angeben **Dt:uuid**, XML-Massenladen Zeichenfolgen mit geschweiften Klammern akzeptiert (und entfernt diese ggf.).  
  
-   Wenn die XML-Daten **bin. Base64** oder **bin.hex**, Sie müssen angeben, die XML-Datentyps mit **dt: Type**. XML-Massenladen lädt die Daten dann als Hexadezimaldarstellung der Daten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
  
