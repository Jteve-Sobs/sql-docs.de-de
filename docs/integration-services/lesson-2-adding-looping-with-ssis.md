---
title: 'Lektion 2: Hinzufügen von Schleifen mit SSIS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed4b198ab8f0582f3e01cfaca957af4f72e343e2
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51641217"
---
# <a name="lesson-2-adding-looping-with-ssis"></a>Lesson 2: Adding Looping with SSIS
In Rahmen von [Lesson 1: Create a Project and Basic Package with SSIS (Lektion 1: Erstellen eines Projekts und Basispakets mit SSIS)](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md) haben Sie ein Paket erstellt, mit dem Daten aus einer einzelnen Flatfilequelle zunächst extrahiert, anschließend mithilfe der Suchtransformationen transformiert und schließlich in eine Kopie der Faktentabelle **FactCurrencyRate** der **AdventureWorksDW2012** -Beispieldatenbank geladen wurden.  
  
Das Verwenden einer einzelnen flachen Datei ist allerdings bei einem ETL-Vorgang (Extract, Transform and Load, Extrahieren, Transformieren und Laden) selten. Von einem typischen ETL-Vorgang würden Daten aus mehreren flachen Dateiquellen extrahiert. Das Extrahieren von Daten aus mehreren Quellen erfordert eine iterative (wiederholende) Ablaufsteuerung. Mit [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ist es auf einfache Weise möglich, Iterationen oder Schleifen zu Paketen hinzuzufügen.  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] bietet zwei Containertypen für Schleifenvorgänge durch Pakete an: den Foreach- und den For-Schleifencontainer. Der Foreach-Schleifencontainer verwendet einen Enumerator für die Ausführung der Schleife, während der For-Schleifencontainer normalerweise einen Variablenausdruck verwendet. In dieser Lektion wird der Foreach-Schleifencontainer verwendet.  
  
Durch den Foreach-Schleifencontainer wird es für ein Paket möglich, die Ablaufsteuerung für jedes Element eines angegebenen Enumerators zu wiederholen. Mithilfe des Foreach-Schleifencontainer können Sie die folgenden Elemente aufzählen:  
  
-   ADO-Recordsetzeilen  
  
-   ADO.NET-Schemainformationen  
  
-   Datei- und Verzeichnisstrukturen  
  
-   System-, Paket- und Benutzervariablen  
  
-   Aufzählbare Objekte in einer Variablen  
  
-   Elemente in einer Auflistung  
  
-   Knoten in einem XPath-Ausdruck (XML Path Language)  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO)  
  
In dieser Lektion ändern Sie das in Lektion 1 erstellte einfache ETL-Paket, um die Vorteile des Foreach-Schleifencontainers nutzen zu können. Sie legen auch benutzerdefinierte Paketvariablen fest, um die Iteration durch alle flachen Dateien im Ordner für das Lernprogrammpaket zu ermöglichen. Wenn Sie die vorherige Lektion nicht abgeschlossen haben, können Sie auch das abgeschlossene Paket aus Lektion 1 kopieren, das im Lernprogramm enthalten ist.  
  
In dieser Lektion ändern Sie nur die Ablaufsteuerung, nicht den Datenfluss.  
  
> [!IMPORTANT]  
> Dieses Lernprogramm erfordert die **AdventureWorksDW2012** -Beispieldatenbank. Weitere Informationen zum Installieren und Bereitstellen von **AdventureWorksDW2012**finden Sie unter [Reporting Services Produktbeispiel-Projekt auf CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Schritt 1: Kopieren des Pakets aus Lektion 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [Schritt 2: Hinzufügen und Konfigurieren des Foreach-Schleifencontainers](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [Schritt 3: Ändern des Flatfile-Verbindungs-Managers](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [Schritt 4: Testen des Tutorialpakets aus Lektion 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Lektion beginnen  
[Schritt 1: Kopieren des Pakets aus Lektion 1](../integration-services/lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[For-Schleifencontainer](../integration-services/control-flow/for-loop-container.md)  
  
  
  
