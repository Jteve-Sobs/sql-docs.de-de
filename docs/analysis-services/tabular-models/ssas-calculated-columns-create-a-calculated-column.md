---
title: Erstellen Sie eine berechnete Spalte in Analysis Services | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 705428d2c2a6671452a1d95e06e500f4860574e0
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53071937"
---
# <a name="create-a-calculated-column"></a>Erstellen einer berechneten Spalte
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Mithilfe berechneter Spalten können Sie dem Modell neue Daten hinzufügen. Anstatt einzufügen, oder Importieren von Werten in der Spalte, erstellen Sie eine DAX-Formel, die zeilenebenenwerte der Spalte definiert. Die Werte in den einzelnen Zeilen einer berechneten Spalte werden berechnet und aufgefüllt, wenn Sie eine gültige Formel erstellen und die EINGABETASTE drücken. Die berechnete Spalte kann anschließend wie jeder andere Datenspalte einer Berichterstellungs- oder Analyseanwendung hinzugefügt werden. In diesem Artikel wird beschrieben, wie Sie eine neue berechnete Spalte erstellen, mit der DAX-Bearbeitungsleiste im Modell-Designer.  
  
#### <a name="to-create-a-new-calculated-column"></a>So erstellen Sie eine neue berechnete Spalte  
  
1.  Wählen Sie im Modell-Designer in der Datensicht die Tabelle aus, der Sie eine berechnete Spalte hinzufügen möchten, und klicken Sie dann auf das Menü **Spalte** und auf **Spalte hinzufügen**.  
  
     In der leeren Spalte am äußersten rechten Rand wird**Spalte hinzufügen** hervorgehoben, und der Cursor wird in die Bearbeitungsleiste verschoben.  
  
     Klicken Sie mit der rechten Maustaste auf eine vorhandene Spalte, und klicken Sie dann auf **Spalte einfügen**, um zwischen zwei vorhandenen Spalten eine neue Spalte zu erstellen.  
  
2.  Führen Sie in der Bearbeitungsleiste einen der folgenden Schritte aus:  
  
    -   Geben Sie ein Gleichheitszeichen gefolgt von einer Formel ein.  
  
    -   Geben Sie ein Gleichheitszeichen gefolgt von einer DAX-Funktion, den Argumenten und Parametern ein, die von der Funktion benötigt werden.  
  
    -   Klicken Sie auf die Funktionsschaltfläche (**fx**), und wählen Sie dann im Dialogfeld **Funktion einfügen** eine Kategorie und eine Funktion aus. Klicken Sie abschließend auf **OK**. Geben Sie in der Bearbeitungsleiste die übrigen Argumente und Parameter ein, die von der Funktion benötigt werden.  
  
3.  Drücken Sie die EINGABETASTE, um die Formel zu übernehmen.  
  
     Die gesamte Spalte wird mit der Formel aufgefüllt, d. h., für jede Zeile wird ein Wert berechnet.  
  
> [!TIP]  
>  Sie können AutoVervollständigen für DAX-Formeln auch mitten in einer vorhandenen Formel mit geschachtelten Funktionen verwenden. Ausgehend vom Text unmittelbar vor der Einfügemarke werden Werte in der Dropdownliste angezeigt. Der Text nach der Einfügemarke bleibt unverändert.  
  
## <a name="see-also"></a>Siehe auch  
 [Berechnete Spalten](../../analysis-services/tabular-models/ssas-calculated-columns.md)   
 [Measures](../../analysis-services/tabular-models/measures-ssas-tabular.md)  
  
  
