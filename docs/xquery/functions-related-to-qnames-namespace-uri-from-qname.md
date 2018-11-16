---
title: Namespace-Uri-aus-QName (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 111eff61472e33c6517f733d45f1ea0e3bd1700c
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51668636"
---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>Funktionen, die sich auf QNames beziehen – namespace-uri-from-QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeichenfolge mit den Namespace-Uri, der vom angegebenen QName *$arg*. Das Ergebnis ist die leere Sequenz ist, wenn *$arg* die leere Sequenz.  
  
## <a name="syntax"></a>Syntax  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Ist der QName, dessen Namespace-URI zurückgegeben wurde.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. Abrufen der Namespace-URI von einem QName  
 Ein Arbeitsbeispiel finden Sie unter [Local-Name-aus-QName &#40;XQuery&#41;](../xquery/functions-related-to-qnames-local-name-from-qname.md).  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **namespace-uri-from-QName()** Funktion gibt Instanzen von xs: String anstelle von xs: anyURI zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Functions Related to QNames sich &#40;XQuery&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
