---
title: Suchen von Text, Zahlen oder Datumswerten in einem Bericht | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Reporting Services verwenden können, um in einem Bericht nach Inhalten zu suchen, z. B. Text, Zahlen und Datumsangaben.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- searching reports
ms.assetid: 309dffe5-00f5-404f-bb63-9e6046253ae0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 39dad6e1717e151a7fc90cfac60a6adc1c7dddf2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510151"
---
# <a name="find-text-numbers-or-dates-in-a-report"></a>Suchen von Text, Zahlen oder Datumswerten in einem Bericht
  Sie können einen Bericht durchsuchen, indem Sie das Wort bzw. den Satz eingeben, den Sie suchen (der Maximalwert eines Suchbegriffs beträgt 256 Zeichen). Bei der Suche handelt es sich um eine Navigationstechnik, die einen übereinstimmenden Wert im Bericht sucht und legt den Fokus auf den Teil des Berichts, der den entsprechenden Wert enthält.  
  
 Bei der Suche wird die Groß- und Kleinschreibung beachtet, und sie beginnt bei der aktuell ausgewählten Seite oder beim aktuell markierten Abschnitt. Nur Inhalt, der im Bericht sichtbar ist, wird in den Suchvorgang eingeschlossen. Wenn der Bericht Bereiche enthält, die Sie erweitern oder reduzieren, werden Werte in einem reduzierten Bereich während der Suche ausgelassen. Sie können nur nach Text, Zahlen oder Datumsangaben suchen, die sich im aktuellen Bericht befinden. Wenn Sie einen automatisch generierten Bericht mit Durchklicken zum Durchsuchen von Daten verwenden, können Sie nicht nach einem Begriff suchen, den Sie in einem zuvor generierten Bericht gesehen haben, noch können Sie die Suche verwenden, um einen Begriff zu suchen, der möglicherweise in einem Bericht weiter unten im Datenpfad angezeigt wird.  
  
 Geben Sie beim Eingeben eines Werts für die Suche den Wert so ein, wie er Ihrer Erwartung nach im Bericht angezeigt wird. Stellen Sie keine Frage (z. B. "wie hoch ist der durchschnittliche Gewinn für diesen Monat"), es sei denn, Sie gehen davon aus, dass jedes Wort des Satzes im Bericht vorkommt.  
  
 Sie können jeweils nur nach einem Begriff oder Wert suchen. Sie können keine Suchoperatoren (wie AND oder OR), Symbole oder Platzhalter verwenden. Sie können eine Suche nicht für einen Querschnitt der Daten ausführen (beispielsweise die Suche nach Umsatzerlösen für einen bestimmten Monat für ein bestimmtes Produkt). Verwenden Sie für diese Art von Analyse den Berichts-Generator, um Berichte mit Durchklicken zu erstellen oder zu verwenden.  
  
 Für Suchvorgänge gelten Datenbank- und Modellsicherheitseinstellungen, mit denen der Zugriff auf Berichtsdaten eingeschränkt wird. Wenn Sie in einem Bericht mit Durchklicken nach einem Wert suchen, für den ein Modell als Datenquelle verwendet wird, und wenn Sie auf einen Teil des Modells keinen Zugriff haben, werden die Daten, die von diesem Teil des Modells dargestellt werden, von der Suche ausgeschlossen.  
  
### <a name="to-find-data-in-a-report"></a>So suchen Sie Daten in einem Bericht  
  
1.  Öffnen Sie den Bericht.  
  
2.  Geben Sie den zu suchenden Text, die Zahl oder den Datumswert auf der Berichtssymbolleiste ein.  
  
     Wenn die Berichtssymbolleiste nicht angezeigt wird, wurde sie absichtlich ausgeblendet, und Sie können die entsprechende Funktionalität nicht verwenden. Mit den Eigenschaften für das Berichts-Viewer-Webpart wird bestimmt, ob die Symbolleiste angezeigt wird.  
  
3.  Klicken Sie auf **Suchen**.  
  
4.  Wenn Sie nach weiteren Vorkommen desselben Wertes suchen möchten, klicken Sie auf **Weiter**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen des Berichts-Viewer-Webparts zu einer Webseite &#40;Reporting Services im integrierten SharePoint-Modus&#41;](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)  
  
  
