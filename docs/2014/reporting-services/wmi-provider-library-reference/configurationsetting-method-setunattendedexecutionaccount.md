---
title: 'SetUnattendedExecutionAccount-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 095929c60d586fa0ed6c857412a369171acdaa10
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097925"
---
# <a name="setunattendedexecutionaccount-method-wmi-msreportserver_configurationsetting"></a>SetUnattendedExecutionAccount-Methode (WMI: MSReportServer_ConfigurationSetting)
  Gibt das Konto an, das verwendet wird, um Berichte unbeaufsichtigt auszuführen  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parameter  
 *User*  
 Ein Windows-Konto, das für die unbeaufsichtigte Ausführung verwendet werden soll  
  
 *Kennwort*  
 Das Kennwort für das angegebene Konto  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Methode „SetUnattendedExecutionAccount“ überprüft nicht, ob sich der Berichtsserver als der angegebene Benutzer anmelden kann.  
  
 Die Methode „SetUnattendedExecutionAccount“ kann nicht für die unbeaufsichtigte Ausführung im Kontext des Report Server-Windows-Diensts verwendet werden.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting Members (MSReportServer_ConfigurationSetting-Member)](msreportserver-configurationsetting-members.md)  
  
  
