---
title: Implementierungsanforderungen für benutzerdefinierte Berichtselemente | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3e90b19178bc62d0c6ef51a740ab86244709a948
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63194315"
---
# <a name="custom-report-item-implementation-requirements"></a>Implementierungsanforderungen für benutzerdefinierte Berichtselemente
  In diesem Thema werden die Voraussetzungen zur Entwicklung und Bereitstellung von benutzerdefinierten Berichtselementen erläutert.  
  
## <a name="development-and-deployment-requirements"></a>Entwicklungs- und Bereitstellungsanforderungen  
 Die Entwicklung eines benutzerdefinierten Berichtselements für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erfordert Folgendes:  
  
-   Administratorzugriff auf einen Server, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ausgeführt wird.  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)] oder höher, auf dem das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) installiert ist.  
  
-   Zugriff auf die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK-Dokumentation.  
  
-   Kenntnisse über die Komponentenerstellung und die Komponentenmodell-Namespaces in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Weitere Informationen finden Sie in "Erstellen von Komponenten" und "Namespaces für Komponentenmodelle in Visual Studio" auf msdn.microsoft.com.  
  
## <a name="language-and-namespace-requirements"></a>Sprach- und Namespace-Anforderungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Berichtselemente unterstützen [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] vollständig. Sie können benutzerdefinierte Berichtselemente mithilfe einer Auswahl .NET-konformer Sprachen entwickeln.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] enthält viele Tools und Funktionen für Entwickler, die die iterativen Zyklen, bestehend aus Codierung, Debugging und Testen, sowie die Bereitstellung vereinfachen und beschleunigen. Das [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK enthält [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] und C#-Compiler sowie zugehörige Tools.  
  
-   Benutzerdefinierte Berichtselemente verwenden **Microsoft.ReportDesigner** und <xref:Microsoft.ReportingServices.Interfaces>-Namespaces. Diese werden in den Assemblys „Microsoft.ReportingServices.Designer.DLL“ und „Microsoft.ReportingServices.Interfaces.DLL“ gespeichert, die als Teil von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert werden.  
  
-   Benutzerdefinierte Berichtselement-Entwurfszeitkomponenten müssen Schnittstellen des <xref:System.ComponentModel>-Namespace in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] implementieren. <xref:System.ComponentModel> ist in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK-Dokumentation dokumentiert.  
  
> [!IMPORTANT]  
>  Standardmäßg wird [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert, das [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -SDK jedoch nicht. Die in diesem Abschnitt vorkommenden Links auf SDK-Inhalte funktionieren nur, wenn das SDK auf Ihrem Computer installiert und die SDK-Dokumentation in der Onlinedokumentation enthalten ist. Fügen Sie das SDK nach der Installation des [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK zur Onlinedokumentation und dem Inhaltsverzeichnis hinzu, indem Sie die Anweisungen unter [Hinzufügen oder Entfernen der Produktdokumentation für SQL Server](https://msdn.microsoft.com/library/ef798cc8-87cf-4d60-a7bf-9e061bdd0052) befolgen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Laufzeitkomponente für ein benutzerdefiniertes Berichtselement](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Erstellen einer Entwurfszeitkomponente für ein benutzerdefiniertes Berichtselement](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [How to: Deploy a Custom Report Item (Vorgehensweise: Bereitstellen eines benutzerdefinierten Berichtselements)](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)   
 [Custom Report Item Class Libraries (Klassenbibliotheken für ein benutzerdefiniertes Berichtselement)](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  
