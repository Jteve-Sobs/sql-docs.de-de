---
title: Eigenschaften von NS$&lt;Dienstname&gt; (Registerkarte „Anmelden“)
description: In diesem Artikel erhalten Sie Informationen zur Registerkarte „Anmelden“ des Dialogfelds „Notification Services Properties“ (Eigenschaften der Notification Services) in SQL Server. Sie erfahren, wie Sie ein Konto angeben und den Dienst starten oder anhalten.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 5e6816ec-d4c5-4429-8033-b97427584890
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7dbd0bca6e392b6a3037cef2ab05975829d5972b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883183"
---
# <a name="nsltservice-namegt-properties-log-on-tab"></a>Eigenschaften von NS$&lt;Dienstname&gt; (Registerkarte „Anmelden“)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Verwenden Sie im Dialogfeld **Notification Services-Eigenschaften** die Registerkarte **Anmelden** , um das vom [!INCLUDE[ssNS](../../includes/ssns-md.md)] -Dienst verwendete Konto anzugeben und den Dienst zu starten und zu beenden.  
  
## <a name="options"></a>Tastatur  
 **Lokales System**  
 Geben Sie ein lokales Systemkonto an, das kein Kennwort erfordert. Das lokale Systemkonto kann sich allerdings einschränkend auf die Zusammenarbeit mit anderen Servern auswirken. Dies hängt von den Privilegien ab, die dem Konto erteilt wurden.  
  
 **Dieses Konto**  
 Geben Sie ein lokales oder ein Domänenbenutzerkonto an, das die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung verwendet. [!INCLUDE[msCoName](../../includes/msconame-md.md)] empfiehlt, ein Domänenbenutzerkonto mit minimalen Berechtigungen für Dienste zu verwenden. Informationen zum Auswählen eines Kontos finden Sie in der Onlinedokumentation unter "Einrichten von Windows-Dienstkonten".  
  
 **Kontoname**  
 Geben Sie den Kontonamen des lokalen oder Domänenbenutzers an.  
  
 **Kennwort**  
 Geben Sie das Kennwort des Kontos ein.  
  
 **Kennwort bestätigen**  
 Geben Sie das Kennwort des Kontos erneut ein.  
  
 **Starten**  
 Starten Sie den Dienst.  
  
 **Beenden**  
 Beenden Sie den Dienst.  
  
 **Anhalten**  
 Halten Sie den Dienst an.  
  
 **Fortsetzen**  
 Setzen Sie einen angehaltenen Dienst fort.  
  
  
