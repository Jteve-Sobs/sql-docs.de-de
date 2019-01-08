---
title: 'RestoreEncryptionKey-Methode (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: acdd99c590f05fbe21777416dcd56234a6a797d0
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52417441"
---
# <a name="restoreencryptionkey-method-wmi-msreportserverconfigurationsetting"></a>RestoreEncryptionKey-Methode (WMI: MSReportServer_ConfigurationSetting)
  Wendet den angegebenen Verschlüsselungsschlüssel erneut auf die Berichtsserver-Datenbank an  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parameter  
 *KeyFile[]*  
 [out] Ein Array, das den verschlüsselten Verschlüsselungsschlüssel enthält  
  
 *Länge*  
 [out] Die Länge des von der Methode zurückgegebenen Arrays  
  
 *Kennwort*  
 Eine Zeichenfolge, die zum Verschlüsseln des Verschlüsselungsschlüssels verwendet wird  
  
 *HRESULT*  
 [out] Wert, der angibt, ob der Aufruf erfolgreich war oder zu einem Fehler geführt hat.  
  
 *ExtendedErrors[]*  
 [out] Ein Zeichenfolgenarray, das zusätzliche Fehler enthält, die durch den Aufruf zurückgegeben werden  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt *HRESULT* zurück, wodurch der Erfolg oder das Fehlschlagen des Methodenaufrufs angegeben wird. Der Wert 0 (null) gibt an, dass der Methodenaufruf erfolgreich war. Ein Wert ungleich 0 (null) gibt an, dass ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Wenn bereits ein Eintrag für den Berichtsserver in der Berichtsserver-Datenbank vorhanden ist, wird dieser gelöscht. Der neue Eintrag wird dann mit dem angegebenen Verschlüsselungsschlüssel und dem öffentlichen Schlüssel des Berichtsservers erstellt.  
  
 Diese Methode ist am effektivsten, wenn sie nach der [DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md) -Methode aufgerufen wird, die die Liste der Verschlüsselungsschlüssel löscht.  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
