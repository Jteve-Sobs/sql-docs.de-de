---
title: Erstellen einer Attributgruppe (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b53cff2104d5f510db446095a3a65c6be27be77d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52813302"
---
# <a name="create-an-attribute-group-master-data-services"></a>Erstellen einer Attributgruppe (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Attributgruppen, wenn Sie Attribute auf einzelnen Registerkarten im **Explorerraster** anzeigen möchten.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)zuzugreifen.  
  
-   Es muss mindestens ein Attribut vorhanden sein. Weitere Informationen finden Sie unter [Erstellen eines Textattributs &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-create-an-attribute-group"></a>So erstellen Sie eine Attributgruppe  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Wählen Sie auf der Seite **Modell verwalten** im Raster ein Modell aus, und klicken Sie dann auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entität verwalten** im Raster die Zeile der Entität aus, für die Sie eine Attributgruppe erstellen möchten.  
  
4.  Klicken Sie auf **Attributgruppen**.  
  
5.  Führen Sie auf der Seite „Attributgruppen verwalten“ einen der folgenden Schritte aus, und klicken Sie dann auf **Hinzufügen**.  
  
     Wenn die Attributgruppe für Blattelemente bestimmt ist, wählen Sie in der Dropdownliste **Member Types** (Elementtypen) im oberen Seitenbereich die Option **Blatt** aus.  
  
     Wenn die Attributgruppe für konsolidierte Elemente bestimmt ist, wählen Sie in der Dropdownliste **Member Types** (Elementtypen) die Option **Konsolidiert** aus.  
  
     Wenn die Attributgruppe für Sammlungen bestimmt ist, wählen Sie in der Dropdownliste **Member Types** (Elementtypen) die Option **Sammlung** aus.  
  
6.  Klicken Sie auf **Blattgruppen**, **Konsolidierte Gruppen**oder **Auflistungsgruppen** , um eine Attributgruppe von Blattelementen, konsolidierten Elementen oder Auflistungen zu erstellen.  
  
7.  Geben Sie im Feld **Name** einen Namen für die Attributgruppe ein. Dieser Name wird auf der Registerkarte im **Explorer**angezeigt.  
  
8.  Um ein Attribut hinzuzufügen, klicken Sie im Feld **Verfügbare Attribute** auf das Attribut, und klicken Sie dann auf den Pfeil **Hinzufügen** . Um alle Attribute hinzuzufügen, klicken Sie auf den Pfeil **Alle hinzufügen** .  
  
9. Klicken Sie auf die Pfeile **Nach oben** und **Nach unten** , um die Reihenfolge der Attribute (von links nach rechts) zu ändern.  
  
10. Klicken Sie im Feld **Verfügbare Benutzer** auf Benutzer, und klicken Sie dann auf den Pfeil **Hinzufügen** . Um alle Benutzer hinzuzufügen, klicken Sie auf den Pfeil **Alle hinzufügen** .  
  
11. Klicken Sie im Feld **Verfügbare Gruppen** auf Gruppen, und klicken Sie dann auf den Pfeil **Hinzufügen** . Um alle Gruppen hinzuzufügen, klicken Sie auf den Pfeil **Alle hinzufügen** .  
  
12. Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Sichtbarmachen einer Attributgruppe für Benutzer &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Attributgruppen &#40;Master Data Services&#41;](../master-data-services/attribute-groups-master-data-services.md)   
 [Attribute &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Ändern des Namens einer Attributgruppe &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-group-name-master-data-services.md)   
 [Löschen einer Attributgruppe &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-group-master-data-services.md)   
 [Blattberechtigungen &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md)   
   
  
  
