---
title: Pfadausdrücke (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- path expressions [XQuery]
- expressions [XQuery], path
ms.assetid: b93fa36c-bf69-46b9-b137-f597d66fd0c0
author: rothja
ms.author: jroth
ms.openlocfilehash: 9be2fb8752f27164e0e6dbc59e499f4b048d8979
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946391"
---
# <a name="path-expressions-xquery"></a>Pfadausdrücke (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Über XQuery-Pfadausdrücke werden in einem Dokument enthaltene Knoten gesucht, z. B. Element-, Attribut- und Textknoten. Das Ergebnis eines Pfadausdrucks erscheint immer in der Dokumentreihenfolge ohne Duplikatknoten in der Ergebnissequenz. Beim Angeben eines Pfads können Sie entweder die vollständige oder die abgekürzte Syntax verwenden. Die folgenden Informationen beziehen sich auf die ungekürzte Syntax. Die abgekürzte Syntax wird anschließend beschrieben.  
  
> [!NOTE]  
>  Da die Beispielabfragen in diesem Thema, für angegeben werden die **Xml** Spalten vom Typ **CatalogDescription** und **Anweisungen**in die  **ProductModel** Tabelle, Sie sollten sich vertraut machen mit dem Inhalt und Struktur der XML-Dokumente in diesen Spalten gespeichert.  
  
 Ein Pfadausdruck kann relativ oder absolut sein. Beide sind im Folgenden beschrieben:  
  
-   Ein relativer Pfadausdruck besteht aus einem oder mehreren Schritten, die durch einen oder zwei Schrägstriche (/ oder //) getrennt sind. Beispiel: `child::Features` ist ein relativer Pfadausdruck, in dem `Child` nur auf die untergeordneten Knoten des Kontextknotens verweist. Dies ist der Knoten der gegenwärtig verarbeitet wird. Ruft der Ausdruck ab, der \<Features >-Element untergeordneten Knoten des Kontextknotens.  
  
-   Ein absoluter Pfadausdruck beginnt mit einem oder zwei Schrägstrichen (/ oder //), auf die ein optionaler relativer Pfad folgt. Beispiel: Der erste Schrägstrich des Ausdrucks `/child::ProductDescription` gibt an, dass es sich um einen absoluten Pfadausdruck handelt. Da ein Schrägstrich am Anfang eines Ausdrucks den Stammknoten des Dokuments Knoten des Kontextknotens zurückgibt, gibt der Ausdruck alle die \<ProductDescription > untergeordneten Elementknoten des Basisverzeichnisses.  
  
     Wenn ein absoluter Pfad mit einem einzelnen Schrägstrich beginnt, kann darauf ein relativer Pfad folgen. Wenn Sie nur einen Schrägstrich angeben, gibt der Ausdruck den Stammknoten des Kontextknotens zurück. Bei einem XML-Datentyp ist dies der Dokumentknoten.  
  
 Ein typischer Pfadausdruck besteht aus Schritten. Z. B. der absolute Pfadausdruck `/child::ProductDescription/child::Summary`, enthält zwei durch einen Schrägstrich getrennte Schritte.  
  
-   Ruft ab, der erste Schritt der \<ProductDescription > untergeordneten Elementknoten des Basisverzeichnisses.  
  
-   Der zweite Schritt Ruft die \<Zusammenfassung > für jeden der abgerufenen untergeordneten Elementknoten \<ProductDescription > Elementknoten, der wiederum der Kontextknoten wird.  
  
 Bei einem Schritt eines Pfadausdrucks kann es sich um einen Achsen- oder um einen allgemeinen Schritt handeln.  
  
## <a name="axis-step"></a>Achsenschritt  
 Ein Achsenschritt in einem Pfadausdruck besteht aus den folgenden Teilen.  
  
 [axis](../xquery/path-expressions-specifying-axis.md)  
 Definiert die Bewegungsrichtung. Ein Achsenschritt in einem Pfadausdruck beginnt beim Kontextknoten und navigiert zu den in der durch die Achse angegebenen Richtung erreichbaren Knoten.  
  
 [Knotentest](../xquery/path-expressions-specifying-node-test.md)  
 Gibt an, welcher Knotentyp oder welche Knotennamen ausgewählt werden sollen.  
  
 Keines oder beliebig viele optionale Prädikate  
 Filtert die Knoten, indem einige ausgewählt und andere verworfen werden.  
  
 Die folgenden Beispiele verwenden eine **Axisstep** in der Path-Ausdrücken:  
  
-   Der absolute Pfadausdruck `/child::ProductDescription` enthält nur einen Schritt. Er gibt eine Achse (`child`) und einen Knotentest (`ProductDescription`) an.  
  
-   Der relative Pfadausdruck `child::ProductDescription/child::Features` enthält zwei durch einen Schrägstrich getrennte Schritte. Beide Schritte geben eine untergeordnete Achse an. ProductDescription und Features sind Knotentests.  
  
-   Der relative Pfadausdruck `child::root/child::Location[attribute::LocationID=10]`, enthält zwei durch einen Schrägstrich getrennte Schritte. Der erste Schritt gibt eine Achse (`child`) und einen Knotentest (`root`) an. Der zweite Schritt gibt alle drei Komponenten eines Achsenschritts an: eine Achse (child), einen Knotentest (`Location`) und ein Prädikat (`[attribute::LocationID=10]`).  
  
 Weitere Informationen zu den Komponenten eines achsenschritts finden Sie unter [Achse angeben, in einem Schritt eines Pfadausdrucks](../xquery/path-expressions-specifying-axis.md), [Knotentest angeben, in einem Schritt eines Pfadausdrucks](../xquery/path-expressions-specifying-node-test.md), und [angeben von Auswahlprädikaten im eine Schritt eines pfadausdrucks](../xquery/path-expressions-specifying-predicates.md).  
  
## <a name="general-step"></a>Allgemeiner Schritt  
 Ein allgemeiner Schritt ist lediglich ein Ausdruck, der eine Knotensequenz auswerten muss.  
  
 Die XQuery-Implementierung in SQL Server unterstützt einen allgemeinen Schritt als ersten Schritt eines Pfadausdrucks. In den folgenden Beispielen werden Pfadausdrücke mit allgemeinen Schritten verwendet:  
  
```  
(/a, /b)/c  
id(/a/b)  
```  
  
 Weitere Informationen zu den Id-Funktion finden Sie unter [Id-Funktion &#40;XQuery&#41;](../xquery/functions-on-sequences-id.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben einer Achse in einem Pfadausdrucksschritt](../xquery/path-expressions-specifying-axis.md)  
 Beschreibt das Arbeiten mit dem Achsenschritt in einem Pfadausdruck.  
  
 [Angeben von Knotentests in einem Pfadausdrucksschritt](../xquery/path-expressions-specifying-node-test.md)  
 Beschreibt das Arbeiten mit Knotentests in einem Pfadausdruck.  
  
 [Angeben von Prädikaten in einem Pfadausdrucksschritt](../xquery/path-expressions-specifying-predicates.md)  
 Beschreibt das Arbeiten mit Prädikaten in einem Pfadausdruck.  
  
 [Verwenden abgekürzter Syntax in einem Pfadausdruck](../xquery/path-expressions-using-abbreviated-syntax.md)  
 Beschreibt das Arbeiten mit einer abgekürzten Syntax in einem Pfadausdruck.  
  
  
