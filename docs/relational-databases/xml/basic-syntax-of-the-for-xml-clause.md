---
title: Basissyntax der FOR XML-Klausel | Microsoft-Dokumentation
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- BINARY BASE64 directive
- ROOT directive
- FOR XML clause, BINARY BASE64 directive
- FOR XML clause, syntax
- FOR XML clause, ROOT directive
ms.assetid: df19ecbf-d28e-4e9c-aaa3-700f8bbd3be4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 273cfed91e6d0077700f81b8cb9a0fc8c0300c61
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66175390"
---
# <a name="basic-syntax-of-the-for-xml-clause"></a>Basissyntax der FOR XML-Klausel

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Der FOR XML-Modus kann RAW, AUTO, EXPLICIT oder PATH lauten. Er bestimmt die Form des erhaltenen XML.  
  
> [!IMPORTANT]  
> Die **XMLDATA-Direktive** zur FOR XML-Option ist **veraltet**. Verwenden Sie XSD-Generierung für RAW- und AUTO-Modus. Es gibt keinen Ersatz für die XMLDATA-Direktive im EXPLICIT-Modus. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]

## <a name="syntax"></a>Syntax

Im Folgenden wird die Basissyntax der [FOR-Klausel (Transact-SQL)](../../t-sql/queries/select-for-clause-transact-sql.md) beschrieben.

```  
[ FOR { BROWSE | <XML> } ]  
<XML> ::=  
XML   
    {   
      { RAW [ ('ElementName') ] | AUTO }   
        [   
           <CommonDirectives>   
           [ , { XMLDATA | XMLSCHEMA [ ('TargetNameSpaceURI') ]} ]
           [ , ELEMENTS [ XSINIL | ABSENT ]   
        ]  
      | EXPLICIT   
        [   
           <CommonDirectives>   
           [ , XMLDATA ]   
        ]  
      | PATH [ ('ElementName') ]   
        [   
           <CommonDirectives>   
           [ , ELEMENTS [ XSINIL | ABSENT ] ]  
        ]  
     }   
  
 <CommonDirectives> ::=   
   [ , BINARY BASE64 ]  
   [ , TYPE ]  
   [ , ROOT [ ('RootName') ] ]  
```  

### <a name="syntax-for-azure-sql-database"></a>Syntax für Azure SQL-Datenbank

Eine Dokumentation zur SELECT...**FOR XML**-Klausel, die auch für Azure SQL-Datenbank gilt, finden Sie unter [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md).

## <a name="arguments"></a>Argumente

**RAW** [('_ElementName_')]  
 Verwendet das Abfrageergebnis und wandelt jede Zeile im Resultset in ein XML-Element mit einem generischen Bezeichner (\<row />) als Elementtag um. Sie können optional einen Namen für das Zeilenelement angeben, wenn Sie diese Direktive verwenden. Das sich ergebende XML verwendet den angegebenen *ElementName* als das für jede Zeile generierte Zeilenelement. Weitere Informationen finden Sie unter [Verwenden des RAW-Modus mit FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
**AUTO**  
 Gibt Abfrageergebnisse in einer einfachen, geschachtelten XML-Struktur zurück. Jede Tabelle in der FROM-Klausel, aus der mindestens eine Spalte in der SELECT-Klausel aufgeführt ist, wird als ein XML-Element dargestellt. Die in der SELECT-Klausel aufgelisteten Spalten werden den entsprechenden Elementattributen zugeordnet. Weitere Informationen finden Sie unter [Verwenden des AUTO-Modus mit FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md).  
  
**EXPLICIT**  
 Gibt an, dass die Form der sich ergebenden XML-Struktur explizit definiert wird. In diesem Modus müssen die Abfragen jedoch auf eine bestimmte Weise geschrieben werden, sodass zusätzliche Informationen über die gewünschte Schachtelung explizit angegeben werden. Weitere Informationen finden Sie unter [Verwenden des EXPLICIT-Modus mit FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md).  
  
**PATH**  
 Stellt ein einfacheres Verfahren zum Mischen von Elementen und Attributen bereit und führt zusätzliche Schachtelung für die Darstellung komplexer Eigenschaften ein. Sie können Abfragen im FOR XML EXPLICIT-Modus zum Erstellen dieser Art von XML aus einem Rowset verwenden, der PATH-Modus stellt jedoch eine einfachere Alternative zu den möglicherweise aufwendigen Abfragen im EXPLICIT-Modus bereit. Der PATH-Modus ermöglicht in Kombination mit der Möglichkeit, verschachtelte FOR XML-Abfragen zu schreiben und die TYPE-Direktive zum Zurückgeben von Instanzen des Typs **xml** zu verwenden, das Schreiben von Abfragen mit geringerer Komplexität. Er bietet eine Alternative zum Schreiben der meisten Abfragen im EXPLICIT-Modus. Standardmäßig generiert der PATH-Modus einen \<row>-Elementwrapper für jede Zeile im Resultset. Optional können Sie einen Elementnamen angeben. Wenn Sie einen Elementnamen angeben, wird der angegebene Name als Wrapperelementname verwendet. Bei einer leeren Zeichenfolge (FOR XML PATH ('')) wird kein Wrapperelement generiert. Weitere Informationen finden Sie unter [Verwenden des PATH-Modus mit FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md).  
  
**MLDATA**  
 Gibt an, dass ein XML XDR-Inlineschema zurückgegeben werden soll. Das Schema wird dem Dokument als Inlineschema vorangestellt. Ein funktionierendes Beispiel finden Sie unter [Verwenden des RAW-Modus mit FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
**XMLSCHEMA**  
 Gibt ein W3C XML-Inlineschema (XSD) zurück. Optional können Sie einen Zielnamespace-URI angeben, wenn Sie diese Direktive angeben. Auf diese Weise wird der angegebene Namespace im Schema zurückgegeben. Weitere Informationen finden Sie unter [Generieren eines XSD-Inlineschemas](../../relational-databases/xml/generate-an-inline-xsd-schema.md). Ein funktionierendes Beispiel finden Sie unter [Verwenden des RAW-Modus mit FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
**ELEMENTS**  
 Wenn die Option ELEMENTS angegeben ist, werden die Spalten als Teilelemente zurückgegeben. Andernfalls werden sie XML-Attributen zugeordnet. Diese Option wird nur in den Modi RAW, AUTO und PATH unterstützt. Optional können Sie XSINIL oder ABSENT angeben, wenn Sie diese Direktive angeben. XSINIL gibt an, dass ein Element, dessen **xsi:nil** -Attribut auf True festgelegt ist, für NULL-Spaltenwerte erstellt wird. Standardmäßig werden keine Elemente für NULL-Werte erstellt. Dies gilt auch, wenn ABSENT zusammen mit ELEMENTS angegeben wird. Ein funktionierendes Beispiel finden Sie unter [Verwenden des RAW-Modus mit FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md) und unter [Verwenden des AUTO-Modus mit FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md).  
  
**BINARY BASE64**  
 Wenn die Option BINARY Base64 angegeben ist, werden alle von der Abfrage zurückgegebenen Binärdaten im Base64-codierten Format dargestellt. Zum Abrufen von Binärdaten mithilfe des Modus RAW oder EXPLICIT muss diese Option angegeben werden. Standardmäßig werden Binärdaten im AUTO-Modus als Verweis zurückgegeben. Ein funktionierendes Beispiel finden Sie unter [Verwenden des RAW-Modus mit FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
**TYPE**  
 Gibt an, dass die Abfrage die Ergebnisse als **xml** -Typ zurückgibt. Weitere Informationen finden Sie unter [TYPE Directive in FOR XML Queries](../../relational-databases/xml/type-directive-in-for-xml-queries.md).  
  
**ROOT** [('_RootName_')]  
 Gibt an, dass ein einzelnes Element der obersten Ebene dem als Ergebnis zurückgegebenen XML-Dokument hinzugefügt wird. Optional können Sie den zu generierenden Stammelementnamen angeben. Der Standardwert lautet `<root>`.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des RAW-Modus mit FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)   
 [Verwenden des AUTO-Modus mit FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)   
 [Verwenden des EXPLICIT-Modus mit FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)   
 [Verwenden des PATH-Modus mit FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML &#40;SQL Server&#41;](../../relational-databases/xml/for-xml-sql-server.md)  
