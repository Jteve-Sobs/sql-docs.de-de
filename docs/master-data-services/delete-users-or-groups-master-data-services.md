---
title: Löschen von Benutzern oder Gruppen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting groups [Master Data Services]
- groups [Master Data Services], deleting
- users [Master Data Services], deleting
- deleting users [Master Data Services]
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 66ecbfa946b894b3dcfad9befb63f30645f9c77d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65478088"
---
# <a name="delete-users-or-groups-master-data-services"></a>Löschen von Benutzern oder Gruppen (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Löschen Sie Benutzer oder Gruppen, wenn Sie nicht mehr möchten, dass sie auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]zugreifen.  
  
 Beachten Sie das folgende Verhalten, wenn Sie Benutzer und Gruppen löschen:  
  
-   Wenn Sie einen Benutzer löschen, der Mitglied einer Gruppe ist, die Zugriff auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]hat, kann der Benutzer weiter auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] zugreifen, bis Sie den Benutzer aus Active Directory oder der lokalen Gruppe entfernen.  
  
-   Wenn Sie eine Gruppe löschen, werden alle Benutzer aus der Gruppe mit Zugriff auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] in der Liste **Benutzer** angezeigt, bis Sie sie löschen.  
  
-   Änderungen an der Sicherheit werden 20 Minuten lang nicht an MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] weitergegeben.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
### <a name="to-delete-users-or-groups"></a>So löschen Sie Benutzer oder Gruppen  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Um einen Benutzer zu löschen, bleiben Sie auf der Seite **Benutzer** . Um eine Gruppe zu löschen, klicken Sie auf der Menüleiste auf **Gruppen verwalten**.  
  
3.  Wählen Sie im Raster die Zeile für den Benutzer oder die Gruppe aus, die Sie löschen möchten.  
  
4.  Klicken Sie auf **Ausgewählten Benutzer löschen** oder **Ausgewählte Gruppe löschen**.  
  
5.  Klicken Sie im Bestätigungsdialogfeld auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit &#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
