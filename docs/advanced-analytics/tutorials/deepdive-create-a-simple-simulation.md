---
title: Erstellen einer einfachen Simulation (SQL und R tieferer) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b0db5fdfd177f1303432659f7a96b0fbf111c000
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51698238"
---
# <a name="create-a-simple-simulation-sql-and-r-deep-dive"></a>Erstellen einer einfachen Simulation (SQL und R tieferer)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel ist der letzte Schritt im Tutorial zur Verwendung von Data Science Deep Dive [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Bis jetzt Sie verwende R-Funktionen, die entwickelt wurden speziell für das Verschieben von Daten zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einem lokalen computekontext. Angenommen jedoch, Sie schreiben eine eigene benutzerdefinierte R-Funktion und möchten sie im Serverkontext ausführen.

Sie können eine beliebige Funktion im Kontext des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computers aufrufen, indem Sie die [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) -Funktion verwenden. Sie können auch **RxExec** um explizit Arbeit über die Kerne in einem einzelnen Server zu verteilen.

In dieser Lektion verwenden Sie den Remoteserver, um einer einfachen Simulation zu erstellen. Die Simulation erfordert keinerlei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten. Das Beispiel demonstriert nur, wie Sie eine benutzerdefinierte Funktion entwerfen und sie anschließend mithilfe von **rxExec** aufrufen.

Ein komplexeres Beispiel der Verwendung von **RxExec**, finden Sie im Artikel: [grob differenzierte Parallelität mit Foreach und RxExec](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)

## <a name="create-the-custom-function"></a>Die benutzerdefinierte Funktion erstellen

Ein bekanntes Spiel im Casino ist das Würfeln mit folgenden Regeln:

- Wenn Sie eine 7 oder 11 beim ersten Wurf würfeln, gewinnen Sie.
- Wenn Sie eine 2, 3 oder 12 würfeln, verlieren Sie.
- Wenn Sie eine 4, 5, 6, 8, 9 oder 10 würfeln, wird diese Zahl zu Ihrem Point, und Sie würfeln weiter, bis Sie entweder noch einmal Ihren Point würfeln (dann gewinnen Sie) oder eine 7 würfeln, was bedeutet, dass Sie verlieren.

Das Spiel wird in R einfach simuliert, indem Sie eine benutzerdefinierte Funktion erstellen und diese anschließend mehrmals ausführen.

1.  Erstellen Sie die benutzerdefinierte Funktion mit dem folgenden R-Code:
  
    ```R
    rollDice <- function()
    {
        result <- NULL
        point <- NULL
        count <- 1
            while (is.null(result))
            {
                roll <- sum(sample(6, 2, replace=TRUE))
  
                if (is.null(point))
                { point <- roll }
                if (count == 1 && (roll == 7 || roll == 11))
                {  result <- "Win" }
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))
                { result \<- "Loss" }
                else if (count > 1 && roll == 7 )
                { result \<- "Loss" }
                else if (count > 1 && point == roll)
                { result <- "Win" }
                else { count <- count + 1 }
            }
            result
    }
    ```
  
2.  Um ein einzelnes würfelspiel zu simulieren, führen Sie die Funktion ein.
  
    ```R
    rollDice()
    ```
  
    Haben Sie gewonnen oder verloren?
  
Jetzt sehen wir uns an, wie Sie verwenden können **RxExec** die Funktion mehrmals ausführen, um eine Simulation zu erstellen, die dabei hilft, die Wahrscheinlichkeit eines Gewinns zu bestimmen.

## <a name="create-the-simulation"></a>Erstellen der simulation

Um eine beliebige Funktion im Kontext des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computers auszuführen, rufen Sie die **rxExec** -Funktion auf. Obwohl **RxExec** auch unterstützt verteilte Ausführung einer Funktion parallel auf Knoten oder Kerne es führt die benutzerdefinierte Funktion auf dem SQL Server-Computer in einem Serverkontext, hier.

1. Rufen Sie die benutzerdefinierte Funktion als Argument an **RxExec**zusammen mit anderen Parametern, die die Simulation zu ändern.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    - Verwenden Sie das *timesToRun* -Argument, um anzugeben, wie oft die Funktion ausgeführt werden soll.  In diesem Fall würfeln Sie 20 Mal.
  
    - Die Argumente *RNGseed* und *RNGkind* können dazu verwendet werden, die Generierung von Zufallszahlen zu steuern. Wenn *RNGseed* auf **automatisch**festgelegt ist, wird ein paralleler Stream von Zufallszahlen auf jedem Worker initialisiert.
  
2. Die Funktion **rxExec** erstellt bei jeder Ausführung eine Liste mit einem Element, es passiert jedoch nicht viel, bis die Liste vollständig ist. Wenn alle Iterationen abgeschlossen sind, gibt die Zeile, die mit `length` beginnt, einen Wert zurück.
  
    Sie können anschließend den nächsten Schritt ausführen, um eine Zusammenfassung Ihrer Bilanz aus gewonnenen und verlorenen Spielen abzurufen.
  
3. Konvertieren Sie die zurückgegebene Liste mithilfe der `unlist` -Funktion von R zu einem Vektor, und fassen Sie die Ergebnisse mithilfe der `table` -Funktion verwenden.
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Ihre Ergebnisse sollten in etwa wie folgt aussehen:
  
     *Verlust – Gewinn* *12 8*

## <a name="conclusions"></a>Schlussfolgerungen

In diesem Tutorial haben Sie die folgenden Aufgaben geübt:
  
-   Abrufen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Daten, die in Analysen verwendet werden
  
-   Erstellen und Ändern von Datenquellen in R
  
-   Übergeben von Modellen, Daten und Diagrammen zwischen Ihrer Arbeitsstation und dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Server
  

Wenn Sie mit diesen Techniken mithilfe eines größeren Datensatzes von 10 Millionen Beobachtungen experimentieren möchten, stehen die Datendateien von der Website von Revolution Analytics: [Index des Datasets](https://packages.revolutionanalytics.com/datasets)

Um in dieser exemplarischen Vorgehensweise mit den umfangreicheren Datendateien erneut zu verwenden, die Daten herunter, und ändern Sie jede der Datenquellen wie folgt:

1. Ändern Sie die Variablen `ccFraudCsv` und `ccScoreCsv` um auf die neuen Datendateien zu verweisen
2. Ändern Sie den Namen der Tabelle verwiesen wird, im *SqlFraudTable* auf `ccFraud10`
3. Ändern Sie den Namen der Tabelle verwiesen wird, im *SqlScoreTable* auf `ccFraudScore10`

## <a name="additional-samples"></a>Zusätzliche Beispiele

Nun, da Sie die Verwendung von berechneten Kontexten und RevoScaler-Funktionen übergeben und Transformieren von Daten verwaltet haben, sehen Sie sich diese Tutorials:

[R-Tutorials für Machine Learning-Dienste](machine-learning-services-tutorials.md)
## <a name="previous-step"></a>Vorherigen Schritt

[Verschieben von Daten zwischen SQL Server und einer XDF-Datei](../../advanced-analytics/tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
