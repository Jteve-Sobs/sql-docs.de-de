---
title: ODBC-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.odbcconnection.f1
helpviewer_keywords:
- connections [Integration Services], ODBC
- ODBC connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], ODBC
ms.assetid: e8c77aa7-6772-485e-918e-cef9eeb18c58
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4a9b8fa4b316c34bb2cfc4b51c0fcb6ba310367e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104030"
---
# <a name="odbc-connection-manager"></a>ODBC-Verbindungs-Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Mit einem ODBC-Verbindungs-Manager kann ein Paket eine Verbindung mit einer Reihe von Datenbank-Managementsystemen mithilfe der ODBC-Spezifikation (Open Database Connectivity) herstellen.  
  
 Wenn Sie einem Paket eine ODBC-Verbindung hinzufügen und die Eigenschaften des Verbindungs-Managers festlegen, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager und fügt den Verbindungs-Manager der **Connections** -Auflistung des Pakets hinzu. Zur Laufzeit wird der Verbindungs-Manager als physische ODBC-Verbindung aufgelöst.  
  
 Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **ODBC**festgelegt.  
  
 Es gibt folgende Möglichkeiten, um den ODBC-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie eine Verbindungszeichenfolge an, die auf einen Benutzer- oder System-Datenquellennamen verweist.  
  
-   Geben Sie den Server für die Verbindungsherstellung an.  
  
-   Geben Sie an, ob die Verbindung zur Laufzeit beibehalten wird.  
  
## <a name="configuration-of-the-odbc-connection-manager"></a>Konfiguration des ODBC-Verbindungs-Managers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [ODBC-Verbindungs-Manager: Referenz zur Benutzeroberfläche](../../integration-services/connection-manager/odbc-connection-manager-ui-reference.md)  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="odbc-connection-manager-ui-reference"></a>ODBC-Verbindungs-Manager – Referenz zur Benutzeroberfläche
  Im Dialogfeld **ODBC-Verbindungs-Manager konfigurieren** können Sie einer ODBC-Datenquelle eine Verbindung hinzufügen.  
  
 Weitere Informationen zum ODBC-Verbindungs-Manager finden Sie unter [ODBC Connection Manager](../../integration-services/connection-manager/odbc-connection-manager.md).  
  
### <a name="options"></a>enthalten  
 **Datenverbindungen**  
 Wählen Sie in der Liste einen vorhandenen ODBC-Verbindungs-Manager aus.  
  
 **Datenverbindungseigenschaften**  
 Zeigen Sie Eigenschaften und Werte für den ausgewählten ODBC-Verbindungs-Manager an.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Verbindungs-Manager** einen ODBC-Verbindungs-Manager. In diesem Dialogfeld können Sie bei Bedarf auch eine neue ODBC-Datenquelle erstellen.  
  
 **Löschen**  
 Wählen Sie eine Verbindung aus, und löschen Sie sie mithilfe der Schaltfläche **Löschen** .  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Verbindungen &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
