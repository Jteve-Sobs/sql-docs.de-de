---
title: Automatisches Generieren von Attributwerten
titleSuffix: Master Data Services
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b82f6f81-6e9c-4918-9ea9-4ab5f5d11b15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: dc4ee9fd4eead46df29538a85013949402b1920e
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73728730"
---
# <a name="automatically-generate-attribute-values-other-than-code-master-data-services"></a>Automatisches Generieren von anderen Attributwerten als Code (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] können Sie Werte für die Attributwerte einer Entität automatisch generieren, wenn Sie möchten, dass eine ganze Zahl jedes Mal automatisch als Wert zugewiesen werden soll, wenn Geschäftsregeln angewendet werden.  
  
## <a name="prerequisites"></a>Prerequisites  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)zuzugreifen.  
  
-   Ein numerisches Attribut muss vorhanden sein. Weitere Informationen finden Sie unter [Erstellen eines numerischen Attributs &#40;Master Data Services&#41;](../master-data-services/create-a-numeric-attribute-master-data-services.md).  
  
### <a name="to-automatically-generate-an-attribute-value"></a>So generieren Sie automatisch einen Attributwert  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Geschäftsregeln**.  
  
3.  Wählen Sie auf der Seite **Verwaltung von Geschäftsregeln** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie aus der Liste **Entität** eine Entität aus.  
  
5.  Wählen Sie aus der Liste **Elementtyp** einen Typ des Elements aus, auf das die Geschäftsregel angewendet werden soll.  
  
6.  Behalten Sie in der Liste **Attribut** die Standardeinstellung **Alle**bei.  
  
7.  Klicken Sie auf **Geschäftsregel hinzufügen**.  
  
8.  Klicken Sie auf **Ausgewählte Geschäftsregel bearbeiten**.  
  
9. Erweitern Sie im Bereich **Komponenten** den Knoten **Aktionen** .  
  
10. Klicken Sie im Knoten „Standardwert“ auf **entspricht standardmäßig generiertem Wert**, und ziehen Sie ihn auf die Beschriftung **Aktionen** des Bereichs **THEN**.  
  
11. Klicken Sie im Bereich **Attribute** auf das Attribut mit dem zu generierenden Wert, und ziehen Sie es in die Beschriftung **Attribut auswählen** des Bereichs **Aktion bearbeiten** .  
  
12. Geben Sie in den Feldern **Start bei** und **Erhöhen um** einen Wert ein. Wenn Elemente bereits vorhanden sind, wird der Wert auf Grundlage des höchsten vorhandenen Werts festgelegt. Wenn der höchste vorhandene Wert zum Beispiel 299 beträgt und Sie **Erhöhen um** auf **1**festgelegt haben, wird der Wert des nächsten Elements auf 300 festgelegt.  
  
13. Klicken Sie im Bereich **Aktion bearbeiten** auf **Element speichern**.  
  
14. Klicken Sie auf **Zurück**.  
  
15. Optional können Sie auf der Seite **Verwaltung von Geschäftsregeln** für die Zeile, die die Geschäftsregel enthält, auf eine Zelle in den Spalten **Name**, **Beschreibung**oder **Benachrichtigung** doppelklicken, um den Wert zu aktualisieren.  
  
16. Klicken Sie auf **Geschäftsregeln veröffentlichen**.  
  
17. Klicken Sie im Bestätigungsdialogfeld auf **OK**. Der Status der Regel ändert sich zu **Aktiv**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Überprüfen von bestimmten Elementen auf Geschäftsregeln &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
-   [Überprüfen einer Version anhand von Geschäftsregeln &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Automatische Codeerstellung &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md)   
 [Geschäftsregeln &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)   
 [Überprüfung &#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)  
  
  
