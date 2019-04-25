---
title: Reparieren einer Distributed Replay-Installation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d14b1bf3200802e9fab359ba3ede9fa295911fe1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760926"
---
# <a name="repair-a-distributed-replay-installation"></a>Reparieren einer Distributed Replay-Installation
  Zur Reparatur einer Distributed Replay-Komponente (Controller oder Client) gehen Sie wie folgt vor:  
  
1.  Installieren Sie alle zugehörigen Dateien erneut auf dem Datenträger, und ersetzen Sie dabei alle vorhandenen Dateien.  
  
2.  Wenn das entsprechende Windows-Dienstkonto entfernt wurde, erstellen Sie dieses erneut.  
  
 Über den Reparaturvorgang können Sie Komponenten nicht hinzuzufügen oder entfernen. Klicken Sie zum Hinzufügen oder Entfernen von Komponenten, überprüfen Sie, oder deaktivieren Sie die entsprechende Komponente in der Funktionsstruktur auf der **Funktionsauswahl** auf der Seite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>So reparieren Sie eine fehlerhafte Distributed Replay-Installation  
  
1.  Von der **starten** Menü klicken Sie auf **Systemsteuerung**, und doppelklicken Sie dann auf **Software**.  
  
2.  Wählen Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in die **deinstallieren oder Ändern eines Programms** Fenster, und klicken Sie dann in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] im Dialogfeld klicken Sie auf **reparieren**.  
  
3.  Führen Sie die Schritte in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Assistenten, und klicken Sie auf die **Features auswählen** Seite, wählen Sie die Distributed Replay-Komponenten, die Sie reparieren möchten, und klicken Sie dann auf **weiter.**.  
  
4.  Schließen Sie den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Installations-Assistenten ab, um die ausgewählten Distributed Replay-Funktionen zu reparieren.  
  
  
