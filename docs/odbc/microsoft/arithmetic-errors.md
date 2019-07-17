---
title: Arithmetische Fehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e0880e1746b4b65070fb28bf8d83aadec301aa4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138178"
---
# <a name="arithmetic-errors"></a>Arithmetische Fehler
Der ODBC-Treiber die WHERE-Klausel einer SELECT-Anweisung ausgewertet wird, wie jede Zeile abgerufen. Wenn eine Zeile einen Wert enthält, der einen arithmetischen Fehler wie z. B. aufgrund einer Division durch Null "oder" numeric "Überlauf", bewirkt, dass der Treiber gibt alle Zeilen zurück, gibt jedoch Fehler für Spalten mit arithmetischen Fehlern. Beim Einfügen oder aktualisieren, beendet jedoch der ODBC-Treiber, einfügen oder Aktualisieren von Daten, wenn die erste arithmetische Fehler aufgetreten ist.
