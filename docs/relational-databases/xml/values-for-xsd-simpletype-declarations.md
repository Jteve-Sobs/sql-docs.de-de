---
title: Werte für &lt;xsd:simpleType&gt;-Deklarationen | Microsoft-Dokumentation
description: Dieser Artikel enthält eine Tabelle der Einschränkungen, die für alle erkannten Werte der Deklaration <xsd:simpleType> gelten.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:simpleType declarations
ms.assetid: 557b972d-3af9-40bf-8382-72b05c9de1c1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2738ba3387ac167eeadc83071dcce1f4a59304bb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775524"
---
# <a name="values-for-ltxsdsimpletypegt-declarations"></a>Werte für &lt;xsd:simpleType&gt;-Deklarationen
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Die folgende Tabelle führt die Beschränkungen auf, basierend auf allen erkannten XSD-Enumerationen des simple-Datentyps, die angewendet werden.  
  
 Außerdem unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht den NaN-Wert in **\<xsd:simpleType>** -Deklarationen. Schemas, die NaN-Werte enthalten, werden vom Server zurückgewiesen.  
  
|simple-Datentyp|Einschränkung|  
|-----------------|----------------|  
|**duration**|Der Jahresteil muss im Bereich von -2^31 bis 2^31-1 liegen. Monat, Tag, Stunde, Minute und Sekunde müssen alle im Bereich zwischen 0 und 9999 liegen. Der zweite Teil weist eine zusätzliche dreistellige Genauigkeit rechts neben dem Dezimaltrennzeichen auf.|  
|**dateTime**|Die Stundenangabe im Zeitzonen-Unterfeld muss innerhalb des gültigen Bereichs von -14 bis +14 liegen. Die Jahresangabe muss im Bereich zwischen -1 und 9999 liegen. Die Monatsangabe muss im Bereich zwischen 1 und 12 liegen. Die Tagesangabe muss im Bereich zwischen 1 und 31 liegen und ein gültiges kalendarisches Datum sein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkennt z.B. ein ungültiges Datum (wie etwa 1974-02-31) und gibt einen Fehler zurück. Der Monat Februar hat nicht 31 Tage.<br /><br /> Die zweite Komponente unterstützt eine Genauigkeit von 100 Nanosekunden. Das Angeben der Zeitzone ist optional.<br /><br /> SQL Server 2005 unterstützte Jahre im Bereich von -9999 bis 9999. SQL Server unterstützt jetzt einen eingeschränkteren Bereich von Jahren. Weitere Informationen finden Sie unter [Vergleichen von typisiertem XML mit nicht typisiertem XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).|  
|**date**|Die Jahresangabe muss im Bereich zwischen -1 und 9999 liegen. Die Monatsangabe muss im Bereich zwischen 1 und 12 liegen. Die Tagesangabe muss im Bereich zwischen 1 und 31 liegen und ein gültiges kalendarisches Datum sein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkennt z.B. ein ungültiges Datum (wie etwa 1974-02-31) und gibt einen Fehler zurück. Der Monat Februar hat nicht 31 Tage.<br /><br /> SQL Server 2005 unterstützte Jahre im Bereich von -9999 bis 9999. SQL Server unterstützt jetzt einen eingeschränkteren Bereich von Jahren. Weitere Informationen finden Sie unter [Vergleichen von typisiertem XML mit nicht typisiertem XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).|  
|**gYearMonth**|Die Jahresangabe muss im Bereich zwischen -9999 und 9999 liegen.|  
|**gYear**|Die Jahresangabe muss im Bereich zwischen -9999 und 9999 liegen.|  
|**gMonthDay**|Die Monatsangabe muss im Bereich zwischen 1 und 12 liegen. Die Tagesangabe muss im Bereich zwischen 1 und 31 liegen.|  
|**gDay**|Die Tagesangabe muss im Bereich zwischen 1 und 31 liegen.|  
|**gMonth**|Die Monatsangabe muss im Bereich zwischen 1 und 12 liegen.|  
|**decimal**|Werte dieses Typs müssen dem Format des numeric-Datentyps von SQL entsprechen. Dieser Typ stellt intern die Unterstützung für Zahlen dar, die insgesamt bis zu 38-stellig sein können, wobei 10 dieser Dezimalstellen für die Genauigkeit von Bruchteilen reserviert sind.|  
|**float**|Werte dieses Typs müssen dem Format des **real** -Datentyps von SQL entsprechen.|  
|**double**|Werte dieses Typs müssen dem Format des **float** -Datentyps von SQL entsprechen.|  
|**string**|Werte dieses Typs müssen dem Format des Typs **nvarchar(max)** von SQL entsprechen.|  
|**anyURI**|Werte dieses Typs dürfen nicht länger als 4.000 Unicode-Zeichen sein.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anforderungen und Einschränkungen für XML-Schemaauflistungen auf dem Server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
