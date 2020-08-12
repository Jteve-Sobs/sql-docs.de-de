---
title: Zulassen, dass Textfelder vergrößert oder verkleinert werden (Berichts-Generator) | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie, wie Sie Eigenschaftenoptionen in paginierten Berichten im Berichts-Generator festlegen, mit denen ein Textfeld je nach Inhalt erweitert oder verkleinert wird.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: dbc01e78-5993-47e5-af04-34f9e3bbcee1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2e224794dde1c171c583106bf1680ba19da23ed2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84994545"
---
# <a name="allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs"></a>Zulassen, dass Textfelder vergrößert oder verkleinert werden (Berichts-Generator und SSRS)
  In einem paginierten [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]-Bericht sind Textfelder nicht nur eigenständige Felder auf der Berichtsentwurfsoberfläche. Jede Zelle in einer Tabelle oder Matrix (einem Tablix-Datenbereich) enthält auch ein Textfeld, das auf dieselbe Weise formatiert werden kann wie eigenständige Textfelder. Standardmäßig haben Textfelder eine feste Größe. Sie können Optionen festlegen, durch die ein Textfeld in Anpassung an seinen Inhalt vergrößert oder verkleinert wird. Diese Optionen entsprechen der **CanGrow** -Eigenschaft bzw. der **CanShrink** -Eigenschaft im Bereich Eigenschaften.  
  
## <a name="to-allow-a-text-box-to-grow-or-shrink"></a>So lassen Sie zu, dass ein Textfeld vergrößert oder verkleinert wird  
  
1.  Klicken Sie mit der rechten Maustaste auf das Textfeld, und klicken Sie dann auf **Textfeldeigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Allgemein**.  
  
    -   Wenn ein Textfeld basierend auf dem Inhalt vertikal erweitert werden soll, wählen Sie **Vergrößern der Höhe zulassen**.  
  
    -   Wenn ein Textfeld basierend auf dem Inhalt verkleinert werden soll, wählen Sie **Verringern der Höhe zulassen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Textfelder &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)  
  
  
