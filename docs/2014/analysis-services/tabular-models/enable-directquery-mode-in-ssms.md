---
title: Konfigurieren von Speicherinternem oder DirectQuery-Zugriff für eine tabellarische Modelldatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 55a1a296e6a7b2a2155dea590be9321b22e73451
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66067184"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>Konfigurieren von speicherinternem oder DirectQuery-Zugriff für eine tabellarische Modelldatenbank
  In diesem Thema wird beschrieben, wie die Verbindungseigenschaften eines bereits bereitgestellten tabellarischen Modells geändert werden, um die Verwendung des Modells im DirectQuery-Modus zu aktivieren.  
  
 Weitere Informationen zu diesen Eigenschaften und die Konfiguration für die häufigsten Szenarien finden Sie unter [DirectQuery-Bereitstellungsszenarien &#40;SSAS – tabellarisch&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
## <a name="requirements"></a>Anforderungen  
 Es sind mehrere Schritte nötig, um den DirectQuery-Modus auf ein tabellarisches Modell anwenden zu können. Du musst:  
  
1.  Stellen Sie sicher, dass das Modell keine Funktionen hat, die möglicherweise Überprüfungsfehler im DirectQuery-Modus verursachen.  
  
2.  Ändern Sie den Speichermodus für das Modell, um DirectQuery zu unterstützen.  
  
3.  Stellen Sie das Modell in einem Modus bereit, in dem Abfragen in entweder einem hybriden oder reinen DirectQuery-Modus unterstützt werden.  
  
4.  Bearbeiten Sie die Verbindungszeichenfolge in der bereitgestellten Datenbank, um den DirectQuery-Modus zu unterstützen.  
  
 In diesem Thema wird davon ausgegangen, dass Sie das Modell erstellt und überprüft haben und den DirectQuery-Zugriff nur noch von einem Client (beispielsweise [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]) aktivieren müssen.  
  
## <a name="procedure"></a>Prozedur  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a>Ändern der Verbindungszeichenfolgen-Eigenschaften eines Modells  
  
1.  Öffnen Sie in SQL Server Management Studio die Instanz, für die Sie das Modell bereitgestellt haben.  
  
2.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste in des Namens der Model-Datenbank, und wählen **Eigenschaften**.  
  
3.  Suchen Sie die Eigenschaft **DirectQueryMode**. Diese Eigenschaft muss auf einen dieser Werte festgelegt werden, um die Verwendung der relationalen Datenquelle zu aktivieren:  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  
