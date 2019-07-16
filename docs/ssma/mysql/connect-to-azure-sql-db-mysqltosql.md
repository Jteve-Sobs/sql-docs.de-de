---
title: Verbinden mit Azure SQL-Datenbank (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 81623d27-25af-444f-9779-1edb8c6fb470
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 12da1aa42f468b92e1833410e635183aabf3a384
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103246"
---
# <a name="connect-to-azure-sql-db-mysqltosql"></a>Herstellen einer Verbindung mit Azure SQL-DB (MySQLToSQL)
Verwenden Sie die Connect SQL Azure-Dialogfeld zur Verbindung mit der SQL Azure-Datenbank, die Sie migrieren möchten.  
  
Zum Zugriff auf dieses Dialogfeld, in der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit SQL Azure**. Wenn Sie zuvor eine Verbindung hergestellt haben, wird der Befehl ist **Wiederherstellen der Verbindung zu SQL Azure.**  
  
## <a name="options"></a>Optionen  
**Servername**  
  
Wählen Sie aus, oder geben Sie den Servernamen für die Verbindung mit SQL Azure.  
  
**Datenbank**  
  
Wählen Sie aus, geben Sie ein oder **Durchsuchen** der Name der Datenbank.  
  
> [!IMPORTANT]  
> SSMA für MySQL unterstützt keine Verbindung mit der master-Datenbank in SQL Azure.  
  
**Benutzername**  
  
Geben Sie den Benutzernamen, mit der SSMA mit der SQL Azure-Datenbank herstellen  
  
**Kennwort**  
  
Geben Sie das Kennwort für den Benutzernamen ein.  
  
**Encrypt**  
  
SSMA empfiehlt verschlüsselte Verbindung für SQL Azure.  
  
## <a name="create-azure-database"></a>Erstellen von Azure-Datenbank  
Wenn keine Datenbanken im SQL Azure-Konto vorhanden sind, können Sie die erste Datenbank erstellen.  
  
Führen Sie die folgenden Schritte aus, um eine neue Datenbank zum ersten Mal erstellen,  
  
1.  Klicken Sie auf die Schaltfläche zum Durchsuchen, die in Verbindung zu SQL Azure (Dialogfeld) vorhanden ist  
  
2.  Wenn keine Datenbanken vorhanden sind, werden die folgenden zwei Menüelemente angezeigt.  
  
    1.  **(keine Datenbanken gefunden.)**  die deaktiviert und ausgegraut, ständig  
  
    2.  **Erstellen Sie neue Datenbank** die ist nur aktiviert, wenn keine Datenbanken für SQL Azure-Konto vorhanden sind. Nach dem Klicken auf dieses Menüelement, für Azure-Datenbank erstellen (Dialogfeld) mit Datenbanknamen und Größe vorhanden ist.  
  
3.  Zum Zeitpunkt der Erstellung der Datenbank sind die folgenden beiden Parameter als Eingabe übergeben:  
  
    1.  **Datenbankname:** Geben Sie den Datenbanknamen ein.  
  
    2.  **Größe der Datenbank:** Wählen Sie die Größe der Datenbank, die in SQL Azure-Konto erstellen müssen.  
  
