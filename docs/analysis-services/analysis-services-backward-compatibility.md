---
title: Abwärtskompatibilität der SQL Server 2016 Analysis Services | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ab4f304d865992a3269b4ee83c9e25f61069e8c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210261"
---
# <a name="analysis-services-backward-compatibility-sql-server-2016"></a>Analysis Services-Abwärtskompatibilität (SQL Server 2016)
[!INCLUDE[ssas-appliesto-sql2016](../includes/ssas-appliesto-sql2016.md)]

In diesem Artikel werden Änderungen an der Verfügbarkeit von Features und verhaltensänderungen zwischen der aktuellen Version und die vorherige Version beschrieben.

## <a name="deprecated-features"></a>Veraltete Features
Ein *veraltete Funktion* werden in einer zukünftigen Version wird aus dem Produkt eingestellt, aber ist immer noch unterstützt und in der aktuellen Version aus, um Abwärtskompatibilität enthalten. Es wird empfohlen, dass Sie dieses als veraltet markierte Funktionen in neue und vorhandene Projekte auf um Kompatibilität mit zukünftigen Versionen zu gewährleisten.
  
Die folgenden Features sind in dieser Version als veraltet markiert:
  
|||  
|-|-|  
|**Im Modus/Kategorie**|**Funktion**|  
|Multidimensional|Remotepartitionen|  
|Multidimensional|Remoteverknüpfte Measuregruppen|  
|Multidimensional|Dimensionales Rückschreiben|  
|Multidimensional|Verknüpfte Dimensionen|   
|Multidimensional|SQL Server-Tabellenbenachrichtigungen für proaktives Zwischenspeichern.  <br />Der Ersatz erfolgt durch die Verwendung eines Abrufs für proaktives Zwischenspeichern. <br />Weitere Informationen finden Sie unter [Proaktives Zwischenspeichern &#40;Dimensionen&#41;](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md) und [Proaktives Zwischenspeichern &#40;Partitionen&#41;](../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).|  
|Multidimensional|Sitzungscubes. Es gibt keinen Ersatz.|  
|Multidimensional|Lokale Cubes Es gibt keinen Ersatz.|  
|Tabellarisch|Kompatibilitätsgrade für die Tabellenmodelle 1100 und 1103 werden in einer zukünftigen Version nicht unterstützt. Der Austausch ist, legen Sie Modelle mit Kompatibilitätsgrad 1200 oder höher, Modelldefinitionen zu tabellarischen Metadaten konvertiert. Weitere Informationen finden Sie unter [Kompatibilitätsgrad für tabellarische Modelle in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).|  
|Tools|SQL Server Profiler für die Ablaufverfolgungssammlung<br /><br /> Der Ersatz verwendet den in SQL Server Management Studio eingebetteten Profiler für erweiterte Ereignisse.  <br /> Weitere Informationen finden Sie unter [Überwachen von Analysis Services mit den erweiterten Ereignissen von SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Tools|Server Profiler für die Ablaufverfolgungswiedergabe <br />Ersatz. Es gibt keinen Ersatz.|  
|Verwaltungsobjekte für die Ablaufverfolgung und Ablaufverfolgungs-APIs|Microsoft.AnalysisServices.Trace-Objekte (enthält die APIs für Analysis Services Ablauf-und Wiedergabeobjekte). Der Ersatz ist mehrteilig:<br /><br /> -Ablaufverfolgungskonfiguration: Microsoft.SqlServer.Management.XEvent<br />-Ablaufverfolgungslesevorgänge: Microsoft.SqlServer.XEvent.Linq<br />-Ablaufverfolgungswiedergabe: None|  
  
> [!NOTE]  
>  Zuvor als veraltet markierte Ankündigungen von Funktionen aus [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] bleiben wirksam. Da der Code, der diese Funktionen unterstützt, noch nicht aus dem Produkt-entfernt wurde, sind viele dieser Funktionen in dieser Version weiterhin vorhanden. Bei der zuvor als veraltet markierte Funktionen möglicherweise zugegriffen werden kann, diese weiterhin gelten als veraltet markiert und ist möglicherweise physisch aus dem Produkt zu einem beliebigen Zeitpunkt entfernt werden.  

## <a name="discontinued-features"></a>Nicht mehr unterstützte Funktionen
Ein *nicht mehr unterstützte Funktion* wurde in einer früheren Version als veraltet markiert. Sie können weiterhin in der aktuellen Version enthalten sein, aber es wird nicht mehr unterstützt. Möglicherweise werden nicht mehr unterstützte Funktionen entfernt vollständig in einer zukünftigen Version, oder aktualisieren.

Die folgenden Features wurden in einer früheren Version als veraltet markiert und werden in dieser Version nicht mehr unterstützt.

|||  
|-|-|  
|**Funktion**|**Alternative oder Problemumgehung**|  
|[CalculationPassValue &#40;MDX&#41;](../mdx/calculationpassvalue-mdx.md)|Keine Diese Funktion wurde in SQL Server 2005 als veraltet markiert.|  
|[CalculationCurrentPass &#40;MDX&#41;](../mdx/calculationcurrentpass-mdx.md)|Keine Diese Funktion wurde in SQL Server 2005 als veraltet markiert.|  
|Hinweis NON_EMPTY_BEHAVIOR für den Abfrageoptimierer|Keine Diese Funktion wurde in SQL Server 2008 als veraltet markiert.|  
|COM-Assemblys|Keine Diese Funktion wurde in SQL Server 2008 als veraltet markiert.|  
|Systeminterne Zelleneigenschaft CELL_EVALUATION_LIST|Keine Diese Funktion wurde in SQL Server 2005 als veraltet markiert.|  
  
> [!NOTE]  
>  Zuvor als veraltet markierte Ankündigungen von Funktionen aus [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] bleiben wirksam. Da der Code, der diese Funktionen unterstützt, noch nicht aus dem Produkt-entfernt wurde, sind viele dieser Funktionen in dieser Version weiterhin vorhanden. Bei der zuvor als veraltet markierte Funktionen möglicherweise zugegriffen werden kann, diese weiterhin gelten als veraltet markiert und ist möglicherweise physisch aus dem Produkt zu einem beliebigen Zeitpunkt entfernt werden.  

## <a name="breaking-changes"></a>Wichtige Änderungen
Eine *wichtige Änderung* bewirkt, dass ein Datenmodell, Anwendungscode oder Skript nach dem Aktualisieren des Modells oder Servers nicht mehr funktioniert.
  
### <a name="net-40-version-upgrade"></a>.NET 4.0-Versionsupgrade  
 Clientbibliotheken von Analysis Services Management Objects (AMO), ADOMD.NET und Tabular Object Model (TOM) als Ziel jetzt die .NET 4.0-Laufzeit. Dies kann für Anwendungen, die auf .NET 3.5 ausgerichtet sind, eine wichtige Änderung sein. Anwendungen, die neuere Versionen dieser Assemblys verwenden, müssen jetzt auf .NET 4.0 oder höher ausgerichtet sein.  
  
### <a name="amo-version-upgrade"></a>AMO-Versionsupgrade  
 Diese Version ist ein Versionsupgrade für [Analysis Services Management Objects &#40;AMO&#41; ](https://msdn.microsoft.com/library/mt436122.aspx) und ist unter bestimmten Umständen eine wichtige Änderung.  Vorhandener Code und Skripts, die AMO aufrufen, werden bei einem Upgrade von einer vorherigen Version wie bisher ausgeführt. Allerdings bei Bedarf *recompile* Ihrer Anwendung, und Sie eine SQL Server 2016 Analysis Services-Instanz Anzielen, müssen Sie den folgenden Namespace ein, um Ihr Code oder Skript betriebsbereit zu machen:  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 Der Namespace [Microsoft.AnalysisServices.Core](https://msdn.microsoft.com/library/microsoft.analysisservices.core.aspx) ist jetzt jedes Mal erforderlich, wenn Sie die Microsoft.AnalysisServices-Assembly in Ihrem Code referenzieren. Objekte, die zuvor nur im **Microsoft.AnalysisServices** -Namespace enthalten waren, werden in dieser Version in den Core-Namespace verschoben, wenn das Objekt in tabellarischen und mehrdimensionalen Szenarien auf die gleiche Weise verwendet wird.  Beispielsweise werden serverorientierte APIs zum Core-Namespace verschoben.  
  
 Obgleich jetzt mehrere Namespaces vorhanden sind, existieren alle in derselben Assembly (Microsoft.AnalysisServices.dll).  
  
### <a name="xevent-discover-changes"></a>Änderungen an XEvent DISCOVER  
 Um besser zu XEvent DISCOVER-streaming in SSMS für SQL Server 2016 Analysis Services unterstützen `DISCOVER_XEVENT_TRACE_DEFINITION` wird durch folgenden XEvent-ablaufverfolgungen ersetzt:  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  

## <a name="behavior-changes"></a>Verhaltensänderungen
*Verhaltensänderungen* beeinflussen die Funktion und Interaktion von Funktionen in der aktuellen Version im Vergleich zu früheren Versionen von SQL Server.
  
Beispiele für eine Verhaltensänderung beinhalten Überarbeitungen von Standardwerten, die für das Abschließen einer Upgrade- oder Wiederherstellungsfunktionalität benötigte manuelle Konfiguration oder eine neue Implementierung einer vorhandenen Funktion.
  
Funktionsverhalten, die in diesem Release geändert werden, die jedoch kein vorhandenes Modell oder Code nach dem Upgrade unterbrechen, sind hier aufgelistet.
  
### <a name="analysis-services-in-sharepoint-mode"></a>Analysis Services im SharePoint-Modus
 Die Ausführung des Assistenten für die PowerPivot-Konfiguration ist nach der Installation nicht mehr erforderlich. Dies gilt für alle unterstützten Versionen von SharePoint, die Modelle aus der aktuellen SQL Server 2016 Analysis Services zu laden.
  
### <a name="directquery-mode-for-tabular-models"></a>DirectQuery-Modus für tabellarische Modelle
 *DirectQuery* ist ein Datenzugriffsmodus für tabellarische Modelle, in dem die Abfrageausführung in einer relationalen Back-End-Datenbank stattfindet, wobei ein Resultset in Echtzeit abgerufen wird. Er wird häufig für sehr große Datasets verwendet, die nicht in den Arbeitsspeicher passen. Er wird zudem verwendet, wenn Daten flüchtig sind und Sie möchten, dass die aktuellsten Daten in Abfragen an ein tabellarisches Modell zurückgegeben werden.
  
 DirectQuery war als Datenzugriffsmodus in den letzten Releases vorhanden. In SQL Server 2016 Analysis Services wurde die Implementierung geringfügig überarbeitet, vorausgesetzt, dass das tabellarische Modell mit Kompatibilitätsgrad 1200 oder höher ist. DirectQuery hat weniger Einschränkungen als bisher. Es verfügt außerdem über verschiedene Datenbankeigenschaften.
  
 Wenn Sie DirectQuery in einem vorhandenen tabellarischen Modell verwenden, können Sie für das Modell dessen aktuellen Kompatibilitätsgrad von 1100 oder 1103 erhalten und DirectQuery weiterhin verwenden, da es für diese Grade implementiert ist. Alternativ können Sie auf 1200 oder höher, profitieren von erfolgten Verbesserungen von DirectQuery aktualisieren.
  
 Es gibt kein direktes Upgrade eines DirectQuery-Modells auf, da die Einstellungen der älteren Kompatibilitätsgrade keine genaue Entsprechungen in den neueren 1200 und höher Kompatibilitätsgraden vorliegen. Wenn Sie ein vorhandenes tabellarisches Modell, die im DirectQuery-Modus ausgeführt wird verfügen, Sie sollten das Modell in SQL Server Data Tools öffnen, DirectQuery deaktivieren, legen Sie die **Kompatibilitätsgrad** -Eigenschaft auf 1200 oder höher, und anschließend erneut konfigurieren DirectQuery Eigenschaften. Finden Sie unter [DirectQuery-Modus](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md) Details.


## <a name="see-also"></a>Siehe auch
[Analysis Services-Abwärtskompatibilität (SQL Server 2017)](analysis-services-backward-compatibility-sql2017.md)
