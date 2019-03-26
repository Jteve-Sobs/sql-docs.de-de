---
title: Debuggen eines Skripts durch Festlegen von Breakpoints in einem Skripttask und einer Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b1719647906f96bdf5602ca6110195a141d4e787
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58277579"
---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>Debuggen eines Skripts durch Festlegen von Breakpoints in einem Skripttask und einer Skriptkomponente
  In diesem Verfahren wird beschrieben, wie Sie in den Skripts Breakpoints festlegen, die im Skripttask und in der Skriptkomponente verwendet werden.  
  
 Nachdem Sie im Skript Breakpoints festgelegt haben, werden im Dialogfeld **Breakpoints festlegen – \<Objektname>** die Breakpoints zusammen mit den integrierten Breakpoints aufgelistet.  
  
> [!IMPORTANT]  
>  In bestimmten Fällen werden Breakpoints im Skripttask und in der Skriptkomponente ignoriert. Weitere Informationen finden Sie im Abschnitt **Debugging the Script Task** (Debuggen des Skripttasks) unter [Coding and Debugging the Script Task](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) (Codieren und Debuggen des Skripttasks) sowie im Abschnitt **Debuggen der Skriptkomponente** unter [Codieren und Debuggen der Skriptkomponente](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md).  
  
### <a name="to-set-a-breakpoint-in-script"></a>So legen Sie einen Breakpoint im Skript fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie auf das Paket mit dem Skript, in dem Sie Breakpoints festlegen möchten.  
  
3.  Um den Skripttask zu öffnen, klicken Sie auf die Registerkarte **Ablaufsteuerung**, und doppelklicken Sie dann auf den Skripttask.  
  
4.  Um die Skriptkomponente zu öffnen, klicken Sie auf die Registerkarte **Datenfluss**, und doppelklicken Sie dann auf die Skriptkomponente.  
  
5.  Klicken Sie auf **Skript** und dann auf **Skript bearbeiten**.  
  
6.  Suchen Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) die Skriptzeile, für die Sie einen Breakpoint festlegen möchten, klicken Sie mit der rechten Maustaste auf diese Zeile, zeigen Sie auf **Breakpoint**, und klicken Sie dann auf **Breakpoint einfügen**.  
  
     Das Breakpointsymbol wird in der Codezeile angezeigt.  
  
7.  Klicken Sie im Menü **Datei** auf **Beenden**.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
  
