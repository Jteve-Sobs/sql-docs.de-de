---
title: Genehmigung erforderlich (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 6bda48b3645260ed3886316a0ba478aad214b593
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65486383"
---
# <a name="approval-required-master-data-services"></a>Genehmigung erforderlich (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]kann der Administrator eine Entität auf „Genehmigung erforderlich“ festlegen. Alle Änderungen an dieser Entität müssen dann von einem der Entitätsadministratoren überprüft und genehmigt werden.  
  
> [!NOTE]  
>  Änderungen an Blattelementen müssen genehmigt werden. Bei Änderungen an veralteten expliziten Hierarchien und Sammlungen wird die Genehmigung umgangen.  
>   
>  Bei Änderungen, die vom Stagingtabellenprozess vorgenommen werden, wird die Genehmigung umgangen.  
>   
>  Bei Änderungen, die durch eine Geschäftsregel vorgenommen werden, wird die Genehmigung umgangen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich der Systemverwaltung zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)  
  
-   Eine Entität muss vorhanden sein. Weitere Informationen finden Sie unter [Erstellen einer Entität &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="to-enable-approval-required-for-an-entity"></a>So aktivieren Sie „Genehmigung erforderlich“ für eine Entität  
  
1.  Klicken Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]auf **Systemverwaltung**.  
  
2.  Wählen Sie auf der Seite **Modell verwalten** im Raster ein Modell aus, und klicken Sie dann auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entität verwalten** im Raster die Zeile für die Entität aus, für die Sie  **Genehmigung erforderlich** aktivieren möchten.  
  
4.  Klicken Sie auf **Bearbeiten**, wählen Sie **Genehmigung erforderlich**, und klicken Sie dann auf **Speichern**.  
  
## <a name="see-also"></a>Siehe auch  
 [Changesets &#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)  
  
  
