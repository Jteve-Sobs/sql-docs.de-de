---
title: Volltextsuche und semantische Suche Katalogsichten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- catalog views [SQL Server], full-text search
- full-text search [SQL Server], catalog views
- full-text indexes [SQL Server], catalog views
ms.assetid: b08ad2fd-e3d8-458f-96f1-678217e0f419
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 2183619c0519bd170a54a0a15450d45c062d96af
ms.sourcegitcommit: 04c031f7411aa33e2174be11dfced7feca8fbcda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945581"
---
# <a name="full-text-search-and-semantic-search-catalog-views-transact-sql"></a>Katalogsichten für Volltextsuche und semantische Suche (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In diesem Abschnitt werden die Katalogsichten beschrieben, die Informationen zu Volltextindizes und semantischen Indizes bereitstellen.  
  
## <a name="full-text-search-catalog-views"></a>Katalogsichten für die Volltextsuche  
 [sys.fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)  
 Enthält eine Zeile für jeden Volltextkatalog.  
  
 [sys.fulltext_document_types](../../relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql.md)  
 Gibt eine Zeile für jeden für Volltextindizierungen verfügbaren Dokumenttyp zurück. Jede Zeile stellt die **IFilter** -Schnittstelle, die in der Instanz von SQL Server registriert ist.  
  
 [sys.fulltext_index_catalog_usages](../../relational-databases/system-catalog-views/sys-fulltext-index-catalog-usages-transact-sql.md)  
 Gibt eine Zeile für jeden Verweis zwischen Volltextkatalog und Volltextindex zurück.  
  
 [sys.fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md)  
 Enthält eine Zeile für jede Spalte, die Teil eines Volltextindexes ist.  
  
 [sys.fulltext_index_fragments](../../relational-databases/system-catalog-views/sys-fulltext-index-fragments-transact-sql.md)  
 Enthält jeweils eine Zeile für jedes Volltextindexfragment einer Tabelle, die einen Volltextindex enthält.  
  
 [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)  
 Enthält eine Zeile pro Volltextindex eines Tabellenobjekts.  
  
 [sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)  
 Enthält eine Zeile pro Sprache, deren Wörtertrennungen bei SQL Server registriert sind. Jede Zeile zeigt die LCID und den Namen der Sprache an.  
  
 [sys.fulltext_stoplists](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)  
 Enthält eine Zeile für jede Volltext-Stoppliste in der Datenbank.  
  
 [sys.fulltext_stopwords](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
 Enthält eine Zeile pro Stoppwort für alle Stopplisten in der Datenbank.  
  
 [sys.fulltext_system_stopwords](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)  
 Bietet Zugriff auf die Systemstoppliste.  
  
 [sys.registered_search_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-properties-transact-sql.md)  
 Enthält eine Zeile für jede Sucheigenschaft in einer Sucheigenschaftenliste der aktuellen Datenbank.  
  
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)  
 Enthält eine Zeile für jede Sucheigenschaftenliste in der aktuellen Datenbank.  
  
## <a name="semantic-search-catalog-views"></a>Katalogsichten für die semantische Suche  
 [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)  
 Gibt eine Zeile zur semantischen Sprachstatistikdatenbank zurück, die in der aktuellen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert ist.  
  
 [sys.fulltext_semantic_languages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md)  
 Gibt eine Zeile für jede Sprache zurück, deren Statistikmodell für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert ist. Wenn ein Sprachenmodell registriert ist, wird diese Sprache für die semantische Indizierung aktiviert.  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Volltextsuche und semantische Suche, dynamische Verwaltungssichten und Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
