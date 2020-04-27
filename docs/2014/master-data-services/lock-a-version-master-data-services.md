---
title: Sperren einer Version (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: e38a4c75ad6cf8c65d7120e0eb98163f7ee0fccc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482875"
---
# <a name="lock-a-version-master-data-services"></a>Sperren einer Version (Master Data Services)
  Sperren Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine Version eines Modells, um Änderungen an den Elementen des Modells und den Attributen zu verhindern.  
  
> [!NOTE]  
>  Wenn eine Version gesperrt ist, können Modelladministratoren weiterhin Elemente hinzuzufügen, bearbeiten und entfernen. Andere Benutzer mit Berechtigungen für das Modell können die Elemente jedoch nur anzeigen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Versionsverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Der Status der Version muss **Öffnen**sein.  
  
### <a name="to-lock-a-version"></a>So sperren Sie eine Version  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Versionsverwaltung**.  
  
2.  Wählen Sie auf der Seite **Versionen verwalten** die Zeile für die Version aus, die Sie sperren möchten.  
  
3.  Klicken Sie auf **Sperren**.  
  
4.  Klicken Sie im Bestätigungsdialogfeld auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Überprüfen einer Version anhand von Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Durchführen eines Commits für eine Version &#40;Master Data Services&#41;](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Versionen &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Entsperren einer Version &#40;Master Data Services&#41;](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
