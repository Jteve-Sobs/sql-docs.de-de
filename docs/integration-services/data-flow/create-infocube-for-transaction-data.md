---
title: InfoCube für Transaktionsdaten erstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
author: janinezhang
ms.author: janinez
ms.openlocfilehash: f0ca83c61a09c03c5c066da4b65a5a342f86c631
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045247"
---
# <a name="create-infocube-for-transaction-data"></a>InfoCube für Transaktionsdaten erstellen

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Verwenden Sie das Dialogfeld **InfoCube für Transaktionsdaten erstellen** , um einen neuen InfoCube für Transaktionsdaten im SAP NetWeaver BW-System zu erstellen.  
  
 Sie können das Dialogfeld **InfoCube für Transaktionsdaten erstellen** im **Ziel-Editor für SAP BW** auf der Seite **Verbindungs-Manager**öffnen. Weitere Informationen zum SAP BW-Ziel finden Sie unter [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  Die Dokumentation für Microsoft Connector 1.1 for SAP BW setzt Kenntnisse der SAP NetWeaver BW-Umgebung voraus. Weitere Informationen zu SAP NetWeaver BW oder Informationen zur Konfiguration von SAP NetWeaver BW-Objekten und -Prozessen finden Sie in der SAP-Dokumentation.  
  
 **So öffnen Sie das Dialogfeld "InfoCube für Transaktionsdaten erstellen"**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paket, in dem das SAP BW-Ziel enthalten ist.  
  
2.  Doppelklicken Sie auf der Registerkarte **Datenfluss** auf das SAP BW-Ziel.  
  
3.  Klicken Sie im **Ziel-Editor für SAP BW**auf **Verbindungs-Manager** , um die Seite **Verbindungs-Manager** des Editors zu öffnen.  
  
4.  Wählen Sie auf der Seite **Verbindungs-Manager** im Gruppenfeld **SAP BW-Objekte erstellen** die Option **InfoCube**aus, und klicken Sie dann auf **Erstellen**.  
  
## <a name="general-options"></a>Allgemeine Optionen  
 **InfoCube-Name**  
 Geben Sie einen Namen für den neuen InfoCube ein.  
  
 **Lange Beschreibung**  
 Geben Sie eine Beschreibung für den neuen InfoCube ein.  
  
 **Speichern und aktivieren**  
 Speichern und aktivieren Sie den neuen InfoCube.  
  
## <a name="infocube-transfer-structure-options"></a>Optionen für die InfoCube-Übergangsstruktur  
 Im Abschnitt für die InfoCube-Übergangsstruktur können Sie InfoObjects Datenflussspalten zuordnen.  
  
 **PipelineElement**  
 Zeigt die Spalte in der Ausgabe des Datenflusses an, der mit dem SAP BW-Ziel verbunden ist.  
  
 **PipelineDataType**  
 Zeigt den Datentyp der Datenflussspalte an.  
  
 **InfoObject**  
 Zeigt den Namen des InfoObject an, das der Datenflussspalte zugeordnet ist.  
  
 **Typ**  
 Zeigt den Typ des InfoObject an, das der Datenflussspalte zugeordnet ist. In der folgenden Tabelle sind die möglichen Werte für den Typ aufgelistet.  
  
|value|und Beschreibung|  
|-----------|-----------------|  
|CHA|Merkmale|  
|UNI|Einheiten|  
|KYF|Kennzahlen|  
|TIM|Zeitmerkmale|  
  
 **Iobject - Suchen**  
 Ordnen Sie der Datenflussspalte der aktuellen Zeile ein vorhandenes InfoObject zu. Um diese Zuordnung zu erstellen, klicken Sie auf **Suchen**und verwenden dann das Dialogfeld **InfoObject suchen** , um das vorhandene InfoObject auszuwählen. Weitere Informationen zu diesem Dialogfeld finden Sie unter [Look Up InfoObject](../../integration-services/data-flow/look-up-infoobject.md).  
  
 Nachdem Sie ein vorhandenes InfoObject ausgewählt haben, werden die Spalten **InfoObject** und **Typ** von der Komponente mit den ausgewählten Werten aufgefüllt.  
  
 **Iobject - Neu**  
 Erstellen Sie ein neues InfoObject, und ordnen Sie dieses neue InfoObject der Datenflussspalte in der aktuellen Zeile zu. Um das neue InfoObject zu erstellen, klicken Sie auf **Neu**und erstellen dann das InfoObject im Dialogfeld **Neues InfoObject erstellen** . Weitere Informationen zu diesem Dialogfeld finden Sie unter [Create New InfoObject](../../integration-services/data-flow/create-new-infoobject.md).  
  
 Nachdem Sie ein neues InfoObject erstellt haben, werden die Spalten **InfoObject** und **Typ** mit den neuen Werten aufgefüllt.  
  
 **Iobject - Entfernen**  
 Heben Sie die Zuordnung zwischen dem InfoObject und der Datenflussspalte für die aktuelle Zeile auf. Um die Zuordnung aufzuheben, klicken Sie auf **Entfernen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [F1-Hilfe zum Microsoft Connector for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
