---
title: Registrierungseinträge für Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0b9d101395a3276f92f3ccf49e36effc65420f7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093881"
---
# <a name="registry-entries-for-data-sources"></a>Registrierungseinträge für Datenquellen
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in das Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 Das Installationsprogramm-DLL verwaltet die Informationen in der Registrierung über jede Datenquelle. In Microsoft Windows NT/Windows 2000 und Microsoft Windows 95/98 werden diese Informationen im Unterschlüssel unter einem der folgenden zwei Schlüssel in der Registrierung gespeichert:  
  
 HKEY_LOCAL_MACHINE  
  
 SOFTWARE  
  
 ODBC  
  
 Odbc.ini  
  
 HKEY_CURRENT_USER  
  
 SOFTWARE  
  
 ODBC  
  
 Odbc.ini  
  
 Hängt von der Schlüssel verwendet wird, ob die Datenquelle ist eine *Systemdatenquelle,* steht für alle Benutzer oder eine *Benutzerdatenquelle,* steht nur für den aktuellen Benutzer. System-Datenquellen werden in der HKEY_LOCAL_MACHINE-Struktur gespeichert, und Benutzerdatenquellen werden in der HKEY_CURRENT_USER-Struktur gespeichert. System-Datenquellen und Benutzerdatenquellen sind in jeder anderen Hinsicht identisch.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Unterschlüssel für ODBC-Datenquellen](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Unterschlüssel für Datenquellenspezifikationen](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Standardunterschlüssel](../../../odbc/reference/install/default-subkey.md)  
  
-   [ODBC-Unterschlüssel](../../../odbc/reference/install/odbc-subkey.md)
