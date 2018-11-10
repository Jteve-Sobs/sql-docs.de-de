---
title: Exportieren einer Wissensdatenbank in eine DQS-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a324ead5-c8aa-4e26-abe3-ef415add00f8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 412744c2bd1ea88e3a85f0cacad5267b1d341969
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033377"
---
# <a name="export-a-knowledge-base-to-a-dqs-file"></a>Exportieren einer Wissensdatenbank in eine DQS-Datei
  In diesem Thema wird beschrieben, wie eine gesamte Wissensdatenbank in eine DQS-Datendatei in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) exportiert wird. Sie können eine Domäne oder eine ganze Wissensdatenbank in eine Datendatei exportieren. Weitere Informationen zum Exportieren einer Domäne finden Sie unter [Exportieren einer Domäne in eine DQS-Datei](../../2014/data-quality-services/export-a-domain-to-a-dqs-file.md).  
  
 Indem Sie eine Wissensdatenbank in eine DQS-Datei exportieren und diese dann als weitere Wissensdatenbank importieren, wird der Wissensgenerierungsprozess vereinfacht, Zeit gespart und der Aufwand verringert. Auf diese Weise haben Sie die Möglichkeit, eine Wissensdatenbank und ihr Wissen zusammen mit anderen zu nutzen. Die DQS-Datei enthält alle Informationen aus der Wissensdatenbank, einschließlich Domänen und der Abgleichsrichtlinie, aber keine Informationen über angefügte Verweisdaten. Nachdem Sie die DQS-Datei importiert haben, müssen Sie die erforderlichen Domänen ggf. erneut an die entsprechenden Verweisdatendienste anfügen. Sowohl veröffentlichte als auch nicht veröffentlichte Daten in einer Wissensdatenbank werden exportiert.  
  
 Die durch den Exportvorgang erstellte DQS-Datendatei wird verschlüsselt, damit der Inhalt nicht angezeigt werden kann.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
 Um eine Wissensdatenbank in eine DQS-Datendatei zu exportieren, müssen Sie zuvor eine Wissensdatenbank erstellt und geöffnet haben. Sie benötigen für den Export keine DQS-Datei. Eine DQS-Datei wird für Sie erstellt.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie müssen über die Rolle „dqs_kb_editor“ oder „dqs_administrator“ in der DQS_MAIN-Datenbank verfügen, um eine Wissensdatenbank in eine DQS-Datendatei zu exportieren.  
  
##  <a name="Export"></a> Exportieren einer Wissensdatenbank in eine DQS-Datei  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ausführen der Data Quality-Clientanwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Öffnen Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm in der Domänenverwaltungsaktivität eine Wissensdatenbank.  
  
3.  Klicken Sie auf der Seite „Domänenverwaltung“ (bei Auswahl einer beliebigen Registerkarte) oberhalb der Domänenliste auf das Symbol **Daten der Wissensdatenbank exportieren** , und klicken Sie dann auf **Wissensdatenbank exportieren**. Sie können alternativ auch mit der rechten Maustaste in der Liste **Domäne** klicken, auf **Exportieren**zeigen und dann auf **Wissensdatenbank exportieren**klicken.  
  
4.  Wechseln Sie im Dialogfeld **In Datendatei exportieren** zu dem Ordner, in dem Sie die Datei speichern möchten, benennen Sie die Datei, oder behalten Sie den Namen der Wissensdatenbank bei, übernehmen Sie **DQS-Datendateien (\*.dqs)** als Dateityp unter **Speichern unter**, und klicken Sie dann auf **Speichern**.  
  
5.  Überprüfen Sie im Dialogfeld **Wissensdatenbank exportieren** , ob die Statuszeile angibt, dass der Exportvorgang abgeschlossen wurde. Klicken Sie auf **OK**.  
  
##  <a name="FollowUp"></a> Nachverfolgung: Nach dem Exportieren einer Domäne in eine DQS-Datei  
 Nachdem Sie eine Wissensdatenbank in eine DQS-Datei exportiert haben, können Sie die Wissensdatenbank in den gleichen [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (unter einem neuen Namen) oder in einen anderen [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]importieren.  
  
  
