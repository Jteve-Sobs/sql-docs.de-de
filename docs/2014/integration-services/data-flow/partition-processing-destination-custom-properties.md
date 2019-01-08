---
title: Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 599f3af6c579a8e9a217df31386b1e799d922f98
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52771112"
---
# <a name="partition-processing-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung
  Das Ziel für Partitionsverarbeitung verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels für Partitionsverarbeitung. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|Zeichenfolge|Die Verbindungszeichenfolge zu einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt oder einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, wie Fehler aufgrund doppelter Schlüssel behandelt werden soll. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|KeyErrorAction|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, wie Schlüsselfehler behandelt werden soll. Die möglichen Werte sind `ConvertToUnknown` (0) und `DiscardRecord` (1). Der Standardwert dieser Eigenschaft ist `ConvertToUnknown` (0).|  
|KeyErrorLimit|Integer|Wenn usedefaultconfiguration `False`, die Obergrenze von Schlüsselfehlern, die zulässig sind.|  
|KeyErrorLimitAction|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, einen Wert an die Aktion beim `KeyErrorLimit` erreicht ist. Die möglichen Werte sind `StopLogging` (1) und `StopProcessing` (0). Der Standardwert dieser Eigenschaft ist `StopProcessing` (0).|  
|KeyErrorLogFile|Zeichenfolge|Wenn usedefaultconfiguration `False`, der Pfad und Dateiname der Fehlerprotokolldatei.|  
|KeyNotFound|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, wie Fehler aufgrund fehlender Schlüssel behandelt werden soll. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `ReportAndContinue` (1).|  
|NullKeyConvertedToUnknown|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, der wie null-Schlüssel behandelt werden sollen, die in den unbekannten Wert konvertiert. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|NullKeyNotAllowed|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, der wie nicht erlaubte Nullwerte behandelt werden sollen. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `ReportAndContinue` (1).|  
|ProcessType|Ganze Zahl (Enumeration)|Der Typ der von der Transformation verwendeten Partitionsverarbeitung. Die möglichen Werte sind `ProcessAdd` (1) (inkrementell), `ProcessFull` (0) und `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Boolean|Ein Wert, der angibt, ob die Transformation die Standardfehlerkonfiguration verwendet. Wenn diese Eigenschaft `False`, verwendet die Transformation die Werte von der benutzerdefinierten Fehlerbehandlungseigenschaften in diese Tabelle einschließlich KeyDuplicate, KeyErrorAction usw. aufgeführt.|  
  
 Die Eingabe und die Eingabespalten des Ziels für Partitionsverarbeitung verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Partition Processing Destination](partition-processing-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Common Properties](../common-properties.md)  
  
  
