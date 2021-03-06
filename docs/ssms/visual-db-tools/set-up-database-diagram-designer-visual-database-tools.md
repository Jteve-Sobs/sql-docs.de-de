---
title: Einrichten des Datenbankdiagramm-Designer
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 811905581cf0bb8f7bbd73f71a751e3c3da028c3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999337"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Einrichten des Datenbankdiagramm-Designers (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Der Datenbankdiagramm-Designer kann erst verwendet werden, nachdem er von einem Mitglied der **db_owner** -Rolle für den Zugriff auf Diagramme eingerichtet wurde.  
  
### <a name="to-set-up-database-diagramming"></a>So richten Sie das Erstellen von Datenbankdiagrammen ein  
  
1.  Erweitern Sie im Objekt-Explorer einen Datenbankknoten.  
  
2.  Erweitern Sie den Knoten Datenbankdiagramme unter der Datenbankverbindung.  
  
3.  Wählen Sie an der entsprechenden Aufforderung **Ja** aus, wenn Sie das Erstellen von Datenbankdiagrammen einrichten möchten.  
  
    > [!NOTE]  
    > Damit werden die Datenbankdiagrammtabelle, gespeicherte Systemprozeduren und eine Systemfunktion in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank erstellt.  
  
4.  Visual Studio erstellt die folgenden Objekte für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    1.  sysdiagrams-Tabelle  
  
    2.  Gespeicherte Prozedur sp_alterdiagram  
  
    3.  Gespeicherte Prozedur sp_creatediagram  
  
    4.  Gespeicherte Prozedur sp_dropdiagram  
  
    5.  Gespeicherte Prozedur sp_renamediagram  
  
    6.  fn_diagramobjects-Funktion  
  
    7.  Gespeicherte Prozedur sp_helpdiagrams  
  
    8.  Gespeicherte Prozedur sp_helpdiagramsdefinition  
  
    9. Gespeicherte Prozedur sp_upgraddiagrams  
  
## <a name="see-also"></a>Weitere Informationen  
[Grundlagen des Besitzes von Datenbankdiagrammen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
[Aktualisieren von Datenbankdiagrammen aus älteren Versionen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
[ALTER AUTHORIZATION (Transact-SQL)](https://msdn.microsoft.com/8c805ae2-91ed-4133-96f6-9835c908f373)  
  
