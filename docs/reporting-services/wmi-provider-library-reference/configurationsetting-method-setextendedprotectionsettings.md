---
title: 'SetExtendedProtectionSettings-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cbfd4392572713e1c81fef07467842e18549e089
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65581016"
---
# <a name="configurationsetting-method---setextendedprotectionsettings"></a>ConfigurationSetting-Methode: SetExtendedProtectionSettings
  Die SetExtendedProtectionSettings-Methode wird verwendet, um die RSWindowsExtendedProtectionLevel- und RSWindowsExtendedProtectionScenario-Eigenschaft in der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsdatei "RSReportServer.config" festzulegen.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *ExtendedProtectionLevel*  
 Legt "RSWindowsExtendedProtectionLevel" in der Datei "RSRreportserver.config" fest. Beim erforderlichen Wert wird die Groß-/Kleinschreibung nicht beachtet.  
  
 In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `"Off | Allow | Require"`  
  
 *ExtendedProtectionScenario*  
 Legt "RSWindowsExtendedProtectionScenario" in der Datei "RSReportserver.config" fest. Beim erforderlichen Wert wird die Groß-/Kleinschreibung nicht beachtet.  
  
 In der folgenden Liste werden gültige Werte aufgeführt:  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a>Remarks  
 Die RSWindowsExtendedProtectionLevel-Eigenschaft und die RSWindowsExtendedProtectionScenario-Eigenschaft sind gültig, wenn AuthenticationTypes in der Datei RSReportServer.config RSWindowNTLM, RSWindowsNegotiate oder RSWindowsKerberos einschließt. Das Festlegen dieser Eigenschaften wirkt sich darauf aus, wie sich Benutzer und Clientsoftware an einem Berichtsserver authentifizieren. Es wird empfohlen, dass Sie die Dokumentation für erweiterten Schutz vor dem Festlegen von ExtendedProtectionLevel auf **Allow** oder **Require**lesen.  
  
 Zum Festlegen von ExtendedProtectionLevel muss der Benutzer Mitglied der Gruppe "BUILTIN\Administrators" auf dem Berichtsserver sein.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [RSWindowsExtendedProtectionScenario-Eigenschaft &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [RSWindowsExtendedProtectionLevel-Eigenschaft &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Erweiterter Schutz für die Authentifizierung mit Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer.config-Konfigurationsdatei](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
