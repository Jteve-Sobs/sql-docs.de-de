---
title: LocalDBGetVersionInfo-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBGetVersionInfo
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d45c83b0a8c7ce0884809c394ea35d21dbc42c75
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52390528"
---
# <a name="localdbgetversioninfo-function"></a>LocalDBGetVersionInfo-Funktion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Gibt Informationen zur angegebenen SQL Server Express-LocalDB-Version zurück, z. B., ob sie vorhanden ist sowie die vollständige LocalDB-Versionsnummer (inklusive Build- und Releasenummer).  
  
 Die Informationen werden zurückgegeben, in der Form einer **Struktur** mit dem Namen **LocalDBVersionInfo**, die weist folgende Definition.  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 **Headerdatei:** sqlncli.h  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a>Parameter  
 *wszVersionName*  
 [Eingabe] Der Name der LocalDB-Version.  
  
 *pVersionInfo*  
 [Ausgabe] Der Puffer zum Speichern der Informationen zur LocalDB-Version.  
  
 *dwVersionInfoSize*  
 [Eingabe] Nimmt die Größe der *VersionInfo* Puffer.  
  
## <a name="returns"></a>Rückgabewert  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-version.md)  
 Die angegebene LocalDB-Version ist nicht vorhanden.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="details"></a>Details  
 Der Grund für die Einführung der **Struktur** -größenargument (*LpVersionInfoSize*) besteht darin, aktivieren die API zum Zurückgeben von verschiedenen Versionen von der **LocalDBVersionInfostruct**effektiv Aufwärts-und Abwärtskompatibilität aktivieren.  
  
 Wenn die **Struktur** -größenargument (*LpVersionInfoSize*) entspricht der Größe einer bekannten Version der **LocalDBVersionInfostruct**, diese Version von der  **Struktur** zurückgegeben wird. Andernfalls wird LOCALDB_ERROR_INVALID_PARAMETER zurückgegeben.  
  
 Ein typisches Beispiel **LocalDBGetVersionInfo** API-Verwendung sieht folgendermaßen aus:  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Hinweise  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Express LocalDB-Header und -Versionsinformationen](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
