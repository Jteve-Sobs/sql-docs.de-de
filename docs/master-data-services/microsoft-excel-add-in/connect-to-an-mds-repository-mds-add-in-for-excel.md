---
title: Herstellen einer Verbindung mit einem MDS-Repository (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 711c76e4db62c274fe62d2319b3438799954d1c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139366"
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a>Herstellen einer Verbindung mit einem MDS-Repository (MDS-Add-In für Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]müssen Sie eine Verbindung mit einem MDS-Repository herstellen, bevor Sie Daten laden oder veröffentlichen können.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
### <a name="to-connect-to-an-mds-repository"></a>So stellen Sie eine Verbindung mit einem MDS-Repository her  
  
1.  Klicken Sie in MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]auf die Registerkarte **Masterdaten** , klicken Sie in der Gruppe **Verbinden und Laden** auf den Pfeil unter der Schaltfläche **Verbinden** , und klicken Sie auf **Verbindungen verwalten**.  
  
2.  Klicken Sie im Dialogfeld **Verbindungen verwalten** im Abschnitt **Neue Verbindung** auf **Neue Verbindung erstellen**.  
  
3.  Klicken Sie auf **Neu**.  
  
4.  Geben Sie im Dialogfeld **Neue Verbindung hinzufügen** im Feld **Beschreibung** eine Beschreibung für die Verbindung ein. Diese Verbindung wird angezeigt, wenn Sie auf den Pfeil unter der Schaltfläche **Verbinden** auf der Symbolleiste klicken.  
  
5.  Geben Sie im Feld **MDS-Serveradresse** die URL der [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]-Webanwendung ein, z.B. `https://contoso/mds`.  
  
    > [!NOTE]  
    >  Stellen Sie sicher, dass Sie den Computernamen verwenden und nicht „localhost“.  
  
6.  Klicken Sie auf **OK**. Der Name wird im Abschnitt **Vorhandene Verbindungen** angezeigt.  
  
7.  Klicken Sie optional auf **Testen** , um die Verbindung zu testen. Ein Bestätigungs- oder Fehlerdialogfeld wird angezeigt. Klicken Sie auf **OK** , um es zu schließen.  
  
8.  Klicken Sie auf **Verbinden**. Der Bereich **Master Data Services** wird angezeigt.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Exportieren von Daten nach Excel aus Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)  
  
-   [Filter Data before Exporting &#40;MDS Add-in for Excel&#41; (Filtern von Daten vor dem Exportieren (MDS-Add-In für Excel))](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verbindungen &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
  
