---
title: SQLDriverConnect (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6fd8f3be1213a91195cd74a8b723629e2c5833f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053890"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: Vollständig  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Eine Verbindung mit einer vorhandenen Datenquelle, die entweder als eine [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md) oder ein Verzeichnis von [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md). Die ODBC-Attribut Schlüsselwörter UID und PWD werden ignoriert. Die folgende Tabelle enthält die Schlüsselwörter unterstützt zusätzlich das Attribut.  
  
|ODBC-Schlüsselwort|Attributwert|  
|----------------------------|---------------------|  
|DSN||  
|UID|Der Visual FoxPro-ODBC-Treiber ignoriert, nicht jedoch einen Fehler.|  
|PWD|Der Visual FoxPro-ODBC-Treiber ignoriert, nicht jedoch einen Fehler.|  
|Treiber|Name und Speicherort der Visual FoxPro-ODBC-Treiber; implementiert die vom Treiber-Manager.|  
  
|Visual FoxPro-ODBC-Treiber-Attribut-Schlüsselwort|Attributwert|  
|-------------------------------------------------|---------------------|  
|BackgroundFetch|"Yes" oder "No"|  
|Sortieren|"Computer" oder andere Sortierreihenfolge. Eine Liste der unterstützten sortierenden Sequenzen, finden Sie unter [festgelegt COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Beschreibung||  
|Exclusive|"Yes" oder "No"|  
|SourceDB|Ein vollqualifizierter Pfad zu einem Verzeichnis mit NULL oder mehr [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md), oder der absolute Pfad und Dateiname für eine [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SourceType|"DBC" oder "DBF"|  
|Version||  
  
 Wenn der Name der Datenquelle nicht angegeben ist, wird der Treiber-Manager fordert den Benutzer für die Informationen (entsprechend der Einstellung von der *fDriverCompletion* Argument) und dann fortgesetzt wird. Wenn Sie weitere Informationen erforderlich ist, zeigt der Visual FoxPro-ODBC-Treiber eingabeaufforderungs-Dialogfeld.  
  
 Weitere Informationen finden Sie unter [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) in die *ODBC Programmer's Reference*.
