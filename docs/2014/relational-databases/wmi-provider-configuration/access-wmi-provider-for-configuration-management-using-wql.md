---
title: Zugreifen auf WMI-Anbieter für die Konfigurationsverwaltung mit WQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: adec01de84122552812e5b1b28277d0d399fee56
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795432"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>Zugreifen auf WMI-Anbieter für die Konfigurationsverwaltung mit WQL
  In diesem Abschnitt wird beschrieben, wie [!INCLUDE[msCoName](../../includes/msconame-md.md)] WQL-Anweisungen (Windows Management Instrumentation Query Language, Abfragesprache der Windows-Verwaltungsinstrumentation) für den WMI-Anbieter für die Computerverwaltung ausgeführt werden.  
  
 Im Beispiel wird ein WQL-Editor, WBEMtest.exe, zum Ausführen von WQL-Abfragen für den WMI-Anbieter verwendet, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste, -Netzwerkprotokolle und -Aliasnamen aufzuzählen.  
  
### <a name="querying-services-using-wbemtest"></a>Abfragen von Diensten mit WBEMtest  
  
1.  Von der **starten** Menü klicken Sie auf **ausführen**, und geben Sie dann `WBEMtest`.  
  
2.  Das Dialogfeld WBEMtest.exe wird angezeigt. Klicken Sie auf **Verbinden**.  
  
3.  Geben Sie im ersten Textfeld den Namespace für den WMI-Anbieter für die Computerverwaltung ein: root\Microsoft\SqlServer\ComputerManagement11. Klicken Sie auf **Verbinden**.  
  
4.  Klicken Sie auf **Abfrage**. Geben Sie eine Abfrage, die die aktuelle, auf dem lokalen Computer ausgeführten Dienste zurückgibt: **Wählen Sie \* FROM SqlService.** Klicken Sie auf **Anwenden**.  
  
5.  Verfeinern Sie die Abfrage weiter, indem Sie `WHERE ServiceName = "MSSQLSERVER"` hinzufügen.  
  
  
