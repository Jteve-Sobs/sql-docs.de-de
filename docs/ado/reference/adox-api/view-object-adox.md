---
description: View-Objekt (ADOX)
title: View-Objekt (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
author: rothja
ms.author: jroth
ms.openlocfilehash: 3cc635db04358417948e709a4c47605fae17669b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439362"
---
# <a name="view-object-adox"></a>View-Objekt (ADOX)
Stellt einen gefilterten Satz von Datensätzen oder eine virtuelle Tabelle dar. Bei Verwendung in Verbindung mit dem ADO- [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt kann das **View** -Objekt zum Hinzufügen, löschen oder Ändern von Sichten verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Sicht ist eine virtuelle Tabelle, die aus anderen Datenbanktabellen oder Sichten erstellt wurde. Mit dem **View** -Objekt können Sie eine Ansicht erstellen, ohne die "Create View"-Syntax des Anbieters kennen oder verwenden zu müssen.  
  
 Mit den Eigenschaften eines **Ansichts** Objekts können Sie folgende Aktionen ausführen:  
  
-   Identifizieren Sie die Sicht mit der [Name](../../../ado/reference/adox-api/name-property-adox.md) -Eigenschaft.  
  
-   Geben Sie das ADO- **Befehls** Objekt an, das verwendet werden kann, um Sichten mit der [Command](../../../ado/reference/adox-api/command-property-adox.md) -Eigenschaft hinzuzufügen, zu löschen oder zu ändern.  
  
-   Gibt Datumsinformationen mit den Eigenschaften [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) und [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) zurück.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [View-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Sichten und Fields-Auflistungen (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Beispiele für die Append-Methode (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views-Auflistung, CommandText-Eigenschafts Beispiel (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Sichten Delete-Methode (Beispiel) (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
