---
title: Konfigurieren des Data Warehouses für den Steuerungspunkt für das Hilfsprogramm (SQL Server-Hilfsprogramm) | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f71e3ce611c8bf4b9ecfdd0cdafdafe4ca771874
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68115468"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Konfigurieren des Data Warehouses für den Steuerungspunkt für das Hilfsprogramm (SQL Server-Hilfsprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die von verwalteten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen gesammelten Daten werden im UMDW (Utility Management Data Warehouse) gespeichert. Der UMDW-Dateiname lautet sysutility_mdw.  
  
 Sie können die Beibehaltungsdauer der UMDW-Daten konfigurieren. Weitere Informationen finden Sie unter [Hilfsprogrammverwaltung &#40;SQL Server-Hilfsprogramm&#41;](https://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d).  
  
 Die folgenden Konfigurationseinstellungen sind in dieser Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nicht konfigurierbar:  
  
-   UMDW name (UMDW-Name): Sysutility_mdw.  
  
-   Collection set upload frequency (Uploadhäufigkeit des Sammlungssatzes): Every 15 minutes (Alle 15 Minuten).  
  
 Das UMDW-Verzeichnis ist konfigurierbar: \<Systemlaufwerk>:\Programme\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, wobei \<Systemlaufwerk> normalerweise Laufwerk C:\ entspricht. Die Protokolldatei „Sysutility_mdw_\<GUID>_LOG“ befindet sich im selben Verzeichnis.  
  
> [!NOTE]  
>  Der Speicherort der UMDW-Datei (sysutility_mdw) kann mithilfe von Detach/Attach oder ALTER DATABASE geändert werden. Es wird empfohlen, ALTER DATABASE zu verwenden. Weitere Informationen finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
