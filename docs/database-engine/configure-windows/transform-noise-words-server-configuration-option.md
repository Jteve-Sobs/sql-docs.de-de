---
title: Füllwörtertransformation (Serverkonfigurationsoption) | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Option „Füllwörter transformieren“. Sie erfahren, wie diese Option in einigen Volltextabfragen in SQL Server genutzt werden kann, die Füllwörter (Stoppwörter) enthalten.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- full-text queries [SQL Server], performance
- transform noise words option
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 69bd388e-a86c-4de4-b5d5-d093424d9c57
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 401637b4c23ddbcd2918f4d0d3cf5ff224bea8cc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85763970"
---
# <a name="transform-noise-words-server-configuration-option"></a>Füllwörtertransformation (Serverkonfigurationsoption)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Verwenden Sie Serverkonfigurationsoption **Füllwörtertransformation** (Transform Noise Words), um eine Fehlermeldung zu unterdrücken, wenn durch Füllwörter, bei denen es sich um [Stoppwörter](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)handelt, verursacht wird, dass ein boolescher Vorgang für eine Volltextabfrage 0 Zeilen zurückgibt. Diese Option ist für Volltextabfragen nützlich, bei denen das CONTAINS-Prädikat verwendet wird, in dem boolesche oder NEAR-Operationen Füllwörter enthalten. Eine Beschreibung der möglichen Werte finden Sie in der folgenden Tabelle:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0|Füllwörter (oder Stoppwörter) werden nicht umgewandelt. Wenn eine Volltextabfrage Füllwörter enthält, gibt die Abfrage 0 Zeilen zurück und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] löst eine Warnung aus. Dies ist das Standardverhalten.<br /><br /> Hinweis: Bei der Warnung handelt es sich um eine Laufzeitwarnung. Die Warnung wird daher nicht ausgegeben, wenn die Volltextklausel in der Abfrage nicht ausgeführt wird. Bei lokalen Abfragen wird auch bei mehreren Volltextabfrageklauseln immer nur eine einzige Warnung ausgegeben. Bei Remoteabfragen übermittelt der Verbindungsserver u. U. den Fehler nicht, und die Warnung wird daher möglicherweise nicht ausgegeben.|  
|1|Füllwörter (oder Stoppwörter) werden umgewandelt. Sie werden ignoriert, und der Rest der Abfrage wird ausgewertet.<br /><br /> Wenn Füllwörter in einem NEAR-Begriff angegeben werden, werden sie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt. Das Füllwort `is` wird beispielsweise aus `CONTAINS(<column_name>, 'NEAR (hello,is,goodbye)')`entfernt, und die Suchabfrage wird in `CONTAINS(<column_name>, 'NEAR(hello,goodbye)')`umgewandelt. Beachten Sie, dass `CONTAINS(<column_name>, 'NEAR(hello,is)')` einfach in `CONTAINS(<column_name>, hello)` umgewandelt werden würde, da es nur einen gültigen Suchbegriff gibt.|  
  
## <a name="effects-of-the-transform-noise-words-setting"></a>Auswirkungen der Einstellung von „Füllwörtertransformation“  
 In diesem Abschnitt wird das Verhalten von Abfragen, die das Füllwort „`the`“ enthalten, unter den alternativen Einstellungen von **Füllwörtertransformation**dargestellt.  Für die Beispielzeichenfolgen für Volltextabfragen wird angenommen, dass sie in einer Tabellenzeile mit den folgenden Daten ausgeführt werden: `[1, "The black cat"]`.  
  
> [!NOTE]  
>  Alle derartigen Szenarien können eine Füllwortwarnung generieren.  
  
-   Mit „Füllwörtertransformation“ auf „0“ festgelegt:  
  
    |Abfragezeichenfolge|Ergebnis|  
    |------------------|------------|  
    |"`cat`" AND "`the`"|Keine Ergebnisse (das Verhalten ist für "`the`" AND "`cat`" genau gleich.)|  
    |"`cat`" NEAR "`the`"|Keine Ergebnisse (das Verhalten ist für "`the`" NEAR "`cat`" genau gleich.)|  
    |"`the`" AND NOT "`black`"|Keine Ergebnisse|  
    |"`black`" AND NOT "`the`"|Keine Ergebnisse|  
  
-   Mit „Füllwörtertransformation“ auf „1“ festgelegt:  
  
    |Abfragezeichenfolge|Ergebnis|  
    |------------------|------------|  
    |"`cat`" AND "`the`"|Treffer für Zeile mit ID 1|  
    |"`cat`" NEAR "`the`"|Treffer für Zeile mit ID 1|  
    |"`the`" AND NOT "`black`"|Keine Ergebnisse|  
    |"`black`" AND NOT "`the`"|Treffer für Zeile mit ID 1|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird **Füllwörtertransformation** auf `1`festgelegt.  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
GO  
sp_configure 'transform noise words', 1;  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [CONTAINS &#40;Transact-SQL&#41;](../../t-sql/queries/contains-transact-sql.md)  
  
  
