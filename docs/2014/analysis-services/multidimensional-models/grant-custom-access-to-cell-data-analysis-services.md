---
title: Erteilen von benutzerdefiniertem Zugriff auf Zellendaten (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.celldata.f1
helpviewer_keywords:
- user access rights [Analysis Services], cell data
- permissions [Analysis Services], cells
- read contingent permissions
- read permissions
- cells [Analysis Services]
- custom cell data access [Analysis Services]
ms.assetid: 3b13a4ae-f3df-4523-bd30-b3fdf71e95cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5db12886384089afe87ffb5fa659c34b09a9fe23
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074982"
---
# <a name="grant-custom-access-to-cell-data-analysis-services"></a>Erteilen von benutzerdefiniertem Zugriff auf Zellendaten (Analysis Services)
  Zellensicherheit wird verwendet, um den Zugriff auf Measuredaten innerhalb eines Cubes zuzulassen oder zu verweigern. Die folgende Abbildung zeigt eine Kombination zugelassener und verweigerter Measures in einer PivotTable, wenn ein Benutzer angemeldet ist, dessen Rolle nur den Zugriff auf bestimmte Measures erlaubt. In diesem Beispiel sind der **Betrag der Verkäufe des Wiederverkäufers** und die **Gesamtproduktkosten des Wiederverkäufers** die einzigen über diese Rolle verfügbaren Measures. Alle anderen Measures werden implizit abgelehnt (im unten stehenden Abschnitt "Zulassen des Zugriffs auf bestimmte Measures" sind die Schritte zu diesem Ergebnis beschrieben).  
  
 ![PivotTable mit zugelassenen und verweigerten Zellen](../media/ssas-permscellsallowed.png "Pivottable mit zugelassenen und verweigerten Zellen")  
  
 Zellenberechtigungen gelten für Daten innerhalb der Zelle, nicht für deren Metadaten. Sie sehen, dass die Zelle in den Ergebnissen einer Abfrage immer noch sichtbar ist und den Wert `#N/A` anstelle des tatsächlichen Zellenwerts anzeigt. Die `#N/A` -Wert in der Zelle angezeigt wird, es sei denn, die Clientanwendung den Wert übersetzt oder einen anderen Wert durch Festlegen der Secured Cell Value-Eigenschaft in der Verbindungszeichenfolge angegeben ist.  
  
 Um die Zelle ganz auszublenden, müssen Sie die Member-Dimensionen, Dimensionsattribute und dimensionsattributelementen beschränken –, die angezeigt werden. Weiter Informationen finden Sie unter [Erteilen eines benutzerdefinierten Zugriffs auf Dimensionsdaten &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md).  
  
 Als Administrator können Sie angeben, ob Rollenmitglieder über Leseberechtigungen, Berechtigungen für abhängiges Lesen oder Lese-/Schreibberechtigungen für Zellen innerhalb eines Cubes verfügen. Berechtigungen für eine Zelle zu vergeben, ist die geringste zulässige Sicherheitsstufe. Bevor Sie also Berechtigungen auf dieser Ebene anwenden, sollten Sie folgende Aspekte berücksichtigen:  
  
-   Im Rahmen der Sicherheit auf Zellenebene können keine Rechte erweitert werden, die auf einer höheren Ebene eingeschränkt wurden. Beispiel: Wenn durch eine Rolle der Zugriff auf Dimensionsdaten verweigert wird, kann der verweigerte Satz nicht durch Sicherheit auf Zellenebene überschrieben werden. Ein weiteres Beispiel: erwägen Sie eine Rolle mit `Read` -Berechtigung für einen Cube und **Lese-/Schreibzugriff** -Berechtigung für eine Zelle lautet die Berechtigung für die Zellendaten nicht **Lese-/Schreibzugriff**; sie werden `Read`.  
  
-   Benutzerdefinierte Berechtigungen müssen zwischen Dimensionselementen und Zellen innerhalb derselben Rolle häufig koordiniert werden. Angenommen, Sie möchten den Zugriff auf mehrere rabattbezogene Measures für verschiedene Kombinationen aus Wiederverkäufern verweigern. Wenn wir die **Wiederverkäufer** als Dimensionsdaten und den **Rabattbetrag** als Measure verstehen, müssten Berechtigungen innerhalb derselben Rolle sowohl für die Measure (unter Befolgen der Anweisungen in diesem Thema) als auch für die Dimensionselemente kombiniert werden. Weitere Informationen zum Festlegen von Dimensionsberechtigungen finden Sie unter [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) .  
  
 Sicherheit auf Zellenebene wird über MDX-Ausdrücke definiert. Da eine Zelle ein Tupel ist (d. h. ein Schnittpunkt zwischen möglicherweise mehreren Dimensionen und Measures), müssen spezifische Zellen mithilfe von MDX identifiziert werden.  
  
## <a name="allow-access-to-specific-measures"></a>Zulassen des Zugriffs auf bestimmte Measures  
 Sie können Zellensicherheit verwenden, um explizit anzugeben, welche Measures verfügbar sind. Nachdem Sie die Elemente, die zulässig sind, eindeutig identifiziert haben, sind alle weiteren Measures nicht mehr verfügbar. Dies stellt möglicherweise das einfachste Szenario für die Implementierung via MDX-Skript dar, wie folgende Schritte zeigen.  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Instanz her, wählen Sie eine Datenbank aus, öffnen Sie den Ordner **Rollen** , und klicken Sie anschließend auf eine Datenbankrolle (oder erstellen Sie eine neue Datenbankrolle). Die Mitgliedschaft sollte bereits angegeben worden sein, und die Rolle sollte `Read`-Zugriff auf den Cube haben. Weitere Informationen finden Sie unter [Erteilen von Cube- oder Modellberechtigungen &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) .  
  
2.  Überprüfen Sie unter **Zellendaten**die Cubeauswahl, um sich zu vergewissern, dass Sie den richtigen Cube ausgewählt haben. Wählen Sie anschließend **Leseberechtigungen aktivieren**aus.  
  
     Wenn Sie nur dieses Kontrollkästchen aktivieren, aber keinen MDX-Ausdruck angeben, hat dies die gleiche Wirkung, als wenn der Zugriff auf alle Zellen im Cube verweigert würde. Dies ist darauf zurückzuführen, dass der standardmäßig zulässige Satz eine leere Menge darstellt, wenn mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Teilmenge von Cubezellen aufgelöst wird.  
  
3.  Geben Sie den folgenden MDX-Ausdruck ein.  
  
    ```  
    (Measures.CurrentMember IS [Measures].[Reseller Sales Amount]) OR (Measures.CurrentMember IS [Measures].[Reseller Total Product Cost])  
    ```  
  
     Dieser Ausdruck gibt explizit an, welche Measures für die Benutzer sichtbar sind. Benutzern, die sich über diese Rolle verbinden, stehen keine anderen Measures zur Verfügung. Beachten Sie, dass [CurrentMember &#40;MDX&#41;](/sql/mdx/current-mdx) den Kontext festlegt und dass darauf das zulässige Measure folgt. Das Ergebnis dieses Ausdrucks: Wenn das aktuelle Element entweder den **Betrag der Verkäufe des Wiederverkäufers** oder die **Gesamtproduktkosten des Wiederverkäufers** enthält, wird der aktuelle Wert angezeigt. Andernfalls verweigern Sie den Zugriff. Der Ausdruck besteht aus mehreren Teilen, jedes davon wird in Klammern gesetzt. Der Operator `OR` wird verwendet, um mehrere Measures anzugeben.  
  
## <a name="deny-access-to-specific-measures"></a>Verweigern des Zugriffs auf bestimmte Measures  
 Der folgende MDX-Ausdruck, ebenfalls unter **Rolle erstellen**  |  **Zellendaten**  |  **Lesen des Cubeinhalts zulassen** angegeben, hat den gegenteiligen Effekt, sodass bestimmte Measures nicht verfügbar sind. In diesem Beispiel **Discount Amount** und **Discount Percentage** erfolgen nicht verfügbar, mit der `NOT` und `AND` Operatoren. Alle anderen Measures werden Benutzern, die sich über diese Rolle verbinden, angezeigt.  
  
```  
(NOT Measures.CurrentMember IS [Measures].[Discount Amount]) AND (NOT Measures.CurrentMember IS [Measures].[Discount Percentage])  
```  
  
 In Excel wird die Zellensicherheit in folgender Abbildung veranschaulicht:  
  
 ![Excel-Zellen nicht verfügbarer angezeigte Spalten](../media/ssas-permscellshidemeasure.png "Excel-Zellen nicht verfügbarer angezeigte Spalten")  
  
## <a name="set-read-permissions-on-calculated-measures"></a>Festlegen von Leseberechtigungen für berechnete Measures  
 Berechtigungen für eine berechnete Measure können unabhängig von den Teilen, aus denen sie besteht, festgelegt werden. Fahren Sie mit dem nächsten Abschnitt zu den Berechtigungen für abhängiges Lesen fort, wenn Sie Berechtigungen zwischen einer berechneten Measure und ihren abhängigen Measures koordinieren möchten.  
  
 Schauen Sie sich **Reseller Gross Profit** (Bruttoertrag des Wiederverkäufers) in AdventureWorks an, um zu verstehen, wie Leseberechtigungen für ein berechnetes Measure funktionieren. Sie wird von den Measures **Betrag der Verkäufe des Wiederverkäufers** und **Gesamtproduktkosten des Wiederverkäufers** abgeleitet. Solange eine Rolle über Leseberechtigungen für die **Reseller Gross Profit**-Zellen verfügt, ist dieses Measure sichtbar, auch wenn die Berechtigungen für die anderen Measures ausdrücklich verweigert werden. Kopieren Sie zu Demonstrationszwecken den folgenden MDX-Ausdruck nach **Rolle erstellen**  |  **Zellendaten**  |  **Lesen des Cubeinhalts zulassen**.  
  
```  
(NOT Measures.CurrentMember IS [Measures].[Reseller Sales Amount])  
AND (NOT Measures.CurrentMember IS [Measures].[Reseller Total Product Cost])  
```  
  
 Stellen Sie in Excel mit der aktuellen Rolle eine Verbindung zum Cube her, und wählen Sie alle drei Measures aus, um die Auswirkungen der Zellensicherheit anzuzeigen. Sie sehen, dass Measures des abgelehnten Satzes nicht verfügbar sind, während die berechnete Measure vom Benutzer angezeigt werden kann.  
  
 ![Excel-Tabelle mit verfügbar sind und nicht verfügbaren Zellen](../media/ssas-permscalculatedcells.png "Excel-Tabelle mit verfügbar sind und nicht verfügbaren Zellen")  
  
## <a name="set-read-contingent-permissions-on-calculated-measures"></a>Festlegen von Berechtigungen für abhängiges Lesen für berechnete Measures  
 Zellensicherheit bietet mit den Berechtigungen für abhängiges Lesen eine Alternative für das Festlegen von Berechtigungen für die Zellen, die zu einer Berechnung gehören. Schauen wir uns erneut das Beispiel **Reseller Gross Profit** an. Wenn Sie den gleichen MDX-Ausdruck wie im vorherigen Abschnitt eingeben, jetzt allerdings im zweiten Textbereich des Dialogfelds **Rolle erstellen**  |  **Zellendaten** (im Textbereich unter **Lesen des Zelleninhalts abhängig von der Zellensicherheit zulassen**), wird das Ergebnis in Excel angezeigt. Da **Reseller Gross Profit** vom **Betrag der Verkäufe des Wiederverkäufers** und von den **Gesamtproduktkosten des Wiederverkäufers** abhängig ist, kann auf den Bruttoertrag nun nicht mehr zugegriffen werden, weil seine Bestandteile nicht zugänglich sind.  
  
> [!NOTE]  
>  Was passiert, wenn Sie sowohl die Leseberechtigungen als auch die Berechtigungen für abhängiges Lesen für eine Zelle innerhalb derselben Rolle festlegen? Die Rolle stellt Leseberechtigungen für die Zelle bereit, keine Berechtigungen für abhängiges Lesen.  
  
 Erinnern wir uns, dass in den vorherigen Abschnitten allein durch Aktivieren des Kontrollkästchens **Berechtigungen für abhängiges Lesen aktivieren** , ohne Angabe eines MDX-Ausdrucks, der Zugriff auf alle Zellen im Cube verweigert wird. Dies ist darauf zurückzuführen, dass der standardmäßig zulässige Satz eine leere Menge darstellt, wenn mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eine Teilmenge von Cubezellen aufgelöst wird.  
  
## <a name="set-readwrite-permissions-on-a-cell"></a>Festlegen von Lese-/Schreibberechtigungen für eine Zelle  
 Lese-/Schreibberechtigungen für eine Zelle werden verwendet, um das Rückschreiben zu ermöglichen, vorausgesetzt, die Elemente verfügen über Lese-/Schreibberechtigungen für den Cube selbst. Auf Zellenebene erteilte Berechtigungen können nicht höher sein, als die auf Cubeebene erteilten Berechtigungen. Weitere Informationen finden Sie unter [Einrichten des Rückschreibens von Partitionen](set-partition-writeback.md) .  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Generator &#40;Analysis Services – Mehrdimensionale Daten&#41;](../mdx-builder-analysis-services-multidimensional-data.md)   
 [Grundlegendes MDX-Skript &#40;MDX&#41;](mdx/the-basic-mdx-script-mdx.md)   
 [Erteilen von Berechtigungen zum Verarbeiten &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)   
 [Gewähren von Berechtigungen in einer Dimension &#40;Analysis Services&#41;](grant-permissions-on-a-dimension-analysis-services.md)   
 [Erteilen von benutzerdefiniertem Zugriff auf Dimensionsdaten &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Erteilen von Cube- oder Modellberechtigungen &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)  
  
  
