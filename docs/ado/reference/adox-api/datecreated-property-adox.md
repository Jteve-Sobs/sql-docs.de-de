---
description: DateCreated-Eigenschaft (ADOX)
title: DateCreated-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: rothja
ms.author: jroth
ms.openlocfilehash: 37101d33e8a0efcda56dae5df13d7afd299f6f23
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440162"
---
# <a name="datecreated-property-adox"></a>DateCreated-Eigenschaft (ADOX)
Gibt das Datum an, an dem das Objekt erstellt wurde.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt einen **Variant** -Wert zurück, der das erstellte Datum angibt. Der Wert ist NULL, wenn **DateCreated** vom Anbieter nicht unterstützt wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **DateCreated** -Eigenschaft ist für neu angefügte Objekte NULL. Nachdem Sie eine neue [Sicht](../../../ado/reference/adox-api/view-object-adox.md) oder [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md)angehängt haben, müssen Sie die [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode der [Sichten](../../../ado/reference/adox-api/views-collection-adox.md) oder der [Prozeduren](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung aufrufen, um Werte für die **DateCreated** -Eigenschaft zu erhalten.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Procedure Object (ADOX) (Procedure-Objekt (ADOX))](../../../ado/reference/adox-api/procedure-object-adox.md)  
    :::column-end:::
    :::column:::
        [Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)  
    :::column-end:::
    :::column:::
        [View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [DateCreated und DateModified-Eigenschaften (Beispiel) (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified-Eigenschaft (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
