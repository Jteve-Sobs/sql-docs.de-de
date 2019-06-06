---
title: 'Schritt 4: Auffüllen des Texfelds "Details" | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8a2d19ed59aa10ad75843df03d626f5f880462ca
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718706"
---
# <a name="step-4-populate-the-details-text-box"></a>Schritt 4: Auffüllen des Textfelds „Details“
Zum Auffüllen der texfelds "Details", erstellen Sie eine neue Unterroutine namens **RecFields** und fügen Sie den folgenden Code:  
  
```  
Sub recFields(r As Record, l As ListBox, t As TextBox)  
    Dim f As Field  
    Dim s As Stream  
    Set s = New Stream  
    Dim str As String  
  
    For Each f In r.Fields  
        l.AddItem f.Name & ": " & f.Value  
    Next  
    t.Text = ""  
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then  
        s.Open r, adModeRead, adOpenStreamFromRecord  
        str = s.ReadText(1)  
        s.Position = 0  
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"  
            s.Charset = "ascii"  
            s.Type = adTypeText  
        End If  
        t.Text = s.ReadText(adReadAll)  
    End If  
End Sub  
```  
  
 Dieser Code füllt `lstDetails` mit den Feldern und Werten des Datensatzes einfache übergeben `recFields`. Wenn die Ressource eine Textdatei ist, wird ein Text-Stream im Ressourcendatensatz geöffnet. Der Code bestimmt, ob der Zeichensatz ASCII ist und den Inhalt der Stream in kopiert `txtDetails`.  
  
## <a name="see-also"></a>Siehe auch  
 [Internet Publishing-Szenario](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Schritt 3: Auffüllen des Listenfelds "Fields"](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
