---
title: Extrahieren von Daten mithilfe der ODBC-Quelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 10f25703-49a2-4d45-abab-6b4da2a57ba5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f8ecb517174c8cd8189ad2f7382c774df3545620
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864947"
---
# <a name="extract-data-by-using-the-odbc-source"></a>Extrahieren von Daten mithilfe der ODBC-Quelle
  In diesem Verfahren wird beschrieben, wie Sie Daten mithilfe einer ODBC-Quelle extrahieren. Um eine ODBC-Quelle hinzuzufügen und zu konfigurieren, muss das Paket bereits mindestens einen Datenflusstask enthalten.  
  
### <a name="to-extract-data-using-an-odbc-source"></a>So extrahieren Sie Daten mithilfe einer ODBC-Quelle  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]das gewünschte [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] -Paket.  
  
2.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie die ODBC-Quelle dann aus der **Toolbox**auf die Entwurfsoberfläche.  
  
3.  Doppelklicken Sie auf die ODBC-Quelle.  
  
4.  Wählen Sie im Dialogfeld **Quellen-Editor für ODBC** auf der Seite **Verbindungs-Manager** einen vorhandenen ODBC-Verbindungs-Manager aus, oder klicken Sie auf **Neu** , um einen neuen Verbindungs-Manager zu erstellen.  
  
5.  Wählen Sie die Datenzugriffsmethode aus.  
  
    -   **Tabellenname**: Wählen Sie in der Datenbank eine Tabelle oder Sicht aus, oder geben Sie einen regulären Ausdruck ein, um die Tabelle zu identifizieren, mit der der ODBC-Verbindungs-Manager eine Verbindung herstellt.  
  
         Diese Liste enthält nur die ersten 1000 Tabellen. Wenn die Datenbank mehr als 1000 Tabellen enthält, können Sie den Anfang eines Tabellennamens eingeben oder das Platzhalterzeichen (*) verwenden, um einen beliebigen Teil des Namens einzugeben und die gewünschten Tabellen anzuzeigen.  
  
    -   **SQL-Befehl**: Geben Sie einen SQL-Befehl ein, oder klicken Sie auf **Durchsuchen**, um die SQL-Abfrage aus einer Textdatei zu laden.  
  
6.  Sie können auf **Vorschau** klicken, um bis zu 200 Datenzeilen anzuzeigen, die von der ODBC-Quelle extrahiert werden.  
  
7.  Um die Zuordnung zwischen externen Spalten und Ausgabespalten zu aktualisieren, klicken Sie auf **Spalten** und wählen in der Liste **Externe Spalte** verschiedene Spalten aus.  
  
8.  Aktualisieren Sie bei Bedarf die Namen von Ausgabespalten, indem Sie Werte in der Liste **Ausgabespalte** bearbeiten.  
  
9. Klicken Sie auf **Fehlerausgabe**, um die Fehlerausgabe zu konfigurieren.  
  
10. Klicken Sie auf **OK**.  
  
11. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellen-Editor für ODBC &#40;Seite Verbindungs-Manager&#41;](../odbc-source-editor-connection-manager-page.md)   
 [Quellen-Editor für ODBC &#40;Seite Spalten&#41;](../odbc-source-editor-columns-page.md)   
 [Quellen-Editor für ODBC &#40;Seite „Fehlerausgabe“&#41;](../odbc-source-editor-error-output-page.md)  
  
  
