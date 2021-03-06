---
title: Mit Microsoft Azure Storage verbinden
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 07/12/2017
ms.openlocfilehash: f88bafe27da30ceec6154bf64cd9ced0046f7e87
ms.sourcegitcommit: d855def79af642233cbc3c5909bc7dfe04c4aa23
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87123081"
---
# <a name="connect-to-microsoft-azure-storage"></a>Mit Microsoft Azure Storage verbinden

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Verwenden Sie das Dialogfeld **Azure Storage-Verbindung**, um ein Speicherkonto anzugeben und die Verbindung mit Azure zu überprüfen.  
  
## <a name="options"></a>Tastatur  
Geben Sie die folgenden Informationen zu Ihrem Azure-Konto an, und klicken Sie dann auf **Weiter**, um fortzufahren.  
  
1.  **Speicherkonto** – Geben Sie den Speicherkontonamen an.

   >[!NOTE]
   > Sie können nur Verbindungen zu [allgemeinen Speicherkonten](https://docs.microsoft.com/azure/storage/common/storage-introduction#azure-storage-services) herstellen. Die Verbindungserstellung zu anderen Arten von Speicherkonten kann zu einem Fehler wie dem folgenden führen:
   >
   >  Der Wert eines der HTTP-Header weist nicht das richtige Format auf. (Microsoft.SqlServer.StorageClient).
   >
   >  The remote server returned an error: (400) Bad Request. (Der Remoteserver hat einen Fehler zurückgegeben: (400) Ungültige Anforderung.) (System)

2.  **Kontoschlüssel** – Geben Sie den Kontoschlüssel für das angegebene Speicherkonto an.  
  
3.  **Sichere Endpunkte verwenden (HTTPS)** : Bei Aktivierung dieser Option wird die Kommunikation verschlüsselt, und für Netzwerkwebserver wird eine sichere Identifikation verwendet.  
  
4.  **Kontoschlüssel speichern** – Bei Aktivierung dieser Option wird das Kennwort in einer verschlüsselten Datei gespeichert.  
  
