---
title: SQLPostInstallerError-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a189bd082bbf3d5f08080fccec48334165d5d15c
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53208319"
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLPostInstallerError** bietet einen Mechanismus für eine Treiber oder das Konvertierungsprogramm Setup-Bibliothek, um Fehler in der **ConfigDriver**, **ConfigDSN**, und **ConfigTranslator**  Funktionen in die Fehlerwarteschlange Installer. Anwendungen verwenden diese API nicht. Sie verwenden **SQLInstallerError** um den Fehler abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Argumente  
 *fErrorCode*  
 [Eingabe] Installer-Fehlercode.  
  
 *von SQLDiagRec()*  
 [Eingabe] Text der Fehlermeldung.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS oder SQL_ERROR zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLPostInstallerError** veröffentlichen Fehlerwerte nicht für sich selbst. Wenn der Fehler in die Fehlerwarteschlange Installer wurde erfolgreich gesendet wurde (abrufbar mithilfe **SQLInstallerError**), wird SQL_SUCCESS zurückgegeben. Wird SQL_ERROR zurückgegeben, wenn der Wert in der *DwErrorCode* Argument ist nicht der angegebene Installationsprogramm-Fehlercodes.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Hinzufügen, ändern oder Entfernen von Datenquellen|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Festlegen einer Übersetzungsoption|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
