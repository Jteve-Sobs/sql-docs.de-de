---
description: Zuordnen von Abfrageparametern zu Variablen in einer Datenflusskomponente
title: Zuordnen von Abfrageparametern zu Variablen in einer Datenflusskomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d9cb92a6815e41bfffbcf449c98077ab71d25467
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430822"
---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a>Zuordnen von Abfrageparametern zu Variablen in einer Datenflusskomponente

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Wenn Sie die OLE DB-Quelle so konfigurieren, dass parametrisierte Abfragen verwendet werden, können Sie die Parameter Variablen zuordnen.  
  
 Die OLE DB-Quelle verwendet parametrisierte Abfragen zum Filtern von Daten verwenden, wenn die Quelle eine Verbindung zu einer Datenquelle herstellt.  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>So ordnen Sie einer Variablen einen Abfrageparameter zu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus dem Bereich **Toolbox**die OLE DB-Quelle mit der Maus auf die Entwurfsoberfläche.  
  
4.  Klicken Sie mit der rechten Maustaste auf die OLE DB-Quelle, und klicken Sie dann auf **Bearbeiten**.  
  
5.  Wählen Sie im **Quellen-Editor für OLE DB**einen OLE DB-Verbindungs-Manager zum Herstellen einer Verbindung mit der Datenquelle aus, oder klicken Sie auf **Neu** , um einen neuen OLE DB-Verbindungs-Manager zu erstellen.  
  
6.  Wählen Sie die Option **SQL-Befehl** als Datenzugriffsmodus aus, und geben Sie im Bereich **SQL-Befehlstext** eine parametrisierte Abfrage ein.  
  
7.  Klicken Sie auf **Parameter**.  
  
8.  Ordnen Sie im Dialogfeld **Abfrageparameter festlegen** alle Parameter in der Liste **Parameter** einer Variablen in der Liste **Variablen** zu, oder klicken Sie auf **\<New variable>** , um eine neue Variable zu erstellen. Klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Nur Systemvariablen und benutzerdefinierte Variablen im Bereich des Pakets, ein übergeordneter Container (z. B. eine Foreach-Schleife) oder der Datenflusstask, in dem die Datenflusskomponente enthalten ist, können zugeordnet werden. Die Variable muss einen Datentyp aufweisen, der mit der Spalte in der WHERE-Klausel kompatibel ist, der der Parameter zugewiesen wird.  
  
9. Sie können auf **Vorschau** klicken, um bis zu 200 Zeilen der von der Abfrage zurückgegebenen Daten anzuzeigen.  
  
10. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Quelle](../../integration-services/data-flow/ole-db-source.md)   
 [Suchtransformation](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
