---
title: Arbeiten mit Datenbankobjekten
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0229ca7a79db5f502b603df2194843eb8a5fac7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74096043"
---
# <a name="creating-altering-and-removing-database-objects"></a>Erstellen, Ändern und Löschen von Datenbankenobjekten
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Die Phasen der SMO-Objekterstellung sind:  
  
1.  Erstellen einer Instanz des Objekts  
  
2.  Festlegen der Objekteigenschaften  
  
3.  Erstellen von Instanzen der untergeordneten Objekte  
  
4.  Festlegen der Eigenschaften des untergeordneten Objekts  
  
5.  Erstellen des Objekts  

 Wenn Instanzen von SMO-Objekten in einer SMO-Anwendung erstellt werden, sind sie auf der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz erst vorhanden, wenn die **Create** -Methode ausgegeben wird. Allerdings ist es nicht notwendig, eine **Create** -Methode für jedes einzelne Objekt auszugeben. Wenn ein Objekt über einen Satz untergeordneter Objekte verfügt, muss nur das übergeordnete Objekt die **Create** -Methode ausführen. Zum Beispiel erfordert die Definition einer Tabelle, dass mindestens eine Spalte darin enthalten ist. Auch kann eine Spalte nicht ohne eine Tabelle erstellt werden. Es besteht eine Abhängigkeitsbeziehung zwischen der Tabelle und ihren Spalten.  
  
 Die <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A>-Methode ermöglicht es Ihnen, Änderungen an einem Objekt vorzunehmen. Mehrere Änderungen an einem Objekt, wie beispielsweise das Hinzufügen untergeordneter Objekte zu einer der Auflistungen des Objekts oder das Ändern eines Eigenschaftswerts, werden zu einem Batch zusammengefasst und in einem Durchgang ausgeführt. Die **Alter** -Methode reduziert den Netzwerkdatenverkehr und verbessert die Gesamtleistung.  
  
 Die **Drop** -Anweisung wird dazu verwendet, ein Objekt und alle seine abhängigen untergeordneten Objekte zu entfernen, die anfänglich zur Objekterstellung erforderlich waren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SMO-Objektmodell](../../../relational-databases/server-management-objects-smo/smo-object-model.md)  
  
  
