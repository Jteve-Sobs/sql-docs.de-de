---
title: Ein SQL Server-Überwachungsprotokoll anzeigen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: fa30824e32faae5feee1612305c1ca292d44e8e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63012016"
---
# <a name="view-a-sql-server-audit-log"></a>Anzeigen eines SQL Server-Überwachungsprotokolls
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]ein SQL Server-Überwachungsprotokoll anzeigen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Anzeigen eines SQL Server Überwachungs Protokolls mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die `CONTROL SERVER`-Berechtigung.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-a-sql-server-audit-log"></a>So zeigen Sie ein SQL Server-Überwachungsprotokoll an  
  
1.  Erweitern Sie im Objekt-Explorer den Ordner **Sicherheit** .  
  
2.  Erweitern Sie den Ordner **Überwachungen** .  
  
3.  Klicken Sie mit der rechten Maustaste auf das Überwachungsprotokoll, das Sie anzeigen möchten, und klicken Sie auf **Überwachungsprotokolle anzeigen**. Dadurch wird das Dialogfeld **Protokolldatei-Viewer-**_server_name_ geöffnet. Weitere Informationen finden Sie unter [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md).  
  
4.  Wenn Sie fertig sind, klicken Sie auf **Schließen**.  
  
 
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] empfiehlt, das Überwachungsprotokoll mit dem Protokolldatei-Viewer anzuzeigen. Wenn Sie jedoch ein automatisiertes Überwachungssystem erstellen, können die Informationen in der Überwachungsdatei direkt mit der Funktion [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) gelesen werden. Beim direkten Lesen der Datei werden die Daten in einem etwas anderen (unverarbeiteten) Format zurückgegeben. Weitere Informationen finden Sie unter **sys. fn_get_audit_file**  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Überwachungs &#40;Datenbank-Engine&#41;](sql-server-audit-database-engine.md)   
 [Schreiben von SQL-Serverüberwachungsereignissen in das Sicherheitsprotokoll](write-sql-server-audit-events-to-the-security-log.md)  
  
  
