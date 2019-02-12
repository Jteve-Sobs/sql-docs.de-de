---
title: 'Lektion 3: Abgleich von Daten zu entfernen, um Duplikate aus der Lieferantenliste | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 059170b6-d62e-4b28-9451-99a0cc7e1f5f
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 65aa1b0531eb4ba30875e53a77551383b3f38579
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56036771"
---
# <a name="lesson-3-matching-data-to-remove-duplicates-from-supplier-list"></a>Lektion 3: Abgleich von Daten, um Duplikate aus der Lieferantenliste zu entfernen
  Sie bereiten die Wissensdatenbank für die Durchführung einer Abgleichsaktivität vor, indem Sie in der Wissensdatenbank eine Abgleichsrichtlinie erstellen. Es kann nur eine Abgleichsrichtlinie in einer Wissensdatenbank geben. Eine Abgleichsrichtlinie besteht aus einer oder mehreren Abgleichsregeln. Eine Regel identifiziert die Domänen, die an dem Abgleichsprozess beteiligt sind, und gibt die Gewichtung an, die jedem Domänenwert im Abgleichsurteil zukommt. Sie geben in der Regel an, ob Domänenwerte genau übereinstimmen müssen oder auch ähnlich sein können. Außerdem geben Sie den Grad der Ähnlichkeit an. Sie geben außerdem an, ob eine Domänenübereinstimmung eine Voraussetzung für den Abgleichsprozess ist. Sie können jede Regel separat und die gesamte Richtlinie mit Beispieldaten testen. Das Testverfahren zeigt Datensätze, deren treffergenauigkeiten größer als sind, die **Mindestergebnis für Datensätze** Schwellenwert angegeben, in der DQS-Konfiguration in einem Cluster (Gruppe). Sie können die Regeln in der Richtlinie weiter ändern, bis Sie zufrieden sind.  
  
 Nachdem Sie die Richtlinie definiert haben, erstellen Sie ein Data Quality-Projekt zur Ausführung der Abgleichsaktivität. Das Abgleichsprojekt wendet die Abgleichsregeln in der Abgleichsrichtlinie auf die zu bewertende Datenquelle an. Dieser Prozess bewertet die Wahrscheinlichkeit, dass zwei beliebige Zeilen übereinstimmen. Wenn DQS die Abgleichsanalyse ausführt, werden Cluster aus Datensätzen erstellt, die DQS als Übereinstimmungen ansieht. DQS identifiziert einen der Datensätze nach dem Zufallsprinzip als Pivotdatensatz. Sie können jeden Datensatz überprüfen und ablehnen, der keine entsprechende Übereinstimmung für den Cluster darstellt. Finden Sie unter [Erstellen einer Abgleichsrichtlinie](https://msdn.microsoft.com/library/hh270290.aspx) Weitere Informationen.  
  
 In dieser Lektion führen Sie eine Abgleichsaktivität durch, um Duplikate aus der Lieferantenliste zu entfernen. Zunächst erstellen Sie eine Abgleichsrichtlinie mit einer Regel, um Duplikate in der Lieferantenliste zu identifizieren, und veröffentlichen die Richtlinie in der Wissensdatenbank. Als Nächstes erstellen Sie ein Data Quality-Projekt für den Abgleich und führen es aus. Schließlich exportieren Sie die Ergebnisse der Abgleichsaktivität in eine Excel-Datei, die Sie später verwenden, wenn Sie Daten in Master Data Services (MDS) hochladen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1: Definieren einer Abgleichsrichtlinie](../../2014/tutorials/task-1-defining-a-matching-policy.md)  
  
  
