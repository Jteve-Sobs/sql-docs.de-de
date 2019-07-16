---
title: Trennen und Wiederherstellen der Verbindung des Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9829ddfd7e625941c97bd3b2027c328a1fba93d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925514"
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Trennen und erneutes Herstellen einer Verbindung mit dem Recordset
Eines der leistungsstärksten Features finden Sie in ADO ist die Möglichkeit, öffnen Sie ein Recordset clientseitige aus einer Datenquelle, und trennen Sie dann das Recordset aus der Datenquelle. Sobald das Recordset getrennt wurde, kann die Verbindung mit der Datenquelle geschlossen werden, und Freigabe der Ressourcen auf dem Server verwendet, um ihn zu verwalten. Sie können weiterhin anzeigen und bearbeiten die Daten im Recordset, während er getrennt ist und später wieder mit der Datenquelle herstellen und senden Ihre Updates im Batchmodus ausgeführt.  
  
 Wenn Sie ein Recordset trennen möchten, öffnen Sie es mit dem Cursor Standort AdUseClient, und legen Sie die ActiveConnection-Eigenschaft auf "Nothing". (C++-Benutzer sollten ActiveConnection gleich NULL, um die Verbindung trennen festgelegt.)  
  
 Wir verwenden ein getrenntes Recordset später in diesem Abschnitt, wenn wir erörtern Recordset-Beibehaltung, um ein Szenario zu beheben, in denen müssen wir haben die Daten in einem Recordset für eine Anwendung verfügbar, während der Clientcomputer nicht mit einem Netzwerk verbunden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Batchmodus](../../../ado/guide/data/batch-mode.md)
