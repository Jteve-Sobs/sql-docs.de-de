---
title: Löschen von Daten mit XML-Updategrams (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 808cac0491d7a62ef6a7616745dfb56874299f6a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52788992"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>Löschen von Daten mit XML-Updategrams (SQLXML 4.0)
  Ein Updategram zeigt einen Löschvorgang aus, wenn eine im Datensatzinstanz der  **\<vor >** Block, jedoch ohne entsprechende Datensätze in der  **\<nach >** Block. In diesem Fall löscht das Updategram den Datensatz in die  **\<vor >** Block aus der Datenbank.  
  
 Dies ist das Updategramformat für einen Löschvorgang:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 Können Sie weglassen der  **\<nach >** markieren, wenn das Updategram nur einen Löschvorgang ausführt. Wenn Sie nicht das optionale angeben `mapping-schema` -Attribut, das  **\<ElementName >** im Updategram Zuordnungen in einer Datenbanktabelle und die untergeordneten Elemente oder Attribute zugeordnet Spalten in der Tabelle angegeben.  
  
 Wenn ein Element im Updategram angegebene mehr als eine Zeile in der Tabelle entspricht, oder eine beliebige Zeile stimmt nicht überein, wird das Updategram einen Fehler zurück und bricht die gesamte  **\<Sync >** Block. Nur ein Datensatz kann gleichzeitig von einem Element im Updategram gelöscht werden.  
  
## <a name="examples"></a>Beispiele  
 Die Beispiele in diesem Abschnitt verwenden die Standardzuordnung (d. h. es ist kein Zuordnungsschema im Updategram angegeben). Weitere Beispiele für Updategrams, die Zuordnungsschemas verwenden, finden Sie unter [ein Mapping-Schema mit Anmerkungen angeben, in einem Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
 Um funktionierende Beispiele, die mit den folgenden Beispielen erstellen, müssen Sie die Anforderungen, die im angegebenen erfüllen [Anforderungen für die Ausführung von SQLXML-Beispielen](../../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>A. Löschen eines Datensatzes mithilfe eines Updategrams  
 Die folgenden Updategrams löschen zwei Datensätze aus der Tabelle HumanResources.Shift.  
  
 In diesen Beispielen gibt das Updategram kein Zuordnungsschema an. Daher verwendet das Updategram die Standardzuordnung, in der der Elementname einem Tabellennamen, und die Attribute oder untergeordneten Elemente den Spalten in dieser Tabelle zugeordnet werden.  
  
 Dieses erste Updategram ist attributzentriert und identifiziert zwei Schichten (Tag / Abend und Abend / Nacht) in der  **\<vor >** Block. Da es keinen entsprechenden Datensatz in gibt die  **\<nach >** Block, dies ist ein Löschvorgang.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Vollständiges Beispiel B ("Einfügen mehrerer Datensätze mithilfe eines Updategrams") in [Einfügen von Daten mithilfe von XML-Updategrams &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
2.  Kopieren Sie das oben angegebene Updategram in Editor, und speichern Sie sie Updategram-removeshifts.XML in demselben Ordner aus, als abgeschlossen ("Einfügen mehrerer Datensätze mithilfe eines Updategrams") verwendet wurde, im [Einfügen von Daten mithilfe von XML-Updategrams &#40;SQLXML 4.0&#41; ](inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberlegungen zu Updategramms &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
