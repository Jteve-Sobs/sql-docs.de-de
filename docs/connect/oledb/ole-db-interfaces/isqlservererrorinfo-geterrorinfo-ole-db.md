---
title: 'ISQLServerErrorInfo:: GetErrorInfo (OLE DB) | Microsoft-Dokumentation'
description: "'ISQLServerErrorInfo::GetErrorInfo' (OLE DB)"
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
apitype: COM
helpviewer_keywords:
- GetErrorInfo method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 22424e6c8cac92ec0bada0ed3dab13e9b6938c14
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600500"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>'ISQLServerErrorInfo::GetErrorInfo' (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Gibt einen Zeiger auf eine OLE DB-Treiber für SQL Server-SSERRORINFO, die Struktur enthält die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Fehlerdetails.  
  
 Der OLE DB-Treiber für SQL Server definiert die **ISQLServerErrorInfo** fehlerschnittstelle. Diese Schnittstelle gibt Details zu einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehler zurück, einschließlich seines Schweregrads und Status.  

  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT GetErrorInfo(  
   SSERRORINFO**ppSSErrorInfo,  
   OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>Argumente  
 *ppSSErrorInfo*[out]  
 Ein Zeiger auf eine SSERRORINFO-Struktur. Wenn die Methode fehlschlägt oder dem Fehler keine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Informationen zugeordnet sind, teilt der Anbieter keinen Speicher zu und stellt sicher, dass das *ppSSErrorInfo* -Argument bei der Ausgabe ein NULL-Zeiger ist.  
  
 *ppErrorStrings*[out]  
 Ein Zeiger auf einen Unicode-Zeichenfolgenzeiger. Wenn die Methode fehlschlägt oder dem Fehler keine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Informationen zugeordnet sind, teilt der Anbieter keinen Speicher zu und stellt sicher, dass das *ppErrorStrings* -Argument bei der Ausgabe ein NULL-Zeiger ist. Durch die Freigabe des *ppErrorStrings* -Arguments mit der **IMalloc::Free** -Methode werden die drei einzelnen Zeichenfolgenelemente der zurückgegebenen SSERRORINFO-Struktur freigegeben, da der Speicher in einem Block zugeteilt wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 S_OK  
 Die Methode wurde erfolgreich ausgeführt.  
  
 E_INVALIDARG  
 Entweder das *ppSSErrorInfo* -Argument oder das *ppErrorStrings* -Argument war NULL.  
  
 E_OUTOFMEMORY  
 Der OLE DB-Treiber für SQL Server konnte nicht genügend Arbeitsspeicher zum Ausführen der Anforderung zuordnen.  
  
## <a name="remarks"></a>Remarks  
 Der OLE DB Driver for SQL Server teilt Arbeitsspeicher für die SSERRORINFO- und die OLECHAR-Zeichenfolgen zu, die durch die Zeiger zurückgegeben werden, die vom Consumer übergeben werden. Der Consumer muss diesen Arbeitsspeicher mithilfe der **IMalloc::Free** -Methode freigeben, wenn er keinen Zugriff auf die Fehlerdaten mehr benötigt.  
  
 Die SSERRORINFO-Struktur ist folgendermaßen definiert:  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|Member|Beschreibung|  
|------------|-----------------|  
|*pwszMessage*|Die Fehlermeldung aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Die Meldung wird durch die **IErrorInfo::GetDescription** -Methode zurückgegeben.|  
|*pwszServer*|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], auf der der Fehler aufgetreten ist|  
|*pwszProcedure*|Der Name der gespeicherten Prozedur, die den Fehler generiert, wenn der Fehler in einer gespeicherten Prozedur aufgetreten ist; anderenfalls ist es eine leere Zeichenfolge.|  
|*lNative*|Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Fehlernummer. Die Fehlernummer ist mit der im *plNativeError* -Parameter der **ISQLErrorInfo::GetSQLInfo** -Methode zurückgegebenen identisch.|  
|*bState*|Der Zustand des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Fehlers.|  
|*bClass*|Der Schweregrad des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Fehlers.|  
|*wLineNumber*|Das ist gegebenenfalls die Zeile einer gespeicherten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozedur, die die Fehlermeldung generiert hat. Wenn keine Prozedur betroffen ist, lautet der Standardwert 1.|  
  
 Zeiger auf die Strukturverweisadressen in der Zeichenfolge, die im *ppErrorStrings* -Argument zurückgegeben wird  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [ISQLServerErrorInfo &#40;OLE-DB&#41;](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)   
 [RAISERROR &#40;Transact-SQL&#41;](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  
