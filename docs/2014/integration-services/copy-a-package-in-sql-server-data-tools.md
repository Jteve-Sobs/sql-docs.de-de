---
title: Kopieren eines Pakets in SQL Server Data Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], copying
- copying packages
- regenerating package GUID
- updating package properties
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 673b69ea632108b889cc2f99b63c9c602ef05237
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58388816"
---
# <a name="copy-a-package-in-sql-server-data-tools"></a>Kopieren eines Pakets in SQL Server-Datentools
  In diesem Thema wird beschrieben, wie Sie ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Paket durch Kopieren eines vorhandenen Pakets erstellen und wie Sie die Eigenschaften `Name` und `GUID` des neuen Pakets aktualisieren.  
  
### <a name="to-copy-a-package"></a>So kopieren Sie ein Paket  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt mit dem Paket, das Sie kopieren möchten.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket.  
  
3.  Stellen Sie entweder sicher, dass das zu kopierende Paket im Projektmappen-Explorer ausgewählt ist oder dass die Registerkarte im SSIS-Designer, in dem das Paket enthalten ist, aktiviert ist.  
  
4.  Klicken Sie im Menü **Datei** auf **\<Paketname> speichern unter**.  
  
    > [!NOTE]  
    >  Das Paket muss im SSIS-Designer geöffnet sein, bevor im Menü **Datei** die Option **Speichern unter** angezeigt wird.  
  
5.  Suchen Sie optional nach einem anderen Ordner.  
  
6.  Aktualisieren Sie den Namen der Paketdatei. Stellen Sie sicher, dass die Dateierweiterung DTSX beibehalten wird.  
  
7.  Klicken Sie auf **Speichern**.  
  
8.  Wählen Sie an der Eingabeaufforderung aus, ob der Name des Paketobjekts zur Übereinstimmung mit dem Dateinamen aktualisiert werden soll. Wenn Sie auf **Ja**, `Name` -Eigenschaft des Pakets wird aktualisiert. Das neue Paket wird dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt hinzugefügt und im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer geöffnet.  
  
9. Klicken Sie optional in den Hintergrund der Registerkarte **Ablaufsteuerung** , und klicken Sie auf **Eigenschaften**.  
  
10. Klicken Sie im Eigenschaftenfenster auf den Wert der ID-Eigenschaft, und klicken Sie anschließend in der Dropdownliste auf **\<Neue ID generieren>**.  
  
11. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das neue Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Speichern einer Kopie eines Pakets](../../2014/integration-services/save-a-copy-of-a-package.md)   
 [Erstellen von Paketen in SQL Server-Datentools](create-packages-in-sql-server-data-tools.md)   
 [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) (Integration Services-Pakete [SSIS])  
  
  
