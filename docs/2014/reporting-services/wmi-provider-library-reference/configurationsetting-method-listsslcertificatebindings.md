---
title: 'ListSSLCertificateBindings-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b8505017ca0b279a6cc1d7782bff66b120d2851
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59940346"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserverconfigurationsetting"></a>ListSSLCertificateBindings-Methode (WMI: MSReportServer_ConfigurationSetting)
  Gibt eine Liste von auf dem Computer installierten SSL-Zertifikaten zurück  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *LCID*  
 Das Gebietsschema, das für die zurückgegebenen Fehlermeldungen verwendet werden soll  
  
 *Application[]*  
 [out] Die Anwendungen, die Zertifikatsbindungen aufweisen  
  
 *CertificateHash[]*  
 [out] Die Hashes für die Zertifikate  
  
 *IPAddress[]*  
 [out] Die IP-Adresse für die Anwendungen  
  
 *Port[]*  
 [out] Die in der Bindung in rsreportserver.config gespeicherte Portnummer.  
  
 *Errors[]*  
 [out] Die Beschreibungen für Fehler, die aufgetreten sind  
  
 *Länge*  
 [out] Die Länge des von der Methode zurückgegebenen Arrays  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
