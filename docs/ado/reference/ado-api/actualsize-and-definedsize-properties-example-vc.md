---
title: ActualSize und DefinedSize – Beispiel (VC++) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActualSize property [ADO], VC++ example
- DefinedSize property [ADO], VC++ example
ms.assetid: 05f7cc97-b806-41d2-939d-a955d10844c4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6597d6a834771872abab75d9be3fbf3127eca539
ms.sourcegitcommit: fc341b2e08937fdd07ea5f4d74a90677fcdac354
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66718265"
---
# <a name="actualsize-and-definedsize-properties-example-vc"></a>ActualSize und DefinedSize – Beispiel (VC++)
Dieses Beispiel verwendet die [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md) und [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) Eigenschaften, die die definierte Größe und die tatsächliche Größe eines Felds angezeigt.  
  
## <a name="example"></a>Beispiel  
  
```  
// BeginActualSizeCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include "conio.h"   
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void ActualSizeX();  
void PrintProviderError(_ConnectionPtr pConnection);  
  
int main() {  
   if (FAILED(::CoInitialize(NULL)))  
      return -1;  
   ActualSizeX();  
   ::CoUninitialize();  
}  
  
void ActualSizeX() {  
   HRESULT hr = S_OK;  
  
   // Define ADO object pointers. Initialize pointers on define.  
   // These are in the ADODB::  namespace.  
   _RecordsetPtr pRstStores = NULL;  
  
   // Define Other variables  
   _bstr_t strMessage;  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      // Open a recordset for the stores table.  
      TESTHR(pRstStores.CreateInstance(__uuidof(Recordset)));  
  
      // You have to explicitly pass the Cursor type and LockType to the Recordset here.  
      hr = pRstStores->Open("stores", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);  
  
      // Loop through the recordset displaying the contents of the stor_name field,   
      // the field's defined size, and its actual size.  
      pRstStores->MoveFirst();  
  
      while (!(pRstStores->EndOfFile)) {  
         strMessage = "Store Name: ";  
         strMessage += (_bstr_t)pRstStores->Fields->Item["stor_name"]->Value + "\n";  
         strMessage += "Defined Size: ";   
         strMessage += (_bstr_t)pRstStores->Fields->Item["stor_name"]->DefinedSize + "\n";  
         strMessage += "Actual Size: ";  
         strMessage += (_bstr_t) pRstStores->Fields->Item["stor_name"]->ActualSize + "\n";   
  
         printf("%s\n",(LPCSTR)strMessage);  
         pRstStores->MoveNext();  
      }  
   }  
   catch(_com_error &e) {  
      _variant_t vtConnect = pRstStores->GetActiveConnection();  
  
      // GetActiveConnection returns connect string if connection  
      // is not open, else returns Connection object.  
      switch(vtConnect.vt) {  
         case VT_BSTR:  
            printf("Error:\n");  
            printf("Code = %08lx\n", e.Error());  
            printf("Message = %s\n", e.ErrorMessage());  
            printf("Source = %s\n", (LPCSTR) e.Source());  
            printf("Description = %s\n", (LPCSTR) e.Description());  
            break;  
         case VT_DISPATCH:  
            PrintProviderError(vtConnect);  
            break;  
         default:  
            printf("Errors occured.");  
            break;  
      }  
   }  
  
   // Clean up objects before exit.  
   if (pRstStores)  
      if (pRstStores->State == adStateOpen)  
         pRstStores->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
   long nCount = 0;      
   long i = 0;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for (i = 0 ; i < nCount ; i++) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("\t Error number: %x\t%s", pErr->Number,(LPCSTR ) pErr->Description);  
      }  
   }  
}  
```  
  
 **Store-Name: Eric Bücher lesen**  
**Definierte Größe: 40**  
**Tatsächliche Größe: 19**  
**Store-Name: Barnum's**  
**Definierte Größe: 40**  
**Tatsächliche Größe: 8**  
**Store-Name: Nachrichten & Brews**  
**Definierte Größe: 40**  
**Tatsächliche Größe: 12**  
**Store-Name: Doc-U-Mat: Qualität Wäsche und Büchern**  
**Definierte Größe: 40**  
**Tatsächliche Größe: 36**  
**Store-Name: Fricative Bookshop**  
**Definierte Größe: 40**  
**Tatsächliche Größe: 18**  
**Store-Name: Bookbeat**  
**Definierte Größe: 40**  
**Tatsächliche Größe: 8**   
## <a name="see-also"></a>Siehe auch  
 [ActualSize-Eigenschaft (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)   
 [DefinedSize-Eigenschaft](../../../ado/reference/ado-api/definedsize-property.md)
