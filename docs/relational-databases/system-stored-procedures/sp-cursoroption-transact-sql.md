---
title: Sp_cursoroption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursoroption_TSQL
- sp_cursoroption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursoroption
ms.assetid: 88fc1dba-f4cb-47c0-92c2-bf398f4a382e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a686f78ea5dff8a3ea551016d9fbe9c9046b110
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52545503"
---
# <a name="spcursoroption-transact-sql"></a>sp_cursoroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt Cursoroptionen fest oder gibt die von der Prozedur Sp_cursoropen gespeicherten erstellte cursorinformationen zurück. Sp_cursoroption wird aufgerufen, indem ID = 8 in einem tabular Data Stream (TDS)-Paket.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursoroption cursor, code, value  
```  
  
## <a name="arguments"></a>Argumente  
 *Cursor*  
 Ist eine *behandeln* -Wert, der vom generierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zurückgegeben, die von der Prozedur Sp_cursoropen gespeichert. *Cursor* erfordert eine **Int** -Eingabewert zur Ausführung.  
  
 *Code*  
 Wird verwendet, um verschiedene Faktoren der Cursorrückgabewerte festzulegen. *Code* erfordert eine der folgenden **Int** Eingabewerte:  
  
|Wert|Name|Description|  
|-----------|----------|-----------------|  
|0x0001|TEXTPTR_ONLY|Gibt für bestimmte angegebene Text- oder Bildspalten den Textzeiger, nicht aber die tatsächlichen Daten zurück.<br /><br /> TEXTPTR_ONLY ermöglicht Textzeiger als vorgesehen *Handles* für Blob-Objekte, die später selektiv abgerufen werden können oder mithilfe von Windows aktualisiert [!INCLUDE[tsql](../../includes/tsql-md.md)] oder DBLIB-Funktionen (z.B.) [!INCLUDE[tsql](../../includes/tsql-md.md)] READTEXT oder DBLIB DBWRITETEXT).<br /><br /> Wenn der Wert "0" zugewiesen wird, geben alle Text- und Bildspalten in der Auswahlliste Textzeiger anstelle von Daten zurück.|  
|0x0002|CURSOR_NAME|Weist den Namen im angegebenen *Wert* bis zum Cursor. Dies ermöglicht wiederum ODBC verwenden [!INCLUDE[tsql](../../includes/tsql-md.md)] positionierte UPDATE/DELETE-Anweisungen für Cursor, die mithilfe von Sp_cursoropen geöffnet.<br /><br /> Die Zeichenfolge kann als beliebiges Zeichen oder Unicode-Datentyp angegeben werden.<br /><br /> Da [!INCLUDE[tsql](../../includes/tsql-md.md)] positionierte UPDATE/DELETE-Anweisungen ausgeführt werden, standardmäßig auf die erste Zeile in einem fat Cursor Sp_cursor SETPOSITION zur Positionierung des Cursors, bevor die positionierte UPDATE/DELETE-Anweisung ausgegeben verwendet werden soll.|  
|0x0003|TEXTDATA|Gibt für bestimmte Text- oder Bildspalten in nachfolgenden Abrufvorgängen die tatsächlichen Daten und nicht den Textzeiger zurück (d. h., der Effekt von TEXTPTR_ONLY wird aufgehoben).<br /><br /> Wenn TEXTDATA für eine bestimmte Spalte aktiviert ist, wird die Zeile erneut abgerufen oder aktualisiert und kann dann auf TEXTPTR_ONLY zurückgesetzt werden. Wie bei TEXTPTR_ONLY ist der Wertparameter eine ganze Zahl, die die Spaltennummer angibt; beim Wert 0 (null) werden alle Text- oder Bildspalten zurückgegeben.|  
|0x0004|SCROLLOPT|Option für den Bildlauf. Weitere Informationen finden Sie weiter unten in diesem Thema unter "Rückgabecodewerte".|  
|0x0005|CCOPT|Option für die Parallelitätssteuerung. Weitere Informationen finden Sie weiter unten in diesem Thema unter "Rückgabecodewerte".|  
|0x0006|ROWCOUNT|Die Anzahl der aktuell im Resultset enthaltenen Zeilen.<br /><br /> Hinweis: Wenn die asynchrone Auffüllung verwendet wird, hat sich der ROWCOUNT-Wert möglicherweise geändert, seit der Wert von sp_cursoropen zurückgegeben wurde. Der Wert-1 wird zurückgegeben, wenn die Anzahl der Zeilen unbekannt ist.|  
  
 *value*  
 Legt den Rückgabewert von *Code*. *Wert* ist ein erforderlicher Parameter, der 0 x 0001, 0 x 0002 oder 0 x 0003 erfordert *Code* Eingabewert.  
  
> [!NOTE]  
>  Ein *Code* Wert 2 ein Zeichenfolgendatentyp ist. Alle anderen *Code* Wert eingegebene oder zurückgegebene *Wert* ist eine ganze Zahl.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die *Wert* Parameter kann einen der folgenden zurückgeben *Code* Werte.  
  
|Rückgabewert|Description|  
|------------------|-----------------|  
|0x0004|SCROLLOPT|  
|0X0005|CCOPT|  
|0X0006|ROWCOUNT|  
  
 Die *Wert* -Parameter gibt einen der folgenden SCROLLOPT-Werte zurück.  
  
|Rückgabewert|Description|  
|------------------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
  
 Die *Wert* -Parameter gibt einen der folgenden CCOPT-Werte zurück.  
  
|Rückgabewert|Description|  
|------------------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS|  
|0x0004 oder 0x0008|OPTIMISTIC|  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Sp_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-transact-sql.md)   
 [Sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)  
  
  
