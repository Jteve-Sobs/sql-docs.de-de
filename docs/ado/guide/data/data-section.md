---
title: Data-Abschnitt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data section [ADO]
ms.assetid: 43dc42a8-7057-48e6-93d6-880d5c5c51a4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6a06b2291d07378b63907b4a195fa3902930078
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53207769"
---
# <a name="data-section"></a>Datenabschnitt
Data-Abschnitt definiert die Daten des Rowsets zusammen mit allen ausstehenden Updates, einfügungen und löschungen. Data-Abschnitt kann NULL oder mehr Zeilen enthalten. Es kann nur Daten aus einem Rowset enthalten, in die Zeile durch das Schema definiert ist. Darüber hinaus können wie bereits erwähnt, Spalten ohne Daten ausgelassen werden. Wenn ein Attribut oder Unterelement im Data-Abschnitt verwendet wird, und dieses Konstrukt nicht im Schema-Abschnitt definiert wurde, wird es ignoriert.  
  
## <a name="string"></a>Zeichenfolge  
 Reservierte XML-Zeichen im Text-Daten müssen durch entsprechende Zeichenentitäten ersetzt werden. Beispielsweise muss in den Firmennamen "Joes Garage", das einfache Anführungszeichen durch eine Entität ersetzt werden. Die tatsächliche Zeile würde folgendermaßen aussehen:  
  
```  
<z:row CompanyName="Joe's Garage"/>  
```  
  
 Die folgenden Zeichen sind in XML reserviert und muss durch Zeichenentitäten ersetzt werden: {",", &,\<, >}.  
  
## <a name="binary"></a>Binär (Binary)  
 Binärdaten sind bin.hex codiert (d. h. ein Byte-Zuordnungen, die zwei Zeichen, ein Zeichen pro Halbbyte).  
  
## <a name="datetime"></a>datetime  
 Die Variante VT_DATE-Format wird nicht direkt von XML-Data-Datentypen unterstützt. Das richtige Format für Datumsangaben mit-Komponente in ein Datum und die Uhrzeit lautet jjjj-mm-TTThh.  
  
 Weitere Informationen zu XML angegebenen Datums-und Uhrzeitformate, finden Sie unter den [W3C XML-Data-Spezifikation](https://go.microsoft.com/fwlink/?LinkId=5692).  
  
 Wenn die XML-Data-Spezifikation definiert zwei äquivalente Datentypen (z. B. i4 == Int), ADO schreibt den angezeigten Namen jedoch in beide gelesen wird.  
  
## <a name="managing-pending-changes"></a>Verwalten von ausstehenden Änderungen  
 Ein Recordset in sofort geöffnet werden kann oder Update-Modus "Batch". Wenn sie im Modus "Batch-Update" mit clientseitigen Cursorn geöffnet werden, sind alle Änderungen, die auf das Recordset im Status "Ausstehend", bis die UpdateBatch-Methode aufgerufen wird. Ausstehende Änderungen werden auch beibehalten, wenn das Recordset gespeichert wird. In XML, werden sie durch die Verwendung der "Update"-Elemente, die im Urn: Schemas definierten dargestellt – Microsoft-Com:rowset. Darüber hinaus, wenn ein Rowset aktualisiert werden kann, die aktualisierbare-Eigenschaft muss festgelegt werden in der Definition der Zeile "true". Definieren Sie, dass die Shippers-Tabelle, die ausstehenden Änderungen enthält, würde die Zeilendefinition ähneln aussehen z. B. folgende.  
  
```  
<s:ElementType name="row" content="eltOnly" updatable="true">  
  <s:attribute type="ShipperID"/>  
  <s:attribute type="CompanyName"/>  
  <s:attribute type="Phone"/>  
  <s:extends type="rs:rowbase"/>  
</s:ElementType>  
```  
  
 Dies weist den Persistenz-Provider zu Surface-Daten, damit ADO ein aktualisierbares Recordset-Objekt erstellen kann.  
  
 Die folgenden Beispieldaten zeigt eine Vorschau von einfügungen, löschungen und Änderungen in die persistente Datei.  
  
```  
<rs:data>  
  <z:row ShipperID="2" CompanyName="United Package"   
    Phone="(503) 555-3199"/>  
<rs:update>  
  <rs:original>  
    <z:row ShipperID="3" CompanyName="Federal Shipping"   
      Phone="(503) 555-9931"/>  
  </rs:original>  
  <z:row Phone="(503) 552-7134"/>  
</rs:update>  
<rs:insert>  
  <z:row ShipperID="12" CompanyName="Lightning Shipping"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="13" CompanyName="Thunder Overnight"   
    Phone="(505) 111-2222"/>  
  <z:row ShipperID="14" CompanyName="Blue Angel Air Delivery"   
    Phone="(505) 111-2222"/>  
</rs:insert>  
<rs:delete>  
  <z:row ShipperID="1" CompanyName="Speedy Express" Phone="(503) 555-9831"/>  
</rs:delete>  
</rs:data>  
```  
  
 Ein Update enthält immer die gesamte Zeile Originaldaten gefolgt von Daten aus der geänderten Zeile. Alle Spalten oder nur die Spalten, die tatsächlich geändert wurden, kann die geänderte Zeile enthalten. Im vorherigen Beispiel die Zeile für den Spediteur 2 wird nicht geändert, und nur in die Spalte Phone Spediteur 3 Werte geändert wurde und daher die einzige Spalte in der geänderten Zeile enthalten ist. Die eingefügten Zeilen für Shippers 12, 13 und 14 werden im Batchmodus zusammen unter einem Rs: Insert-Tag. Beachten Sie, dass es sich bei gelöschte Zeilen auch zusammen als Batch verarbeitet werden können, auch wenn dies im vorherigen Beispiel nicht angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
