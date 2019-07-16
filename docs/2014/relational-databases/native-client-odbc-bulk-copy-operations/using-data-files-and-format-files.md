---
title: Verwenden von Datendateien und Formatdateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c49ccb59a8e6ab1b027de02afee37252e8cc482
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206831"
---
# <a name="using-data-files-and-format-files"></a>Verwenden von Datendateien und Formatdateien
  Das einfachste Massenkopierprogramm geht wie folgt vor:  
  
1.  Aufrufe [Bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) an Massenkopieren (Set BCP_OUT) aus einer Tabelle oder Sicht in einer Datendatei.  
  
2.  Aufrufe [Bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) um den Massenkopiervorgang auszuführen.  
  
 Die Datendatei wird im einheitlichen Modus erstellt. Daher werden Daten aus allen Spalten in der Tabelle oder Sicht in der Datendatei im gleichen Format wie in der Datenbank gespeichert. Die Datei kann dann mit derselben Vorgehensweise auf einen Server massenkopiert werden, mit der Ausnahme, dass DB_IN statt DB_OUT festgelegt wird. Dies funktioniert jedoch nur, wenn sowohl die Quell- als auch die Zieltabellen genau dieselbe Struktur aufweisen. Die resultierende Datendatei kann auch eingegeben werden, um die **Bcp** Hilfsprogramm mithilfe der **/n** (einheitlicher Modus) wechseln.  
  
 So führen Sie einen Massenkopiervorgang des Resultsets einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung aus, anstatt direkt aus einer Tabelle oder Sicht zu kopieren:  
  
1.  Rufen Sie **Bcp_init** Massenkopieren angeben, aber geben Sie NULL für den Tabellennamen an.  
  
2.  Rufen Sie [Bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) mit *eOption* auf BCPHINTS festgelegt und *iValue* auf einen Zeiger auf eine SQLTCHAR-Zeichenfolge, die mit der Transact-SQL-Anweisung festgelegt.  
  
3.  Rufen Sie **bcp_exec** auf, um den Massenkopiervorgang auszuführen.  
  
 Die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung kann jede Anweisung sein, die ein Resultset generiert. Die Datendatei wird mit dem ersten Resultset der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung erstellt. Beim Massenkopieren wird jedes Resultset nach dem ersten ignoriert, wenn die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung mehrere Resultsets generiert.  
  
 Rufen Sie zum Erstellen einer Datendatei in die Spalte Daten in einem anderen Format als in der Tabelle gespeichert [Bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) aufrufen, um anzugeben, wie viele Spalten geändert werden soll, klicken Sie dann [Bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) für jede Spalte, deren Format Sie möchten ändern. Dies erfolgt nach dem Aufruf **Bcp_init** aber vor dem Aufrufen **Bcp_exec**. **Bcp_colfmt** gibt das Format, in dem die Daten der Spalte in der Datendatei gespeichert ist. Sie können beim Massenkopieren von herunter- oder hochskalieren verwendet werden. Sie können auch **Bcp_colfmt** um die Zeilen- und Spaltenabschlusszeichen festzulegen. Z. B. wenn die Daten keine Tabulatorzeichen enthalten, können Sie erstellen eine Datei mit Tabstopptrennzeichen mit **Bcp_colfmt** das Tabulatorzeichen als Abschlusszeichen für jede Spalte festgelegt.  
  
 Beim Massenkopieren und Verwenden von **Bcp_colfmt**, Sie können ganz einfach erstellen eine Formatdatei beschreiben die Datendatei, die Sie, durch den Aufruf erstellt haben [Bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) nach dem letzten Aufruf von **Bcp_colfmt**.  
  
 Beim Massenkopieren aus einer Datendatei, die durch eine Formatdatei beschrieben wird, lesen Sie die Formatdatei durch Aufrufen von [Bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) nach **Bcp_init** aber vor **Bcp_exec**.  
  
 Die **Bcp_control** -Funktion steuert verschiedene Optionen beim Massenkopieren in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus einer Datendatei. **Bcp_control** Legt Optionen fest, wie z. B. die maximale Anzahl von Fehlern vor dem Beenden, wird die Zeile in der Datei auf dem für das Massenkopieren, die Zeile, auf Beenden und die Batchgröße zu beginnen.  
  
## <a name="see-also"></a>Siehe auch  
 [Durchführen von Massenkopiervorgängen &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)  
  
  
