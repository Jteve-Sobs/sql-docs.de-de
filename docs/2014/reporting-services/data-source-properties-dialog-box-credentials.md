---
title: Dialogfeld "Eigenschaften", "Anmeldeinformationen für Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.credentials.f1
- "10100"
ms.assetid: 14c3eeb6-d37b-4fda-967b-43afcdb48119
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6423c2caca256a257f660eabb8ce5eaf2d81c55f
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59961516"
---
# <a name="data-source-properties-dialog-box-credentials"></a>Datenquelleneigenschaften (Dialogfeld), Anmeldeinformationen
  Wählen Sie im Dialogfeld **Datenquelleneigenschaften** die Option **Anmeldeinformationen** aus, um die Anmeldeinformationen für eine Datenquelle im Bericht anzuzeigen und zu ändern. Die von Ihnen bereitgestellten Anmeldeinformationen werden für den Zugriff auf die Datenquelle und zum Zwischenspeichern einer Kopie der Daten für die Berichtsvorschau verwendet. Weitere Informationen dazu, wie Vorschaudaten zwischengespeichert werden, finden Sie unter [Ausführen einer Vorschau für Berichte](reports/previewing-reports.md). Weitere Anmeldeinformationen finden Sie unter [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
## <a name="options"></a>Optionen  
 **Verwenden Sie Windows-Authentifizierung (integrierte Sicherheit)**  
 Wählen Sie diese Option aus, um die Windows-Authentifizierung zu verwenden.  
  
 **Verwenden Sie diesen Benutzernamen und Kennwort**  
 Wählen Sie diese Option aus, um einen bestimmten Benutzernamen und ein bestimmtes Kennwort bereitzustellen. Für freigegebene Datenquellen gilt Folgendes: Wenn Sie das Berichtsserverprojekt auf dem Zielserver veröffentlichen, werden der Benutzername und das Kennwort als gespeicherte Anmeldeinformationen für die Datenbank gesichert. Wenn Sie den Benutzernamen und das Kennwort als Windows-Anmeldeinformationen verwenden möchten, können Sie die Eigenschaften für die veröffentlichte freigegebene Datenquelle auf dem Zielserver bearbeiten. Weitere Informationen finden Sie unter [Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).  
  
 **Benutzername**  
 Geben Sie einen Benutzernamen ein, der beim Anmelden an der Datenquelle verwendet werden soll.  
  
 **Kennwort**  
 Geben Sie ein Kennwort ein, das beim Anmelden an der Datenquelle verwendet werden soll.  
  
 **Eingabeaufforderung für Anmeldeinformationen**  
 Wählen Sie diese Option aus, um beim Ausführen des Berichts Anmeldeinformationen anzufordern.  
  
 **Eingabeaufforderungs-Zeichenfolge eingeben**  
 Geben Sie einen Satz ein, mit dem der Benutzer zur Eingabe von Anmeldeinformationen für die Datenquelle aufgefordert wird.  
  
 **Keine Anmeldeinformationen**  
 Wählen Sie diese Option aus, wenn keine Anmeldeinformationen für die Datenquelle bereitgestellt werden sollen. Diese Option kann nur verwendet werden, wenn die Datenquelle keine Anmeldeinformationen annimmt oder wenn Sie Anmeldeinformationen auf andere Art übergeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Source Dialogfeld, Allgemein](../../2014/reporting-services/data-source-properties-dialog-box-general.md)   
 [Angeben der Anmeldeinformationen und Verbindungsinformationen für Berichtsdatenquellen](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
