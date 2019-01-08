---
title: Analysis Services tabellarisch modellprogrammierung für Kompatibilitätsgrad 1050-1103 | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe2ce43ffb5d2c5be0afb39931f231d2f0d24e14
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53071767"
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>Programmieren von tabellarischen Modellen für Kompatibilitätsgrad 1050 bis 1103
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Tabellarische Modelle verwenden relationale Konstrukte, um die von Analyse- und Berichtsanwendungen verwendeten Analysis Services-Daten zu modellieren. Diese Modelle werden auf einer Analysis Service-Instanz ausgeführt, die für den Tabellenmodus konfiguriert ist, und zwar mithilfe einer Engine für Datenanalyse im Arbeitsspeicher für einen Speicher und schnelle Tabellenscans, mit denen Daten nach Bedarf aggregiert und berechnet werden.  
  
 Wenn die Anforderungen der benutzerdefinierten BI-Lösung am besten von einer tabellarischen Modelldatenbank erfüllt werden, können Sie eine beliebige der Analysis Services-Clientbibliotheken und -Programmierschnittstellen verwenden, um die Anwendung auf einer Analysis Services-Instanz in tabellarische Modelle zu integrieren. Sie können entweder eingebettete MDX oder DAX im Code verwenden, um tabellarische Modelldaten abzufragen und zu berechnen.  
  
 Für tabellarische Modelle, die in früheren Versionen von Analysis Services, in bestimmten Modelle mit Kompatibilitätsgrad 1050 bis 1103 erstellt, die Objekte, die Sie mit programmgesteuerten in AMO, ADOMD.NET, XMLA oder OLE DB arbeiten entsprechen im Wesentlichen für sowohl tabellarische und mehrdimensionale Lösungen. Insbesondere wird die Objekt-Metadaten definiert, die für mehrdimensionale Modelle auch für tabellarische Modelle Kompatibilitätsgrade 1050-1103 verwendet.  
  
 Ab SQL Server 2016 können tabellarische Modelle erstellt oder ein Upgrade auf den Kompatibilitätsgrad 1200 oder höher, der tabellarischen Metadaten zum Definieren des Modells verwendet werden. Auf dieser Ebene sind Metadaten und die Programmierbarkeit grundlegend. Finden Sie unter [Programmieren von tabellarischen Modellen für Kompatibilitätsgrad 1200 und höher](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md) und [Aktualisieren von Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) für Weitere Informationen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [CSDL-Anmerkungen für Business Intelligence &#40;CSDLBI&#41;](https://docs.microsoft.com/bi-reference/csdl/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [Grundlegendes zum tabellarischen Objektmodell mit Ebenen 1050 bis 1103](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [Technische Referenz für BI-Anmerkungen zu CSDL](https://docs.microsoft.com/bi-reference/csdl/technical-reference-for-bi-annotations-to-csdl)  
  

[IMDEmbeddedData-Schnittstelle](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  
