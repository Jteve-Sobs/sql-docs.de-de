---
title: Ersetzen einer Tabelle oder einer benannten Abfrage in einer Datenquellensicht (Analysis Services) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a171eafc35446f588d64c74457792912dcebe75a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641118"
---
# <a name="replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services"></a>Ersetzen einer Tabelle oder einer benannten Abfrage in einer Datenquellensicht (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Im Datenquellensicht-Designer können Sie eine Tabelle, eine Sicht oder eine benannte Abfrage in einer Datenquellensicht durch eine andere Tabelle oder Sicht aus derselben oder einer anderen Datenquelle bzw. durch eine benannte Abfrage, die in der Datenquellensicht definiert wurde, ersetzen. Beim Ersetzen einer Tabelle bleiben die Verweise aller anderen Objekte einer Datenbank oder eines Projekts von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf diese Tabelle erhalten, da die Objekt-ID der Tabelle in der Datenquellensicht nicht geändert wird. Alle Beziehungen, die weiterhin relevant sind (basierend auf der Übereinstimmung des Namens und des Spaltentyps), werden beibehalten. Wenn Sie eine Tabelle löschen und anschließend eine Tabelle hinzufügen, gehen im Gegensatz dazu Verweise und Beziehungen verloren und müssen neu erstellt werden.  
  
 Zum Ersetzen einer Tabelle durch eine andere Tabelle muss eine aktive Verbindung zur Datenquelle im Datenquellensicht-Designer im Projektmodus vorhanden sein.  
  
 Am häufigsten wird eine Tabelle in der Datenquellensicht durch eine andere Tabelle der Datenquelle ersetzt. Allerdings können Sie auch eine benannte Abfrage durch eine Tabelle ersetzen. Sie haben beispielsweise zuvor eine Tabelle durch eine benannte Abfrage ersetzt, und Sie möchten jetzt die Tabelle wiederherstellen.  
  
> [!IMPORTANT]  
>  Befolgen Sie beim Umbenennen einer Tabelle in einer Datenquelle die Schritte zum Ersetzen einer Tabelle, und geben Sie die umbenannte Tabelle als Quelle für die entsprechende Tabelle in der Datenquellensicht an, bevor Sie eine Datenquellensicht aktualisieren. Nach dem Ersetzen und Umbenennen werden die Tabelle sowie die Verweise und Beziehungen der Tabelle in der Datenquellensicht beibehalten. Andernfalls wird beim Aktualisieren der Datenquellensicht eine umbenannte Tabelle in der Datenquelle als gelöscht interpretiert. Weitere Informationen finden Sie unter [Aktualisieren des Schemas in einer Datenquellensicht &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/refresh-the-schema-in-a-data-source-view-analysis-services.md).  
  
##  <a name="bkmk_nq"></a> Ersetzen einer Tabelle durch eine benannte Abfrage  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das Projekt, oder stellen Sie eine Verbindung mit der Datenbank her, das bzw. die die Datenquellensicht enthält, in der Sie eine Tabelle oder benannte Abfrage ersetzen möchten.  
  
2.  Erweitern Sie im Projektmappen-Explorer den Ordner **Datenquellensichten** , und doppelklicken Sie anschließend auf die Datenquellensicht.  
  
3.  Öffnen Sie das Dialogfeld **Benannte Abfrage erstellen** . Klicken Sie im Bereich **Tabellen** oder **Diagramm** mit der rechten Maustaste auf die Tabelle, die Sie ersetzen möchten, zeigen Sie auf **Tabelle ersetzen** , und klicken Sie dann auf **Durch neue benannte Abfrage**.  
  
4.  Definieren Sie im Dialogfeld **Benannte Abfrage erstellen** die benannte Abfrage, und klicken Sie dann auf **OK**.  
  
5.  Speichern Sie die geänderte Datenquellensicht.  
  
## <a name="replace-a-table-or-named-query-with-a-table"></a>Ersetzen einer Tabelle oder benannten Abfrage durch eine Tabelle  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das Projekt, oder stellen Sie eine Verbindung mit der Datenbank her, das bzw. die die Datenquellensicht enthält, in der Sie eine Tabelle oder benannte Abfrage ersetzen möchten.  
  
2.  Erweitern Sie im Projektmappen-Explorer den Ordner **Datenquellensichten** , und doppelklicken Sie anschließend auf die Datenquellensicht.  
  
3.  Öffnen Sie das Dialogfeld **Tabelle durch eine andere Tabelle ersetzen** . Klicken Sie im Bereich **Tabellen** oder **Diagramm** mit der rechten Maustaste auf die Tabelle oder benannte Abfrage, die Sie ersetzen möchten, zeigen Sie auf **Tabelle ersetzen** , und klicken Sie dann auf **Durch andere Tabelle**.  
  
4.  Führen Sie im Dialogfeld **Tabelle durch eine andere Tabelle ersetzen** folgende Aktionen aus:  
  
    1.  Wählen Sie im Dropdown-Listenfeld **Datenquelle** die gewünschte Datenquelle aus.  
  
    2.  Wählen Sie die Tabelle aus, durch die Sie die Tabelle oder benannte Abfrage ersetzen möchten.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Speichern Sie die geänderte Datenquellensicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellsichten in mehrdimensionalen Modellen](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
