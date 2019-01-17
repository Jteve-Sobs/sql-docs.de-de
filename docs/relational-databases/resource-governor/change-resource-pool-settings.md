---
title: Ändern der Einstellungen für den Ressourcenpool | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool alter
- resource pools [SQL Server], alter
ms.assetid: 49438285-a011-4dac-bd4f-f35cd90fda61
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: c851ecad687008d303ff9b228d27f9fbcc96e58c
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380585"
---
# <a name="change-resource-pool-settings"></a>Ändern der Einstellungen für den Ressourcenpool
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Sie können die Einstellungen für Ressourcenpools in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit [!INCLUDE[tsql](../../includes/tsql-md.md)]ändern.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So ändern Sie die Einstellungen eines Ressourcenpools mit:**  [SQL Server Management Studio](#ChgRPProp), [Transact-SQL](#ChgRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Der maximale CPU-Prozentsatz muss gleich oder höher als der minimale CPU-Prozentsatz sein. Der maximale Arbeitsspeicherprozentsatz muss gleich oder höher als der minimale Arbeitsspeicherprozentsatz sein.  
  
 Die Summe der minimalen CPU-Prozentsätze und minimalen Arbeitsspeicherprozentsätze für alle Ressourcenpools darf nicht größer als 100 sein.  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Ändern der Einstellungen für Ressourcenpools ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="ChgRPProp"></a> Ändern der Einstellungen für Ressourcenpools in SQL Server Management Studio  
 **So ändern Sie Ressourcenpooleinstellungen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer und erweitern Sie rekursiv den Knoten **Verwaltung** bis einschließlich zum Eintrag **Ressourcenpools**.  
  
2.  Klicken Sie mit der rechten Maustaste auf den zu ändernden Ressourcenpool, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie auf der Seite **Eigenschaften der Ressourcenkontrolle** die Zeile für den Ressourcenpool im Raster **Ressourcenpools** aus, sofern diese nicht automatisch ausgewählt wurde.  
  
4.  Klicken oder doppelklicken Sie auf die Zellen in der zu ändernden Zeile, und geben Sie die neuen Werte ein.  
  
5.  Klicken Sie auf **OK**, um die Änderungen zu speichern.  
  
##  <a name="ChgRPTSQL"></a> Ändern der Ressourcenpooleinstellungen mit Transact-SQL  
 **So ändern Sie Ressourcenpooleinstellungen in [!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
1.  Führen Sie die **ALTER RESOURCE POOL** - oder **ALTER EXTERNAL RESOURCE POOL** -Anweisung zum Festlegen der zu ändernden Eigenschaftswerte aus.  
  
2.  Führen Sie die **ALTER RESOURCE GOVERNOR RECONFIGURE** -Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Im folgenden Beispiel wird die maximale CPU-Prozenteinstellung für den Ressourcenpool `poolAdhoc`geändert.  
  
```  
ALTER RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Aktivieren der Ressourcenkontrolle](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Erstellen eines Ressourcenpools](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Löschen eines Ressourcenpools](../../relational-databases/resource-governor/delete-a-resource-pool.md)   
 [Arbeitsauslastungsgruppe der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Klassifizierungsfunktion der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  
