---
description: FilterCriterion-Eigenschaft (RDS)
title: Filterkriterium-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterCriterion property [RDS]
ms.assetid: 24eb03ba-ccfd-4353-b6af-03586b2da6fd
author: rothja
ms.author: jroth
ms.openlocfilehash: b1e2c46549f680e248d5734efa58d949d83f3800
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438992"
---
# <a name="filtercriterion-property-rds"></a>FilterCriterion-Eigenschaft (RDS)
Gibt den Auswertungs Operator an, der im Filter Wert verwendet werden soll.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.FilterCriterion = String  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) -Objekt.  
  
 *String*  
 Ein **Zeichen** folgen Wert, der den Auswertungs Operator des [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md) zu den Datensätzen angibt. Kann eine der folgenden sein: <, \<=, > , >=, = oder <>.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), **Filterkriterium**und [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md) stellen Sortier-und Filterfunktionen für den Client seitigen Cache bereit. Die Sortierfunktion ordnet Datensätze nach Werten aus einer Spalte an. Die Filterfunktion zeigt eine Teilmenge der Datensätze basierend auf den Suchkriterien an, während das vollständige [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) im Cache beibehalten wird. Die [Reset](../../../ado/reference/rds-api/reset-method-rds.md) -Methode führt die Kriterien aus und ersetzt das aktuelle **Recordset** durch ein Aktualisier bares **Recordset**.  
  
 Der Operator "! =" ist für **Filterkriterium**ungültig. Verwenden Sie stattdessen "<>".  
  
 Wenn die Filter-und Sortierungs Eigenschaften festgelegt sind und Sie die **Reset** -Methode aufzurufen, wird das Rowset zuerst gefiltert und dann sortiert. Bei aufsteigenden Sortierungen sind die NULL-Werte ganz oben. bei absteigenden Sortierungen befinden sich NULL-Werte unten (aufsteigend ist Standardverhalten).  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filter Column, Filterkriterium, FilterValue, SortColumn und SortDirection Properties und Reset Method example (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [FilterColumn-Eigenschaft (RDS)](../../../ado/reference/rds-api/filtercolumn-property-rds.md)   
 [FilterValue-Eigenschaft (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [SortColumn-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


