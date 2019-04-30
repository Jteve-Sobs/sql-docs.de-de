---
title: Users-Auflistung (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group::Users
- Users
- Catalog::Users
helpviewer_keywords:
- Users collection [ADOX]
ms.assetid: 0a30fa74-6f10-4410-bd70-882e7c43cd46
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dc465261748c1efd340e78ddc2f3e12d601e931
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281622"
---
# <a name="users-collection-adox"></a>Users-Collection (ADOX)
Enthält alle gespeicherten [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) Objekte eine [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md) oder [Gruppe](../../../ado/reference/adox-api/group-object-adox.md).  
  
## <a name="remarks"></a>Hinweise  
 Die **Benutzer** Auflistung von einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md) Benutzer alle des Katalogs darstellt. Die **Benutzer** Sammlung für einen [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) nur die Benutzer, die eine Mitgliedschaft in der Gruppe darstellt.  
  
 Die [Append](../../../ado/reference/adox-api/append-method-adox-users.md) -Methode für eine **Benutzer** Auflistung für ADOX eindeutig ist. Folgende Aktionen sind möglich:  
  
-   Hinzufügen eines neuen Benutzers auf die Auflistung mit den **Append** Methode.  
  
 Die übrigen Eigenschaften und Methoden sind standard in ADO-Collections. Folgende Aktionen sind möglich:  
  
-   Zugreifen auf einen Benutzer in der Auflistung mit den [Element](../../../ado/reference/ado-api/item-property-ado.md) Eigenschaft.  
  
-   Zurückgeben der Anzahl der Benutzer, die in der Auflistung mit den [Anzahl](../../../ado/reference/ado-api/count-property-ado.md) Eigenschaft.  
  
-   Entfernen eines Benutzers aus der Auflistung mit den [löschen](../../../ado/reference/adox-api/delete-method-adox-collections.md) Methode.  
  
-   Aktualisieren Sie die Objekte in der Auflistung entsprechend dem aktuellen Schema der Datenbank mit der [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) Methode.  
  
> [!NOTE]
>  Vor dem Anfügen einer **Benutzer** -Objekt der **Benutzer** Auflistung von einer **Gruppe** -Objekt, eine **Benutzer** Objekt mit demselben [Name ](../../../ado/reference/adox-api/name-property-adox.md) wie diejenige, die angefügt werden im bereits vorhanden sind, muss die **Benutzer** Auflistung von der **Katalog**.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [Users Collection Properties, Methods, and Events (Users-Auflistung – Eigenschaften, Methoden und Ereignisse)](../../../ado/reference/adox-api/users-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetPermissions und SetPermissions-Methoden – Beispiel (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)
