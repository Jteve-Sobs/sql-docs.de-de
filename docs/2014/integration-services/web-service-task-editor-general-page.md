---
title: Editor für den Task ' Webdienst ' (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c642c100e41574a525578c3392aedbc82ac419a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439847"
---
# <a name="web-service-task-editor-general-page"></a>Editor für den Task 'Webdienst' (Seite Allgemein)
  Auf der Seite **Allgemein** des Dialogfelds **Editor für den Task 'Webdienst'** können Sie einen HTTP-Verbindungs-Manager und den Speicherort der WSDL-Datei (Web Services Description Language) angeben, die der Task „Webdienst“ verwendet, den Task „Webdienst“ beschreiben und die WSDL-Datei herunterladen.  
  
 Weitere Informationen zu diesem Task finden Sie unter [Webdienst (Task)](control-flow/web-service-task.md).  
  
## <a name="options"></a>Optionen  
 **Httpconnection**  
 Wählen Sie einen Verbindungs-Manager aus der Liste aus, oder klicken Sie, \<**New connection...**> um einen neuen Verbindungs-Manager zu erstellen.  
  
> [!IMPORTANT]  
>  Der HTTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Standardauthentifizierung. Er unterstützt keine Windows-Authentifizierung.  
  
 **Verwandte Themen:**  [HTTP-Verbindungs-Manager](connection-manager/http-connection-manager.md), [HTTP-Verbindungs-Manager-Editor &#40;Seite Server&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 Geben Sie den voll qualifizierten Pfad einer WSDL-Datei ein, die sich lokal auf dem Computer befindet, oder klicken Sie auf die Schaltfläche zum Durchsuchen **(...)** , und suchen Sie diese Datei.  
  
 Wenn Sie die WSDL-Datei bereits manuell auf den Computer heruntergeladen haben, wählen Sie diese Datei aus. Wenn die WSDL-Datei jedoch noch nicht heruntergeladen wurde, führen Sie folgende Schritte aus:  
  
-   Erstellen Sie eine leere Datei mit der Dateinamenerweiterung WSDL.  
  
-   Wählen Sie diese leere Datei für die Option **WSDLFile** aus.  
  
-   Legen Sie den Wert von **overwrite tewsdlfile** auf fest, `True` damit die leere Datei mit der tatsächlichen WSDL-Datei überschrieben werden kann.  
  
-   Klicken Sie auf **WSDL herunterladen** , um die tatsächliche WSDL-Datei herunterzuladen und die leere Datei zu überschreiben.  
  
    > [!NOTE]  
    >  Die Option **WSDL herunterladen** wird erst aktiviert, wenn Sie den Namen einer vorhandenen lokalen Datei im Feld **WSDLFile** angeben.  
  
 **OverwriteWSDLFile**  
 Geben Sie an, ob die WSDL-Datei für den Task Webdienst überschrieben werden kann.  
  
 Wenn Sie die WSDL-Datei mithilfe der Schaltfläche **WSDL herunter** laden herunterladen möchten, legen Sie diesen Wert auf fest `True` .  
  
 **Name**  
 Geben Sie einen eindeutigen Namen für den Task Webdienst an. Dieser Name wird im Tasksymbol als Bezeichnung verwendet.  
  
> [!NOTE]  
>  Tasknamen müssen innerhalb eines Pakets eindeutig sein.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Tasks Webdienst ein.  
  
 **WSDL herunterladen**  
 Lädt die WSDL-Datei herunter.  
  
 Diese Schaltfläche wird erst aktiviert, wenn Sie den Namen einer vorhandenen lokalen Datei im Feld **WSDLFile** angeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task ' Webdienst ' &#40;Eingabe Seite&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Editor für den Task ' Webdienst ' &#40;Ausgabe Seite&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)  
  
  
