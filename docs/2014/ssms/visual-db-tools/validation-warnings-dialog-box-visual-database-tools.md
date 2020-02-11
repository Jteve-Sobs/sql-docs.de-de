---
title: Gültigkeitswarnungen (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65556
- vdt.dlgbox.validationwarnings
ms.assetid: fc76e234-ec9c-4a19-a65b-cb558ec8268e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83fde7d8d43086114b2aae4350ce374b713ff4ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63204661"
---
# <a name="validation-warnings-dialog-box-visual-database-tools"></a>Gültigkeitswarnungen (Dialogfeld) (Visual Database Tools)
  Dieses Dialogfeld wird angezeigt, wenn Sie Änderungen zu speichern versuchen, die u. U. Schaden anrichten, oder wenn der Commit für die Datenbank vermutlich fehlschlägt. In diesem Dialogfeld werden die möglichen Nebeneffekte bzw. die Gründe für das Fehlschlagen des Commitvorgangs angegeben. Sie können dann entweder mit der Änderung fortfahren oder den Vorgang abbrechen.  
  
> [!NOTE]  
>  Dieses Dialogfeld wird angezeigt, wenn Sie versuchen, vorgenommene Änderungen an die Datenbank zu übermitteln, oder wenn Sie ein Änderungsskript speichern.  
  
 Das Dialogfeld kann aus folgenden Gründen angezeigt werden:  
  
-   Sie besitzen möglicherweise nicht die Datenbankberechtigungen zum Ausführen eines Commits für alle Änderungen.  
  
-   Die Änderungen würden falsch formatierte abgeleitete Spalten, Standardeinschränkungen oder CHECK-Einschränkungen zur Folge haben.  
  
-   Die Änderung des Datentyps für eine Spalte könnte zu Datenverlusten führen.  
  
-   Eine Änderung hätte einen Index von mehr als 900 Byte zur Folge.  
  
-   Eine Änderung würde eine Tabelle bzw. Spalte ändern und würde dadurch zu einer an ein Schema gebundenen Sicht oder einer benutzerdefinierten Funktion führen.  
  
-   Eine Änderung würde zur Neuerstellung einer Tabelle mit mindestens einem verschlüsselten Trigger führen, wobei die Trigger gelöscht werden würden.  
  
-   Die Änderungen ergeben besondere Einstellungen von ANSI_NULLS und/oder ANSI_PADDING für die Spalten innerhalb einer Tabelle.  
  
## <a name="options"></a>Tastatur  
 **Ja**  
 Setzen Sie den Vorgang fort, und generieren Sie das Änderungsskript, oder übermitteln Sie die Änderungen an die Datenbank. Der Commitvorgang kann trotzdem noch fehlschlagen, wenn Sie nicht über die Berechtigungen zum Ändern der Datenbank verfügen, wenn die Änderungen bewirken, dass der Index größer als 900 Bytes wird, oder wenn die Änderungen eine falsch formatierte berechnete Spalte, Standardeinschränkungen oder CHECK-Einschränkungen zur Folge haben.  
  
 **Nein**  
 Brechen Sie den Speichervorgang ab.  
  
 **Textdatei speichern**  
 Zeigen Sie das Dialogfeld **Speichern unter** an, in dem Sie einen Speicherort für eine Textdatei angeben können, die eine Liste der Warnungen enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwerfen von Tabellen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
