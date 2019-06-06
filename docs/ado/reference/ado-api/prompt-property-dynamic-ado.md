---
title: (ADO) für das dynamische Eigenschaft Prompt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4f2c778a6e922477cd8b21251a638d430ce15480
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703158"
---
# <a name="prompt-property-dynamic-ado"></a>Prompt – dynamische Eigenschaft (ADO)
Gibt an, ob der OLE DB-Anbieter, den Benutzer zur Initialisierung auffordert.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest, und gibt eine [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md) Wert.  
  
## <a name="remarks"></a>Hinweise  
 **Eingabeaufforderung** ist eine dynamische Eigenschaft, die angefügt werden kann die [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) des Objekts [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung vom OLE DB-Anbieter. Initialisierung Informationen aufgefordert wird, werden der OLE DB-Anbieter ein Dialogfeld, das in der Regel für den Benutzer angezeigt.  
  
 Dynamische Eigenschaften eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt werden abgebrochen, wenn die **Verbindung** geschlossen wird. Die **Eingabeaufforderung** Eigenschaft zurückgesetzt werden muss, bevor Sie erneut öffnen. die **Verbindung** auf einen anderen Wert als die Standardeinstellung zu verwenden.  
  
> [!NOTE]
>  Geben Sie nicht, dass der Anbieter die Benutzer in Szenarien auffordert, in dem der Benutzer nicht auf das Dialogfeld reagieren kann. Beispielsweise wird der Benutzer nicht reagieren, wenn die Anwendung auf einem Server statt auf dem Client des Benutzers ausgeführt wird, oder wenn die Anwendung auf einem System ohne angemeldeten Benutzer ausgeführt wird. In diesen Fällen wird die Anwendung eine Antwort auf unbestimmte Zeit warten und scheint zu sperren.  
  
## <a name="usage"></a>Verwendung  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
