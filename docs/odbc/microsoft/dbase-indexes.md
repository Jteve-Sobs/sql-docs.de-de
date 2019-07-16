---
title: dBASE-Indizes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase indexes [ODBC]
- DBase driver [ODBC], indexes
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d9a0a57c3dce920c6d5fbc2510932066cb5a2659
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096360"
---
# <a name="dbase-indexes"></a>dBASE-Indizes
Der ODBC-dBASE-Treiber wird automatisch geöffnet wird und aktualisiert Indexdateien dBASE IV. Verwenden Sie die **Indizes auswählen** Dialogfeld angezeigt, über die ODBC-Datenquellen-Administrator, dBASE-Dateien dBASE III NDX-Dateien zugeordnet werden soll.  
  
 Die folgenden Einschränkungen gelten für die Erstellung von dBASE-Indizes:  
  
-   Alle Spaltennamen müssen gültig sein.  
  
-   Alle Spalten muss in der derselben aufsteigenden oder absteigenden Reihenfolge.  
  
-   Die Länge jeder einzelnen Textspalte muss weniger als 100 Bytes sein.  
  
-   Wenn mehr als eine Spalte vorhanden ist, muss alle Spalten in den Spalten und die Summe der Größen für die Spalte muss weniger als 100 Bytes sein.  
  
-   Memo-Felder können nicht indiziert werden.  
  
-   Ein Index darf nicht für den aktuellen Satz von Feldern angegeben werden (d. h. doppelt vorhandene Indizes sind nicht zulässig).  
  
-   Der Indexname muss die Namenskonvention für die dBASE Index übereinstimmen. dBASE III erfordert, dass jeder Index in einer separaten Datei, die jeweils einer NDX-Erweiterungs. In dBASE IV werden Indizes als Tag-Namen erstellt, die in einer einzigen MDX-Datei gespeichert werden. Die MDX-Datei hat den gleichen Basisnamen wie die Datenbankdatei (z. B. die Emp.mdx die Indexdatei für die Datenbank Emp.dbf ist).  
  
-   dBASE definiert einen eindeutigen Index als, in denen nur ein Datensatz aus einem Satz mit zwei identische Schlüsselwerte, die dem Index hinzugefügt wird.
