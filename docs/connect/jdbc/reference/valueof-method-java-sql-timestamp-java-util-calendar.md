---
title: valueOf-Methode (java.sql.Timestamp, java.util.Calendar) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea08f3b58894ff269972dc2348d71fb2d589959c
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52398195"
---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>valueOf-Methode (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt ein **DateTimeOffset**-Objekt, das einen Zeitpunkt in einem bestimmten Offset von GMT darstellt, wenn ein java.sql.Timestamp-Wert sowie ein den Offset angegebener java.util.Calendar-Wert gegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Parameter  
 *timestamp*  
  
 Einjava.sql.Timestamp-Wert.  
  
 *calendar*  
  
 Der Offsetwert.  Die Komponenten für Datum und Uhrzeit der *Kalender* werden entsprechend festgelegt werden die *Zeitstempel* Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein DateTimeOffset-Objekt, den Zeitpunkt in erhalten vom java.sql.Timestamp-Objekt des Objekts angegebenen java.util.Calendar Zeitzone darstellt.  
  
## <a name="remarks"></a>Remarks  
 Diese Methode wird auch das java.util.Calendar-Objekt zu dem Punkt vom java.sql.Timestamp-Objekt gegebenen Zeitpunkt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset-Elemente](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
