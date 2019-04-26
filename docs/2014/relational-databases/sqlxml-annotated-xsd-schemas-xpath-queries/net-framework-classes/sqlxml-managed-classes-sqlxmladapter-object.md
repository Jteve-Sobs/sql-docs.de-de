---
title: SqlXmlAdapter-Objekt (verwaltete SQLXML Klassen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6764b729ffb2a917a03332d8472053e590d5f352
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740620"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a>SqlXmlAdapter-Objekt (Verwaltete SQLXML-Klassen)
  Dieses Objekt stellt Methoden bereit, welche die Interaktion mit dem Dataset in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework erleichtern. Ein Arbeitsbeispiel finden Sie unter [zugreifen auf SQLXML-Funktionalität in der .NET-Umgebung](accessing-sqlxml-functionality-in-the-net-environment.md).  
  
 SqlXmlAdapter-Objekt unterstützt die folgenden Methoden:  
  
 "void" Fill (ds DataSet)  
 Füllt das Dataset in .NET Framework mit den von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abgerufenen XML-Daten.  
  
 "void" Update (ds DataSet)  
 Übernimmt Updates aus den Daten im Dataset und wendet sie auf Datensätze in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an.  
  
 SqlXmlAdapter-Objekt unterstützt die folgenden Konstruktoren:  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>Siehe auch  
 [SqlXmlCommand-Objekt &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-4-0-net-framework-support-managed-classes.md)   
 [SqlXmlParameter-Objekt &#40;verwaltete SQLXML-Klassen&#41;](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
