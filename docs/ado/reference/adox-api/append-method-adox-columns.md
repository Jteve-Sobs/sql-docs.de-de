---
description: Append-Methode (ADOX-Spalten)
title: Append-Methode (ADOX-Spalten) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
author: rothja
ms.author: jroth
ms.openlocfilehash: bd33dc71c9adcbe8e6ed25f965b227fbc76d96fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440522"
---
# <a name="append-method-adox-columns"></a>Append-Methode (ADOX-Spalten)
Fügt der [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) -Auflistung ein neues [Spalten](../../../ado/reference/adox-api/column-object-adox.md) Objekt hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Spalte*  
 Das anzufügende **Spalten** Objekt oder der Name der Spalte, die erstellt und angefügt werden soll.  
  
 *Typ*  
 Optional. Ein **Long** -Wert, der den Datentyp der Spalte angibt. Der *Typparameter* entspricht der [Type](../../../ado/reference/adox-api/type-property-column-adox.md) -Eigenschaft eines **Column** -Objekts.  
  
 *DefinedSize*  
 Optional. Ein **Long** -Wert, der die Größe der Spalte angibt. Der *DefinedSize* -Parameter entspricht der [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) -Eigenschaft eines **Column** -Objekts.  
  
> [!NOTE]
>  Wenn eine **Spalte** an die **Columns** -Auflistung eines [Indexes](../../../ado/reference/adox-api/index-object-adox.md) angefügt wird, tritt ein Fehler auf, wenn die **Spalte** nicht in einer [Tabelle](../../../ado/reference/adox-api/table-object-adox.md) vorhanden ist, die bereits an die [Tabellen](../../../ado/reference/adox-api/tables-collection-adox.md) Auflistung angehängt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Methoden und Tabellen Append-Methoden, Name Property example (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append-Methode, Schlüsseltyp, RelatedColumn, RelatedTable und UpdateRule Properties-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Beispiel für eine Beispiel Katalog Eigenschaft (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX-Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX-Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
