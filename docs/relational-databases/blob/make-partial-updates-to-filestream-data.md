---
title: Vornehmen von Teilupdates an FILESTREAM-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 86e18215f393971debf60c377514a261937bf647
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664719"
---
# <a name="make-partial-updates-to-filestream-data"></a>Vornehmen von Teilupdates an FILESTREAM-Daten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Eine Anwendung verwendet FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT, um Teilaktualisierungen für FILESTREAM-BLOB-Daten vorzunehmen. Die Funktion [DeviceIoControl](https://go.microsoft.com/fwlink/?LinkId=105527) übergibt diesen Wert und das Handle, das von [OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) zurückgegeben wird, an den FILESTREAM-Treiber. Der Treiber erzwingt dann eine serverseitige Kopie der aktuellen FILESTREAM-Daten in die Datei, auf die das Handle verweist. Wenn die Anwendung den FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT-Wert ausgibt, nachdem in die durch das Handle bezeichnete Datei geschrieben wurde, werden die Daten des letzten Schreibvorgangs persistent gespeichert und alle für das Handle zuvor geschriebenen Daten gehen verloren.  
  
> [!NOTE]  
>  FILESTREAM benötigt für den Remotezugriff das [SMB-Protokoll](https://go.microsoft.com/fwlink/?LinkId=112454) .  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie den `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` -Wert verwenden, um ein Teilupdate eines eingefügten FILESTREAM-BLOB-Elements durchzuführen.  
  
> [!NOTE]  
>  Für dieses Beispiel sind die FILESTREAM-aktivierte Datenbank und die Tabelle erforderlich, die unter [Erstellen einer FILESTREAM-aktivierten Datenbank](../../relational-databases/blob/create-a-filestream-enabled-database.md) und [Erstellen einer Tabelle zum Speichern von FILESTREAM-Daten](../../relational-databases/blob/create-a-table-for-storing-filestream-data.md)erstellt werden.  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../relational-databases/blob/codesnippet/cpp/make-partial-updates-to-_1.cpp)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [ZUgreifen auf FILESTREAM-Daten mit OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [Erstellen von Clientanwendungen für FILESTREAM-Daten](../../relational-databases/blob/create-client-applications-for-filestream-data.md)  
  
  
