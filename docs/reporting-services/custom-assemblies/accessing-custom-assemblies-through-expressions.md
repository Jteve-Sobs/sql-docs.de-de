---
title: Zugriff auf benutzerdefinierte Assemblys über Ausdrücke | Microsoft-Dokumentation
ms.date: 03/04/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-assemblies
ms.topic: reference
helpviewer_keywords:
- expressions [Reporting Services], custom assemblies
- static member calls
- instance member calls [Reporting Services]
- calling class members
- custom assemblies [Reporting Services], expressions
ms.assetid: 917c4d47-1a95-4f54-98b1-e8cb2165d90f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 101af9d59d4a3f1e48d85859c91f77c8be2e4719
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "63194365"
---
# <a name="accessing-custom-assemblies-through-expressions"></a>Zugriff auf benutzerdefinierte Assemblys über Ausdrücke
  Sobald Sie eine benutzerdefinierte Assembly erstellt, diese im Berichts-Designer oder Berichtsserver zur Verfügung gestellt, die entsprechende Sicherheitsrichtlinie und in der Berichtsdefinition einen Verweis auf die benutzerdefinierte Assembly hinzugefügt haben, können Sie mit Berichtsausdrücken auf Klassenelemente in der Assembly zugreifen. Wenn Sie in einem Ausdruck auf benutzerdefinierten Code verweisen möchten, müssen Sie das Klassenelement in der Assembly aufrufen. Die Vorgehensweise hängt davon ab, ob es sich um eine statische oder um eine instanzbasierte Methode handelt.  
  
## <a name="calling-static-members-from-a-report-definition-file"></a>Aufruf statischer Elemente aus einer Berichtsdefinitionsdatei  
 Statische Elemente gehören zur Klasse oder zum Typ selbst und nicht zu einem instanziierten Objekt. Auf diese Elemente kann zugegriffen werden, indem sie direkt von der Klasse aus aufgerufen werden. Wenn möglich, sollten Sie statische Elemente verwenden, um benutzerdefinierte Funktionen in einem Bericht aufzurufen, da die Leistung von statischen Elementen am besten ist. Um ein statisches Element aufzurufen, müssen Sie darauf als Ausdruck in der Form =*Namespace.Class.Method* verweisen.  
  
#### <a name="to-call-static-members"></a>So rufen Sie statische Elemente auf  
  
-   Um ein statisches Element aufzurufen, stellen Sie den Ausdruck auf den vollqualifizierten Namen des Elements ein, der Namespace, den Klassennamen und den Elementnamen umfasst. Im folgenden Beispiel wird die **ToGBP**-Methode verwendet, bei der der Wert des Felds **StandardCost** von Dollar in britische Pund umgerechnet und in einem Bericht angezeigt wird:  
  
    ```  
    =CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
    ```  
  
### <a name="important-information-regarding-static-fields-and-properties"></a>Wichtige Informationen für statische Felder und Eigenschaften  
 Derzeit werden alle Berichte in der gleichen Anwendungsdomäne ausgeführt. Das bedeutet, dass Berichte mit benutzerdefinierten, statischen Daten diese Daten in anderen Instanzen desselben Berichts zur Verfügung stellen. Dies kann dazu führen, dass die statischen Daten eines Benutzers allen Benutzern, die einen bestimmten Bericht ausführen, zur Verfügung gestellt werden. Aus diesem Grund empfiehlt es sich, keine statischen Felder oder Eigenschaften in benutzerdefinierten Assemblys oder im **Code-Element**, sondern stattdessen Instanzfelder bzw. -eigenschaften in Berichten zu verwenden. Statische Methoden können trotzdem verwendet werden, da sie weder Status noch Daten speichern.  
  
## <a name="calling-instance-members-from-a-report-definition-file"></a>Aufruf von Instanzelementen aus einer Berichtsdefinitionsdatei  
 Wenn die benutzerdefinierte Assembly Instanzelemente enthält, auf die Sie in einer Berichtsdefinition zugreifen müssen, müssen Sie einen Instanznamen für die Klasse des Berichts hinzufügen. Hierzu verwenden Sie die Registerkarte **Code** des Dialogfelds **Berichtseigenschaften**. Weitere Informationen zum Hinzufügen von Klasseninstanzen zu einem Bericht finden Sie unter [Benutzerdefinierter Code und Assemblyverweise in Ausdrücken in Berichts-Designer (SSRS)](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 Um ein statisches Element aufzurufen, müssen Sie als Ausdruck in der Form =Code *.InstanceName.Method* darauf verweisen.  
  
#### <a name="to-call-instance-members"></a>So rufen Sie Instanzelemente auf  
  
-   Um ein Instanzelement einer benutzerdefinierten Assembly aufzurufen, müssen Sie auf das Schlüsselwort **Code** gefolgt vom Instanznamen und der Methode verweisen. Im folgenden Beispiel wird die Instanzmethode **ToEUR** verwendet, bei der der Wert des Felds **StandardCost** von Dollar in Euro umgerechnet und in einem Bericht angezeigt wird:  
  
    ```  
    =Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
