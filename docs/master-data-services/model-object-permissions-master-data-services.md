---
title: Berechtigungen für Modellobjekte (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 74ed9891af2905f8f45716c64b5f3ed9ac241905
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51700404"
---
# <a name="model-object-permissions-master-data-services"></a>Berechtigungen für Modellobjekte (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Berechtigungen für Modellobjekte sind erforderlich. Sie bestimmen die Attribute, auf die ein Benutzer im Funktionsbereich **Explorer** der Benutzeroberfläche zugreifen kann.  
  
 Wenn Sie z.B. der Entität „Product“ die Benutzerberechtigung **Aktualisieren** zuweisen, kann der Benutzer alle Attribute der Entität „Product“ aktualisieren. Wenn Sie einem einzelnen Attribut die Berechtigung **Aktualisieren** zuweisen, kann der Benutzer nur dieses Attribut aktualisieren.  
  
 Um die jedem Attributwert zugewiesene Sicherheit zu ermitteln, werden Modellobjektberechtigungen mit Hierarchieelementberechtigungen kombiniert, die die Elemente bestimmen, auf die ein Benutzer zugreifen kann.  
  
 Um einem Benutzer Zugriff auf einen anderen Funktionsbereich als **Explorer** zu gewähren, muss der Benutzer ein Modelladministrator sein, der Objektmodellen auch Administratorberechtigungen zuweisen kann. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)zuzugreifen.  
  
 Berechtigungen für Modellobjekte werden in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Benutzeroberfläche im Funktionsbereich **Benutzer- und Gruppenberechtigungen** auf der Registerkarte **Modelle** zugewiesen. Auf dieser Registerkarte wird das Modell als Baumstruktur dargestellt. Wenn Sie einem Objekt in der Struktur eine Berechtigung zuweisen, wird diese Berechtigung von allen untergeordneten Objekten geerbt. Sie können die Vererbung überschreiben, indem Sie einzelnen Objekten eine Berechtigung zuweisen.  
  
 Sie können eine Kombination aus lesen, erstellen, aktualisieren und löschen zuweisen oder Verweigern von Berechtigungen für Modellobjekte. Wenn Sie auf der Registerkarte **Modelle** keine Berechtigungen zuweisen, kann der Benutzer keine Modelle oder Daten in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]anzeigen.  
  
## <a name="best-practice"></a>Bewährte Methoden  
 Im Allgemeinen sollten Sie dem Modellobjekt die Berechtigung **ALLE** zuweisen und anschließend untergeordneten Objekten die Berechtigung explizit zuweisen.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Blogbeitrag [Sicherheitsverbesserungen](https://go.microsoft.com/fwlink/p/?LinkId=615376), auf msdn.com.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Modellberechtigungen &#40;Master Data Services&#41;](../master-data-services/model-permissions-master-data-services.md)   
 [Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)   
 [Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Vorgehensweise: Festlegen von Berechtigungen &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
