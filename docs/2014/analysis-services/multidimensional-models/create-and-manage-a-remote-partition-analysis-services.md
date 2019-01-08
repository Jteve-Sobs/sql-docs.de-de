---
title: Erstellen und verwalten eine Remotepartition (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], remote
- remote partitions [Analysis Services]
ms.assetid: 4322b5cb-af07-4e79-8ecb-59e1121a9eb8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b5f451a9948315a32710bdb1755bb95a5b8d3b98
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53356640"
---
# <a name="create-and-manage-a-remote-partition-analysis-services"></a>Erstellen und Verwalten einer Remotepartition (Analysis Services)
  Bei der Partitionierung einer Measuregruppe können Sie eine sekundäre Datenbank auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Remoteinstanz als Partitionsspeicher konfigurieren.  
  
 Remotepartitionen für einen Cube (die so genannte Masterdatenbank) werden in einer dedizierten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank auf der Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gespeichert (die so genannte sekundäre Datenbank).  
  
 Eine dedizierte sekundäre Datenbank kann Remotepartitionen für genau eine Masterdatenbank speichern, die Masterdatenbank kann jedoch mehrere sekundäre Datenbanken verwenden, solange sich alle sekundären Datenbank auf derselben Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]befinden. Dimensionen in einer dedizierten Datenbank für Remotepartitionen werden als verknüpfte Dimensionen erstellt.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Vor dem Erstellen einer Remotepartition müssen die folgenden Bedingungen erfüllt sein:  
  
-   Sie müssen über eine zweite [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz und eine dedizierte Datenbank zum Speichern der Partitionen verfügen. Die sekundäre Datenbank ist zweckgebunden; sie dient einer Masterdatenbank als Speicher für Remotepartitionen.  
  
-   Beide Serverinstanzen müssen die gleiche Version aufweisen. Beide Datenbanken sollten die gleiche Funktionsebene aufweisen.  
  
-   Beide Instanzen müssen für TCP-Verbindungen konfiguriert sein. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht unterstützt.  
  
-   Die Firewalleinstellungen auf beiden Computern müssen so festgelegt werden, dass sie Außenverbindungen akzeptieren. Weitere Informationen zum Einrichten der Firewall finden Sie unter [Konfigurieren der Windows-Firewall, um den Zugriff auf Analysis Services zuzulassen](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
-   Das Dienstkonto der Instanz, auf der die Masterdatenbank ausgeführt wird, erfordert Administratorzugriff auf die Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Wenn das Dienstkonto geändert wird, müssen Sie Berechtigungen sowohl für den Server als auch für die Datenbank aktualisieren.  
  
-   Sie müssen auf beiden Computern über [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Administratorrechte verfügen.  
  
-   Stellen Sie sicher, dass Ihr Notfallwiederherstellungsplan auch die Sicherung und Wiederherstellung der Remotepartitionen umfasst. Die Verwendung von Remotepartitionen kann Sicherungs- und Wiederherstellungsvorgänge erschweren. Führen Sie gründliche Tests für den Plan aus, um sicherzustellen, dass die erforderlichen Daten wiederhergestellt werden.  
  
## <a name="configure-remote-partitions"></a>Konfigurieren von Remotepartitionen  
 Zwei separate Computer, auf denen jeweils eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ausgeführt wird, sind erforderlich, um ein Szenario mit Remotepartitionen einzurichten, in dem ein Computer als Masterserver und der andere als untergeordneter Server fungiert.  
  
 Bei der folgenden Prozedur wird vorausgesetzt, dass Sie über zwei Serverinstanzen verfügen, wobei auf dem Masterserver eine Cubedatenbank bereitgestellt wird. In dieser Prozedur wird die Cubedatenbank als "db-master" bezeichnet. Die Speicherdatenbank mit den Remotepartitionen wird als "db-storage" bezeichnet.  
  
 Um diese Schritte abzuschließen, benötigen Sie sowohl [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] als auch [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
> [!NOTE]  
>  Remotepartitionen können nur mit anderen Remotepartitionen zusammengeführt werden. Wenn Sie lokale Partitionen mit Remotepartitionen kombinieren, besteht ein alternativer Ansatz in der Erstellung neuer Partitionen, die die kombinierten Daten enthalten. Die nicht mehr benötigten Partitionen werden gelöscht.  
  
#### <a name="specify-valid-server-names-for-cube-deployment-in-ssdt"></a>Festlegen gültiger Servernamen für die Cubebereitstellung (in SSDT)  
  
1.  Auf dem Masterserver: Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Namens der Projektmappe, und wählen Sie **Eigenschaften**. Klicken Sie im Dialogfeld **Eigenschaften** auf **Konfigurationseigenschaften**, klicken Sie erst auf **Bereitstellung**und dann auf **Server** , um den Namen des Masterservers festzulegen.  
  
2.  Auf dem untergeordneten Server: Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste in des Namens der Projektmappe, und wählen Sie **Eigenschaften**. Klicken Sie im Dialogfeld **Eigenschaften** auf **Konfigurationseigenschaften**, klicken Sie erst auf **Bereitstellung**und dann auf **Server** , und legen Sie den Namen des untergeordneten Servers fest.  
  
#### <a name="create-and-deploy-a-secondary-database-in-ssdt"></a>Erstellen und Bereitstellen einer sekundären Datenbank (in SSDT)  
  
1.  Auf dem untergeordneten Server: Erstellen Sie ein neues Analysis Services-Projekt für die Storage-Datenbank.  
  
2.  Auf dem untergeordneten Server: Erstellen Sie im Projektmappen-Explorer eine neue Datenquelle, die auf die Cubedatenbank Db-Master. Verwenden Sie den Anbieter **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.  
  
3.  Auf dem untergeordneten Server: Bereitstellen der Projektmappe  
  
#### <a name="enable-features-in-ssms"></a>Aktivieren von Funktionen (in SSMS)  
  
1.  Auf dem untergeordneten Server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], mit der rechten Maustaste die verbundene [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz im Objekt-Explorer, und wählen **Eigenschaften**. Legen Sie sowohl **Feature\LinkToOtherInstanceEnabled** als auch **Feature\LinkFromOtherInstanceEnabled** auf **TRUE**fest.  
  
2.  Auf dem untergeordneten Server: Starten Sie den Server neu, indem Sie mit der rechten Maustaste des Servernamen im Objekt-Explorer und auswählen **Neustart**.  
  
3.  Auf dem Masterserver: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], mit der rechten Maustaste die verbundene [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz im Objekt-Explorer, und wählen **Eigenschaften**. Legen Sie sowohl **Feature\LinkToOtherInstanceEnabled** als auch **Feature\LinkFromOtherInstanceEnabled** auf **TRUE**fest.  
  
4.  Auf dem Masterserver: Klicken Sie zum Neustarten des Servers, mit der rechten Maustaste des Servernamen im Objekt-Explorer, und wählen Sie **Neustart**.  
  
#### <a name="set-the-masterdatasourceid-database-property-on-the-remote-server-in-ssms"></a>Festlegen der MasterDataSourceID-Datenbankeigenschaft für den Remoteserver (in SSMS)  
  
1.  Auf dem untergeordneten Server: Mit der rechten Maustaste in des Speichers,-Db-Storage-Datenbank, zeigen Sie auf **Skript für Datenbank als** | **ALTER in** | **neues Abfrage-Editor-Fenster**.  
  
2.  Fügen Sie **MasterDataSourceID** der XMLA hinzu, und geben Sie die ID der Cubedatenbank „db-master“ als Wert an. Die XMLA sollte ähnlich wie im folgenden Beispiel aussehen:  
  
    ```  
    <Alter ObjectExpansion="ExpandFull" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
       <DatabaseID>DB-Storage</DatabaseID>  
    </Object>  
    <ObjectDefinition>  
       <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" 400"   
          <ID>DB-Storage</ID>  
          <Name>DB-StorageB</Name>  
          <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
          <Language>1033</Language>  
          <Collation>Latin1_General_CI_AS</Collation>  
          <DataSourceImpersonationInfo>  
    <ImpersonationMode>ImpersonateAccount</ImpersonationMode>  
             <Account>*********</Account>  
          </DataSourceImpersonationInfo>  
          <MasterDataSourceID>DB-Master</MasterDataSourceID>  
       </Database>  
    </ObjectDefinition>  
    </Alter>  
    ```  
  
3.  Drücken Sie F5, um das Skript auszuführen.  
  
#### <a name="set-up-the-remote-partition-in-ssdt"></a>Einrichten der Remotepartition (in SSDT)  
  
1.  Auf dem Masterserver: Öffnen Sie den Cube im Cube-Designer, und klicken Sie auf **Partitionen** Registerkarte. Erweitern Sie die Measuregruppe. Klicken Sie auf **Neue Partition** , wenn die Measuregruppe bereits für mehrere Partitionen konfiguriert ist, oder klicken Sie in der Quellspalte auf die Schaltfläche zum Durchsuchen (. befinden. ), um die bestehende Partition zu bearbeiten.  
  
2.  Wählen Sie im Partitions-Assistenten unter **Quellinformationen angeben**die ursprüngliche Datenquellensicht und die Faktentabelle aus.  
  
3.  Bei Verwendung einer Abfragebindung geben Sie eine WHERE-Klausel an, durch die die Daten für die neu erstellte Partition segmentiert werden.  
  
4.  Wählen Sie in **Speicherorte zum Verarbeiten und Speichern**unter **Verarbeitungsstandort**die Option **Remotedatenquelle für SQL Server Analysis Services** aus, und klicken Sie auf **Neu** , um eine neue Datenquelle zu erstellen, die auf die untergeordnete Datenbank „db-storage“ zeigt.  
  
    > [!NOTE]  
    >  Wenn der Fehler angezeigt wird, dass die Datenquelle in der Sammlung nicht vorhanden ist, müssen Sie das Speicherdatenbank-Projekt "db-storage" und eine Datenquelle erstellen, die auf die Masterdatenbank "db-master" zeigt.  
  
5.  Auf dem Masterserver: Mit der rechten Maustaste des Cubenamen im Projektmappen-Explorer, wählen **Prozess** und den Cube vollständig verarbeiten.  
  
## <a name="administering-remote-partitions"></a>Verwalten von Remotepartitionen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt sowohl die parallele als auch die sequenzielle Verarbeitung von Remotepartitionen. Die Transaktionen sämtlicher Instanzen, die an der Verarbeitung der Partitionen eines Cubes beteiligt sind, werden von der Masterdatenbank koordiniert, in der die Partitionen definiert wurden. Anschließend werden Verarbeitungsberichte an alle Instanzen gesendet, durch die eine Partition verarbeitet wurde.  
  
 Ein Cube, der Remotepartitionen enthält, kann zusammen mit den zugehörigen Partitionen in einer einzelnen Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]verwaltet werden. Die Metadaten für die Remotepartition können jedoch nur in der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] angezeigt und aktualisiert werden, in der die Partition und deren übergeordneter Cube definiert wurden. Die Remotepartition kann in der Remoteinstanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]nicht angezeigt oder aktualisiert werden.  
  
> [!NOTE]  
>  Obwohl für die Speicherung von Remotepartitionen dedizierte Datenbanken nicht für Schemarowsets verfügbar gemacht werden, können Anwendungen, die Analysis Management Objects (AMO) verwenden, eine dedizierte Datenbank weiterhin mithilfe des Discover-Befehls von XML for Analysis ermitteln. Über einen TCP- oder HTTP-Client direkt an eine dedizierte Datenbank gesendete CREATE- oder DELETE-Befehle werden zwar erfolgreich ausgeführt, der Server gibt jedoch eine Warnung mit dem Hinweis zurück, dass diese dediziert verwaltete Datenbank durch die Aktion beschädigt werden könnte.  
  
## <a name="see-also"></a>Siehe auch  
 [Partitionen &#40;Analysis Services – Mehrdimensionale Daten&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
