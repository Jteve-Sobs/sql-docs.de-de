---
title: Banner-Element (ssbdiagnose) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 202652271b9d8de9603706b9d1c7be8ca9411bb7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986207"
---
# <a name="banner-element-ssbdiagnose"></a>Banner-Element (ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Identifiziert das Hilfsprogramm, das die XML-Ausgabedatei von **ssbdiagnose** generiert hat.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|und Beschreibung|  
|---------------|-----------------|  
|**title**|Identifiziert das Hilfsprogramm, das die XML-Ausgabedatei von **ssbdiagnose** generiert hat.|  
|**product**|Identifiziert das Produkt, das die XML-Ausgabedatei von **ssbdiagnose** generiert hat.|  
|**version**|Identifiziert die Version des Hilfsprogramms, das die XML-Ausgabedatei generiert hat.|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|und Beschreibung|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmal pro XML-Ausgabedatei von **ssbdiagnose**|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[DiagnosticInformation-Element &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**Untergeordnete Elemente**|Keine.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein Banner-Element.  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ssbdiagnose-Hilfsprogramm &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
