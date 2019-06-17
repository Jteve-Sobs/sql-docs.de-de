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
manager: jroth
ms.openlocfilehash: 3e2d977647153ab74299a6b6f002ec33d3003558
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802537"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset-Elemente](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
