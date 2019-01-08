---
title: 'Erstellen von Konstanten Elementen unter Verwendung von Sql: ist-Constant (SQLXML 4.0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 03e2d3d672d0bfa407a3fb553a1139d30696971e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793472"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>Erstellen von 'constant'-Elementen unter Verwendung von sql:is-constant (SQLXML 4.0)
  Constant-Element angeben –, also ein Element in das XSD-Schema, das keiner Datenbanktabelle oder-Spalte zugeordnet ist – können Sie die `sql:is-constant` Anmerkung. Diese Anmerkung akzeptiert einen booleschen Wert (0 = false, 1 = true). Zulässig sind die Werte 0, 1, true und false. Die `sql:is-constant`-Anmerkung kann für ein Element angegeben werden, das über keine Attribute verfügt. Wenn sie für ein Element mit dem Wert true (oder 1) festgelegt ist, wird dieses Element nicht der Datenbank zugeordnet, aber dennoch im XML-Dokument angezeigt.  
  
 Die `sql:is-constant`-Anmerkung kann zu folgenden Zwecken verwendet werden:  
  
-   Hinzufügen eines Elements der obersten Ebene zum XML-Dokument. XML erfordert ein einzelnes Element (Stammelement) der obersten Ebene für das Dokument.  
  
-   Erstellen von Containerelementen, z. B. eine  **\<Bestellungen >** -Element, das alle Reihenfolgen umschließt.  
  
 Die `sql:is-constant` -Anmerkung kann hinzugefügt werden, um eine  **\<ComplexType >** Element.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen für die Ausführung von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>A. Angeben von "sql:is-constant" zum Hinzufügen eines Containerelements  
 In diesem mit Anmerkungen in XSD-Schema  **\<CustomerOrders >** wird als constant-Element definiert, durch Angabe der `sql:is-constant` Attribut mit einem Wert von 1. Aus diesem Grund  **\<CustomerOrders >** ist nicht auf Sie keiner Datenbanktabelle oder – Spalte zugeordnet. Dieses constant-Element besteht aus den  **\<Reihenfolge >** untergeordnete Elemente.  
  
 Obwohl  **\<CustomerOrders >** ordnet nicht auf Sie keiner Datenbanktabelle oder-Spalte erscheint weiterhin in der XML-Ergebnis als Containerelement mit den  **\<Reihenfolge >** untergeordnete Elemente.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine Beispiel-XPath-Abfrage anhand des Schemas  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen isConstant.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen isConstantT.xml im gleichen Verzeichnis, in dem Sie  isConstant.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (isConstant.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird ein Teil des Resultsets aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
