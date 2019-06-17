---
title: Führen Sie SQL-Task-Editor (Seite Resultset) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.resultset.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: d27000c8-8d91-4e1c-b45e-bca9a3c12f6d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d84f7fe551d83f609b2ffc3da92b51eb36b9a595
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66058968"
---
# <a name="execute-sql-task-editor-result-set-page"></a>Editor für den Task 'SQL ausführen' (Seite Resultset)
  Mithilfe der Seite **Resultset** des Dialogfelds **Editor für den Task 'SQL ausführen'** können Sie das Ergebnis der SQL-Anweisung neuen oder vorhandenen Variablen zuordnen. Die Optionen in diesem Dialogfeld sind deaktiviert, wenn auf der Seite Allgemein für **ResultSet** der Wert **Keine**festgelegt ist.  
  
 Weitere Informationen zu diesem Task finden Sie unter [SQL ausführen (Task)](control-flow/execute-sql-task.md) und [Resultsets im Task „SQL ausführen“](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).  
  
## <a name="options"></a>Optionen  
 **Ergebnisname**  
 Nachdem Sie durch Klicken auf **Hinzufügen**eine Resultsetzuordnung hinzugefügt haben, geben Sie einen Namen für das Ergebnis an. Je nach Resultsettyp müssen Sie bestimmte Ergebnisnamen verwenden.  
  
 Für den Resultsettyp **Einzelne Zeile**können Sie entweder den Namen einer von der Abfrage zurückgegebenen Spalte verwenden oder die Zahl, die die Position einer Spalte in der von der Abfrage zurückgegebenen Spaltenliste angibt.  
  
 Für den Resultsettyp **Vollständiges Resultset** oder **XML**müssen Sie 0 als Resultsetnamen verwenden.  
  
 **Verwandte Themen:** [Resultsets im Task „SQL ausführen“](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)  
  
 **Variablenname**  
 Ordnen Sie das Resultset einer Variablen zu, indem Sie eine Variable auswählen, oder klicken Sie auf \<**Neue Variable...** >, um mithilfe des Dialogfelds **Variable hinzufügen** eine neue Variable hinzuzufügen.  
  
 **Hinzufügen**  
 Klicken Sie auf diese Option, um eine Resultsetzuordnung hinzuzufügen.  
  
 **Entfernen**  
 Wählen Sie eine Resultsetzuordnung aus der Liste aus, und klicken Sie anschließend auf **Entfernen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor für den Task SQL ausführen &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor für den Task SQL ausführen &#40;Seite Parameterzuordnung&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md)   
 [Transact-SQL-Referenz &#40;Datenbank-Engine&#41;](/sql/t-sql/language-reference)  
  
  
