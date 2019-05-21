---
title: Filtereinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a626e79a33c134a3bdde5880b68f2545c6dea78e
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129640"
---
# <a name="filter-settings"></a>Filtereinstellungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Im Dialogfeld **Filtereinstellungen** können Sie Filter für Raster im Replikationsmonitor definieren. Wenn Sie z. B. nur die aktiven Abonnements auf der Registerkarte **Alle Abonnements** anzeigen möchten, wählen Sie in der Spalte **Spaltenname** den Eintrag **Status** , in der Spalte **Operator** den Eintrag **Ist gleich** und in der Spalte **Wert1** den Eintrag **Aktiv** aus. Wenn Sie einen auf einer oder mehreren Spalten basierenden Filter definiert haben, wird dieser Filter angewendet, sodass im Raster nur die Teilmenge von Zeilen angezeigt wird, die die Filterkriterien erfüllen.  
  
## <a name="options"></a>Optionen  
 **Status**  
 Wählen Sie den Namen der Spalte aus, für die Sie einen Filter definieren möchten. Sie können einen Filter für eine oder mehrere Spalten definieren.  
  
 **Ist gleich**  
 Wählen Sie für den Filter einen Operator wie **Kleiner als oder gleich**aus.  
  
 **Wert1** und **Wert2**  
 Geben Sie einen Wert für den Filter ein, oder wählen Sie einen Wert aus. Für die meisten Operatoren muss nur in der Spalte **Wert1** ein Wert eingegeben werden. Für die Operatoren **Zwischen** und **Nicht zwischen** muss jedoch auch in der Spalte **Wert2** ein Wert eingegeben werden.  
  
 **Filter löschen**  
 Klicken Sie auf diese Schaltfläche, um alle definierten Filter zu löschen. Wenn Sie einen einzelnen Filter entfernen möchten, wählen Sie die Filterzeile aus, und drücken Sie die ENTF-TASTE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Replikation](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
