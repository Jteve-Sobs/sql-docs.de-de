---
description: Groups-Collection (ADOX)
title: Groups-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Groups
- User::Groups
- Catalog::Groups
helpviewer_keywords:
- Groups collection [ADOX]
ms.assetid: 09aa7b0a-69d5-4564-80a7-20ad8189670f
author: rothja
ms.author: jroth
ms.openlocfilehash: 70c32ba5e4726aca7d6ad8b37c7df082d25b94b0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439992"
---
# <a name="groups-collection-adox"></a>Groups-Collection (ADOX)
Enthält alle gespeicherten [Gruppen](../../../ado/reference/adox-api/group-object-adox.md) Objekte eines Katalogs oder Benutzers.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Groups** -Sammlung eines [Katalogs](../../../ado/reference/adox-api/catalog-object-adox.md) stellt alle Gruppenkonten des Katalogs dar. Die **Groups** -Sammlung für einen [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) stellt nur die Gruppe dar, zu der der Benutzer gehört.  
  
 Die [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) -Methode für eine **Groups** -Sammlung ist für ADOX eindeutig. Ihre Möglichkeiten:  
  
-   Fügen Sie der Sammlung mithilfe der **Append** -Methode eine neue Sicherheitsgruppe hinzu.  
  
 Die restlichen Eigenschaften und Methoden sind Standard für ADO-Auflistungen. Ihre Möglichkeiten:  
  
-   Greifen Sie mit der [Item](../../../ado/reference/ado-api/item-property-ado.md) -Eigenschaft auf eine Gruppe in der Auflistung zu.  
  
-   Gibt die Anzahl der in der Auflistung enthaltenen Gruppen mit der [count](../../../ado/reference/ado-api/count-property-ado.md) -Eigenschaft zurück.  
  
-   Entfernen Sie eine Gruppe aus der Sammlung mit der [Delete](../../../ado/reference/adox-api/delete-method-adox-collections.md) -Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung, um das aktuelle Datenbankschema mit der [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode widerzuspiegeln.  
  
> [!NOTE]
>  Vor dem Anhängen eines **Group** -Objekts an die **Groups** -Auflistung eines **User** -Objekts muss bereits ein **Gruppen** Objekt mit demselben [Namen](../../../ado/reference/adox-api/name-property-adox.md) wie das angefügte-Objekt in der **Groups** -Auflistung des **Katalogs**vorhanden sein.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Groups Collection Properties, Methods, and Events (Groups-Auflistung – Eigenschaften, Methoden und Ereignisse)](../../../ado/reference/adox-api/groups-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Catalog-Objekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)
