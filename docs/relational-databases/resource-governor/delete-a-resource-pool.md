---
title: Löschen eines Ressourcenpools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 8e95c665cc96d98de6664e5af58ed90d4cf70d02
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380561"
---
# <a name="delete-a-resource-pool"></a>Löschen eines Ressourcenpools
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Einen Ressourcenpool können Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder mit Transact-SQL löschen.  
  
-   **Vorbereitungen:**  [Begrenzungen und Einschränkungen](#LimitationsRestrictions), [Berechtigungen](#Permissions)  
  
-   **So löschen Sie einen Ressourcenpool mit:** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Ressourcenpools mit Arbeitsauslastungsgruppen können nicht gelöscht werden.  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
 Standardpools oder interne Ressourcenpools der Ressourcenkontrolle können nicht gelöscht werden. Ressourcenpools mit Arbeitsauslastungsgruppen können nicht gelöscht werden. Weitere Informationen finden Sie unter [Delete a Workload Group](../../relational-databases/resource-governor/delete-a-workload-group.md).  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Löschen eines Ressourcenpools ist die CONTROL SERVER-Berechtigung erforderlich.  
  
##  <a name="DelRPSSMS"></a> Löschen eines Ressourcenpools im Objekt-Explorer  
 **So löschen Sie einen Ressourcenpool in SQL Server Management Studio**  
  
1.  Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]den Objekt-Explorer, und erweitern Sie den Knoten **Verwaltung** rekursiv, bis **Ressourcenkontrolle**angezeigt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den zu löschenden Ressourcenpool, und klicken Sie anschließend auf **Löschen**.  
  
3.  Im Fenster **Objekt löschen** wird der Ressourcenpool in der Liste **Zu löschendes Objekt** aufgeführt. Um den Ressourcenpool zu löschen, klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Falls der zu löschende Ressourcenpool eine Arbeitsauslastungsgruppe enthält, schlägt dieser Vorgang fehl.  
  
##  <a name="DelRPTSQL"></a> Löschen eines Ressourcenpools mit Transact-SQL  
 **So löschen Sie einen Ressourcenpool mit Transact-SQL**  
  
1.  Führen Sie die **DROP RESOURCE POOL** oder die **DROP EXTERNAL RESOURCE POOL** -Anweisung aus, und geben Sie den Namen des zu löschenden Ressourcenpools an.  
  
2.  Führen Sie die **ALTER RESOURCE GOVERNOR RECONFIGURE** -Anweisung aus.  
  
### <a name="example-transact-sql"></a>Beispiel (Transact-SQL)  
 Das folgende Beispiel löscht die Arbeitsauslastungsgruppe `poolAdhoc`.  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Erstellen eines Ressourcenpools](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Ändern der Einstellungen für den Ressourcenpool](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [Arbeitsauslastungsgruppe der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Klassifizierungsfunktion der Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  
