---
title: Anmelden an einer Instanz von SQL Server (Befehlszeile) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 080c90dca2ff47c4ef217beda703615b59996112
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66785227"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a>Anmelden an einer Instanz von SQL Server (Befehlszeile)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie Sie die Konnektivität mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mithilfe des Hilfsprogramms **sqlcmd** testen.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a>So melden Sie sich an der Standardinstanz von SQL Server an  
  
1.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein, um eine Verbindung mithilfe der Windows-Authentifizierung herzustellen:  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a>So melden Sie sich an einer benannten Instanz von SQL Server an  
  
1.  Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein, um eine Verbindung mithilfe der Windows-Authentifizierung herzustellen:  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sqlcmd (Hilfsprogramm)](../../tools/sqlcmd-utility.md)   
 [osql (Hilfsprogramm)](../../tools/osql-utility.md)  
  
  
