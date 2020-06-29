---
title: Festlegen der Eigenschaften einer Datenflusskomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], properties
ms.assetid: 73000ef6-52a2-4dec-8320-0e79acf0c2c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d4ac77a3c2a67b1bd0c0363cbe7fcf4588ca8f8e
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437687"
---
# <a name="set-the-properties-of-a-data-flow-component"></a>Festlegen der Eigenschaften einer Datenflusskomponente
  Die Eigenschaften von Datenflusskomponenten, z. B. Quellen, Ziele und Transformationen, können Sie mithilfe eine der folgenden Funktionen festlegen:  
  
-   Die von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bereitgestellten Komponenten-Editoren. Diese Editoren schließen nur die benutzerdefinierten Eigenschaften jeder Datenflusskomponente ein.  
  
-   Im Fenster **Eigenschaften** werden die benutzerdefinierten Eigenschaften auf Komponentenebene jedes Elements sowie die allen Datenflusselementen gemeinsamen Eigenschaften aufgelistet.  
  
-   Das Dialogfeld **Erweiterter Editor** ermöglicht den Zugriff auf benutzerdefinierte Eigenschaften für jede Komponente. Das Dialogfeld **Erweiterter Editor** ermöglicht außerdem den Zugriff auf benutzerdefinierte Eigenschaften für die einzelnen Komponenten sowie auf die für alle Datenflusskomponenten gemeinsamen Eigenschaften, die Eigenschaften von Eingaben, Ausgaben, Fehlerausgaben, Spalten und externen Spalten.  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-a-component-editor"></a>So legen Sie die Eigenschaften einer Datenflusskomponente mithilfe eines Komponenten-Editors fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** , und doppelklicken Sie anschließend auf den Datenflusstask, der den Datenfluss mit der Komponente enthält, deren Eigenschaften Sie anzeigen und ändern möchten.  
  
4.  Doppelklicken Sie auf die Datenflusskomponente.  
  
5.  Zeigen Sie im Komponenten-Editor die Eigenschaftswerte an, oder ändern Sie diese, und schließen Sie dann den Editor.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern**, um das aktualisierte Paket zu speichern.  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-properties-window"></a>So legen Sie die Eigenschaften einer Datenflusskomponente mithilfe des Eigenschaftenfensters fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** , und doppelklicken Sie anschließend auf den Datenflusstask, der die Komponente enthält, deren Eigenschaften Sie anzeigen und ändern möchten.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Datenflusskomponente, und klicken Sie anschließend auf **Eigenschaften**.  
  
5.  Zeigen Sie die Eigenschaftswerte an, oder ändern Sie diese, und schließen Sie dann das Fenster **Eigenschaften** .  
  
    > [!NOTE]  
    >  Viele Eigenschaften sind schreibgeschützt und können nicht geändert werden.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern**, um das aktualisierte Paket zu speichern.  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-advanced-editor"></a>So legen Sie die Eigenschaften einer Datenflusskomponente mithilfe des erweiterten Editors fest  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** , und doppelklicken Sie anschließend auf den Datenflusstask, der die Komponente enthält, die Sie anzeigen oder ändern möchten.  
  
4.  Klicken Sie im Datenfluss-Designer mit der rechten Maustaste auf die Datenflusskomponente, und klicken Sie anschließend auf **Erweiterten Editor anzeigen**.  
  
    > [!NOTE]  
    >  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kann **Erweiterter Editor**nicht für Datenflusskomponenten verwendet werden, die mehrere Eingaben unterstützen.  
  
5.  Führen Sie im Dialogfeld **Erweiterter Editor** einen beliebigen der folgenden Schritte aus:  
  
    -   Klicken Sie auf die Registerkarte **Verbindungs-Manager** , um die von der Komponente verwendete Verbindung anzuzeigen und anzugeben.  
  
        > [!NOTE]  
        >  Die Registerkarte **Verbindungs-Manager** ist nur für Datenflusskomponenten verfügbar, die Verbindungs-Manager zum Herstellen einer Verbindung mit Datenquellen wie z.B. Dateien und Datenbanken verwenden.  
  
    -   Klicken Sie auf die Registerkarte **Komponenteneigenschaften** , um die Eigenschaften auf Komponentenebene anzuzeigen und zu ändern.  
  
    -   Klicken Sie auf die Registerkarte **Spaltenzuordnungen** , um Zuordnungen zwischen externen Spalten und der verfügbaren Ausgabe anzuzeigen und zu ändern.  
  
        > [!NOTE]  
        >  Die Registerkarte **Spaltenzuordnungen** ist nur verfügbar, wenn Sie Quellen oder Ziele anzeigen oder bearbeiten.  
  
    -   Klicken Sie auf die Registerkarte **Eingabespalten** , um eine Liste der verfügbaren Eingabespalten anzuzeigen und die Namen von Ausgabespalten zu aktualisieren.  
  
        > [!NOTE]  
        >  Die Registerkarte Eingabespalten ist nur verfügbar, wenn Sie mit Transformationen oder Zielen arbeiten. Weitere Informationen finden Sie unter [Integration Services Transformations](transformations/integration-services-transformations.md).  
  
    -   Klicken Sie auf die Registerkarte **Eingabe- und Ausgabeeigenschaften** , um die Eigenschaften von Eingaben, Ausgaben und Fehlerausgaben sowie die Eigenschaften der enthaltenen Spalten anzuzeigen und zu ändern.  
  
        > [!NOTE]  
        >  Quellen weisen keine Eingaben auf. Ziele haben keine Ausgaben, mit Ausnahme einer optionalen Fehlerausgabe.  
  
6.  Zeigen Sie die Eigenschaftswerte an, oder ändern Sie diese.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern**, um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Integration Services-Transformationen](transformations/integration-services-transformations.md)  
  
  
