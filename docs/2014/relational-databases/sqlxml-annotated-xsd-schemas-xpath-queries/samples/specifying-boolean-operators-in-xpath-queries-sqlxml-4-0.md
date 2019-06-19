---
title: Angeben von booleschen Operatoren in XPath-Abfragen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath operators [SQLXML]
- OR operator
- Boolean operators
- XPath queries [SQLXML], Boolean operators
- operators [SQLXML]
ms.assetid: 9928cff5-62ac-42aa-96bf-2e09a1df0bc3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29404c4a3dc7b4b10106e7a3a8cb170ffe1e7a3e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66010630"
---
# <a name="specifying-boolean-operators-in-xpath-queries-sqlxml-40"></a>Angeben von booleschen Operatoren in XPath-Abfragen (SQLXML 4.0)
  Im folgenden Beispiel wird dargestellt, wie boolesche Operatoren in XPath-Abfragen angegeben werden. Die XPath-Abfragen in diesem Beispiel werden für das in SampleSchema1.xml enthaltene Zuordnungsschema angegeben. Weitere Informationen zu diesem Beispielschema finden Sie unter [Annotated XSD-Beispielschema für XPath-Beispiele &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-specify-the-or-boolean-operator"></a>A. Angeben des booleschen OR-Operators  
 Diese XPath-Abfrage gibt die  **\<Kunden >** untergeordneten-Elemente des Kontextknotens mit der **"CustomerID"** -Attribut den Wert 13 "oder" 31:  
  
```  
/child::Customer[attribute::CustomerID="13" or attribute::CustomerID="31"]  
```  
  
 Es kann eine Abkürzung für die `attribute`-Achse (@) angegeben werden. Da die `child`-Achse die Standardachse ist, muss sie nicht angegeben werden:  
  
```  
/Customer[@CustomerID="13" or @CustomerID="31"]  
```  
  
 Im Prädikat ist `attribute` ist die Achse und `CustomerID` ist der Knotentest (TRUE, wenn **"CustomerID"** ist ein  **\<Attribut >** Knoten, da die  **\<Attribut >** Knoten ist der primäre Knoten für die `attribute` Achse). Das Prädikat filtert die  **\<Kunden >** -Elemente und gibt nur solche, die die Bedingung erfüllen, im Prädikat angegebenen.  
  
##### <a name="to-test-the-xpath-queries-against-the-mapping-schema"></a>So testen Sie die XPath-Abfragen mit dem Zuordnungsschema  
  
1.  Kopieren der [Schema Beispielcode](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) und fügen Sie ihn in eine Textdatei. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
2.  Erstellen Sie die folgende Vorlage (BooleanOperatorsA.xml), und speichern Sie sie in dem Verzeichnis, in dem SampleSchema1.xml gespeichert ist.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="13" or @CustomerID="31"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (SampleSchema1.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden finden Sie das Resultset der Vorlagenausführung:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="31" SalesPersonID="286" TerritoryID="7" AccountNumber="31" CustomerType="S" Orders="Ord-51803 Ord-69427">  
    <Order SalesOrderID="Ord-51803" SalesPersonID="286" OrderDate="2003-08-01T00:00:00" DueDate="2003-08-13T00:00:00" ShipDate="2003-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-718" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-838" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    <Order SalesOrderID="Ord-69427" SalesPersonID="286" OrderDate="2004-05-01T00:00:00" DueDate="2004-05-13T00:00:00" ShipDate="2004-05-08T00:00:00">  
      <OrderDetail ProductID="Prod-835" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
  </Customer>  
</ROOT>  
```  
  
  
