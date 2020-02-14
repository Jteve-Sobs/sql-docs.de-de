---
title: Datenbankbezeichner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- regular identifiers [SQL Server]
- identifiers [SQL Server]
- names [SQL Server], identifiers
- identifiers [SQL Server], about identifiers
- SQL Server identifiers
- Transact-SQL identifiers
- database objects [SQL Server], names
ms.assetid: 171291bb-f57f-4ad1-8cea-0b092d5d150c
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fbedcb09ba05ff427fbae722a9223d902f2c438d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71271961"
---
# <a name="database-identifiers"></a>Datenbankbezeichner

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Der Name eines Datenbankobjekts wird Bezeichner genannt. Jedes Element in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann über einen Bezeichner verfügen. Hierzu gehören beispielsweise Server, Datenbanken und Datenbankobjekte wie Tabellen, Sichten, Spalten, Indizes, Trigger, Prozeduren, Einschränkungen und Regeln. Bezeichner werden für die meisten Objekte benötigt, sind jedoch bei einigen Objekten, z. B. Einschränkungen, optional.

 Der Bezeichner eines Objekts wird erstellt, wenn das Objekt definiert wird. Der Bezeichner wird anschließend verwendet, um auf das Objekt zu verweisen. So erstellt beispielsweise die folgende Anweisung eine Tabelle mit dem Bezeichner `TableX`und zwei Spalten mit den Bezeichnern `KeyCol` und `Description`:

```sql
CREATE TABLE TableX
(KeyCol INT PRIMARY KEY, Description nvarchar(80))
```

 Die Tabelle enthält außerdem eine unbenannte Einschränkung. Die `PRIMARY KEY` -Einschränkung besitzt keinen Bezeichner.

 Die Sortierung eines Bezeichners hängt von der Ebene ab, auf der er definiert ist. Bezeichnern von Objekten auf Instanzebene, wie z. B. Anmeldenamen und Datenbanknamen, wird die Standardsortierung der Instanz zugewiesen. Bezeichnern von Objekten innerhalb einer Datenbank, z. B. Tabellen, Sichten und Spaltennamen, wird die Standardsortierung der Datenbank zugewiesen. Beispielsweise können in einer Datenbank mit einer nach Groß-/Kleinschreibung unterscheidenden Sortierung zwei Tabellen mit gleichen Namen, die sich nur durch verschiedene Groß-/Kleinschreibung unterscheiden, erstellt werden; in einer Datenbank mit einer Sortierung ohne Unterscheidung nach Groß-/Kleinschreibung ist dies jedoch nicht möglich.

> [!NOTE]  
> Die Namen von Variablen oder die Parameter von Funktionen und gespeicherten Prozeduren müssen die Regeln für [!INCLUDE[tsql](../../includes/tsql-md.md)] -Bezeichner einhalten.

## <a name="classes-of-identifiers"></a>Bezeichnerklassen

 Es gibt zwei Klassen von Bezeichnern:

 Reguläre Bezeichner entsprechen den Regeln für das Format von Bezeichnern. Reguläre Bezeichner sind nicht begrenzt, wenn sie in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen verwendet werden.

```sql
SELECT *
FROM TableX
WHERE KeyCol = 124
```

 Begrenzungsbezeichner werden entweder in doppelte Anführungszeichen (") oder eckige Klammern ([ ]) eingeschlossen. Bezeichner, die den Regeln für das Format von Bezeichnern entsprechen, können u. U. nicht begrenzt sein. Beispiel:

```sql
SELECT *
FROM [TableX]         --Delimiter is optional.
WHERE [KeyCol] = 124  --Delimiter is optional.
```

 Bezeichner, die nicht allen Regeln für Bezeichner entsprechen, müssen in einer [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung begrenzt werden. Beispiel:

```sql
SELECT *
FROM [My Table]      --Identifier contains a space and uses a reserved keyword.
WHERE [order] = 10   --Identifier is a reserved keyword.
```

 Sowohl reguläre als auch Begrenzungsezeichner müssen zwischen 1 und 128 Zeichen enthalten. Bei lokalen temporären Tabellen darf der Bezeichner maximal 116 Zeichen enthalten.

## <a name="rules-for-regular-identifiers"></a>Regeln für reguläre Bezeichner
 Die Namen von Variablen, Funktionen und gespeicherten Prozeduren müssen den folgenden Regeln für [!INCLUDE[tsql](../../includes/tsql-md.md)] -Bezeichner entsprechen.

1.  Das erste Zeichen muss eines der folgenden Zeichen sein:

    -   Ein vom Unicode-Standard 3,2 definierter Buchstabe. Die Unicode-Definition von Buchstaben enthält die lateinischen Buchstaben von a bis z und von A bis Z sowie Buchstaben anderer Sprachen.

    -   Das Sonderzeichen Unterstrich (_), At-Zeichen (@) oder Nummernzeichen (#).

         Bestimmte Sonderzeichen am Anfang eines Bezeichners haben in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eine besondere Bedeutung. Ein mit dem At-Zeichen beginnender regulärer Bezeichner bezeichnet immer eine lokale Variable oder einen lokalen Parameter und kann nicht als Name eines Objekts eines anderen Typs verwendet werden. Ein mit dem Nummernzeichen (#) beginnender Bezeichner steht für eine temporäre Tabelle oder Prozedur. Ein Bezeichner, der mit einem doppelten Nummernzeichen (##) beginnt, steht für ein globales temporäres Objekt. Das Nummernzeichen und das doppelte Nummernzeichen können zwar auch am Anfang von Namen von Objekten anderer Typen stehen, diese Vorgehensweise wird jedoch nicht empfohlen.

         Einige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktionen haben Namen, die mit doppelten At-Zeichen beginnen (@@). Um Verwechslungen zu vermeiden, sollten Sie keine Namen verwenden, die mit einem @@ beginnen.

2.  Als nachfolgende Zeichen können folgende Zeichen verwendet werden:

    -   Im Unicode-Standard 3,2 definierte Buchstaben.

    -   Dezimalzahlen aus dem lateinischen Grundalphabet oder anderen nationalen Schriften.

    -   Das At-Zeichen, Dollar-Zeichen ($), Nummernzeichen oder Unterstrich-Zeichen.

3.  Der Bezeichner darf kein reserviertes [!INCLUDE[tsql](../../includes/tsql-md.md)] -Wort sein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reserviert sowohl die groß- also auch die kleingeschriebene Version reservierter Wörter. Beim Verwenden von Bezeichnern in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen müssen alle Bezeichner, die diese Regeln nicht einhalten, durch doppelte Anführungszeichen oder eckige Klammern begrenzt werden. Welche Wörter reserviert werden, hängt vom Kompatibilitätsgrad der Datenbank ab. Der Grad kann mithilfe der [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md) -Anweisung festgelegt werden.

4.  Eingebettete Leerzeichen oder Sonderzeichen sind nicht zulässig.

5.  Ergänzende Zeichen sind nicht zulässig.

 Beim Verwenden von Bezeichnern in [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen müssen alle Bezeichner, die diese Regeln nicht einhalten, durch doppelte Anführungszeichen oder eckige Klammern begrenzt werden.

> [!NOTE]
> Einige Regeln für das Format regulärer Bezeichner sind vom Kompatibilitätsgrad der Datenbank abhängig. Dieser Grad kann mithilfe von [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)festgelegt werden.

## <a name="see-also"></a>Weitere Informationen

- [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
- [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
- [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
- [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
- [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
- [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
- [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
- [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
- [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
- [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
- [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
- [Reservierte Schlüsselwörter &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
- [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
- [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
