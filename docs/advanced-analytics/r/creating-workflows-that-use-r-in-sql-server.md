---
title: Erstellen von Business Intelligence (BI)-Workflows mit R – SQL Server Machine Learning Services
description: Kombinieren von Business Intelligence (BI) "und" Sprache "R" Szenarien für die Integration in SQL Server und SQL Server Integration Services (SSIS) unterstützen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 32dfb3317cb790c19289ab02362bf8ee765e5259
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432733"
---
# <a name="creating-bi-workflows-with-r"></a>Erstellen von BI-Workflows mit R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Eine relationale Datenbank ist eine hochgradig optimierte Technologie für die Bereitstellung von skalierbaren Lösungen für die Transaktionsverarbeitung sowie zur Speicherung und Abfrage von Daten.

Im Gegensatz dazu setzen üblicherweise R-Lösungen im Allgemeinen zum Importieren von Daten aus verschiedenen Quellen, oft im CSV-Format und die weiteres Durchsuchen von Daten sowie Modellierung aus. Solche Methoden sind nicht nur ineffizient, sondern auch unsicher.

Dieser Artikel beschreibt die Szenarien für die Integration für R und SQL-Server, der zu vermeiden, häufige Fehlerquellen und Sicherheitsrisiken, die auftreten können, wenn außerhalb der Datenbank Machine Learning-Lösungen entwickelt werden.

Außerdem wird beschrieben, Beispiele, wie Business Intelligence-Anwendungen, insbesondere die Integration Services und Reporting Services, R-Code interagieren können, und Nutzen von Daten oder Grafiken, die generiert werden.

Betrifft: SQL Server 2016 R Services, SQL Server 2017-Machine Learning-Dienste

## <a name="bring-compute-power-to-the-data"></a>Schalten Sie die Computeleistung auf die Daten

Ein Design des Ziel der Integration von Machine Learning in SQL Server wurde um Analysen in der Nähe der Daten zu bringen. Dies bietet mehrere Vorteile:

+ Datensicherheit. Bringen R näher an der Quelle der Daten vermeiden unnötiger oder unsicherer Datentransfer.

+ Geschwindigkeit. Datenbanken sind für setbasierte Vorgänge optimiert. Aktuelle Innovationen in Datenbanken, z.B. in-Memory-Tabellen stellen Zusammenfassungen und Aggregationen der Daten extrem, und es sind eine perfekte Ergänzung für die Data Science.

+ Einfache Bereitstellung und Integration. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist der zentrale Punkt von Vorgängen für viele Verwaltungsaufgaben von Daten und Anwendungen. Verwenden Sie die Daten, die in der Datenbank oder ein berichterstellungs-Warehouse befinden, stellen Sie sicher, dass die Daten, die von Machine learning-Lösungen verwendet konsistent und aktuell ist. 

+ Effizienz im gesamten Cloud und lokal. Anstatt die Daten in R zu verarbeiten, können Sie Datenpipelines des Unternehmens nutzen, darunter [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und Azure Data Factory. Das Berichten von Ergebnissen oder Analysen ist über Power BI oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]einfach.

Durch die Verwendung der richtigen Kombination von SQL und R für verschiedene Datenverarbeitungstasks und analytische Tasks, können Datenanalysten und Entwickler produktiver sein.

## <a name="use-integration-services-for-data-transformation-and-automation"></a>Verwenden von Integration Services für Data Transformation und Automatisierung

Data Science-Workflows sind hoch iterativ und umfassen eine Menge Transformation von Daten, einschließlich Skalierung, Aggregationen, die Berechnung der Wahrscheinlichkeiten, sowie das Umbenennen und Zusammenführen von Attributen. Obwohl Datenanalysten daran gewöhnt sind, viele dieser Aufgaben in R, Python oder einer anderen Sprache zu erledigen, erfordert das Ausführen solcher Workflows mit Unternehmensdaten nahtlose Integration mit ETL-Tools und -Prozessen.

Da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] es Ihnen ermöglicht, komplexe Vorgänge in R über Transact-SQL und gespeicherte Prozeduren auszuführen, können Sie R-spezifische Aufgaben mit vorhandenen ETL-Prozessen ohne erneute Entwicklung integrieren. Stattdessen als eine Kette von Aufgaben für arbeitsspeicherintensive in R auszuführen, die Vorbereitung der Daten kann optimiert werden mit den effizientesten Tools wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] und [!INCLUDE[tsql](../../includes/tsql-md.md)]. 

Hier sind einige Ideen für, wie Sie die Verarbeitung Ihrer Daten automatisieren können, und Modellierung von pipelines mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ Verwendung [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Tasks zum Erstellen von Features der erforderlichen Daten in der SQL-Datenbank
+ Verwenden von bedingter Verzweigung, um Computekontext für R-Aufträge zu wechseln
+ Führen Sie R-Aufträge, die ihre eigenen Daten in der Datenbank zu generieren, und Freigeben von Daten für Anwendungen
+ Bei Verwendung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], laden Sie R-Skript in einer Textvariablen gespeichert, und führen Sie es in SQL Server

### <a name="examples"></a>Beispiele

[Operationalize your machine learning project using SQL Server 2016 SSIS and R Services (Operationalisieren Ihres Machine Learning-Projekts mithilfe von SQL Server 2016 Integration Services (SSIS) und R Services)](https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/)  

In diesem Blogbeitrag zeigt grundlegende Verfahren zum Bearbeiten von R-Code mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]: 

+ Rufen Sie mit der Task SQL ausführen zum Generieren von Daten und speichern Sie es in R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

+ Verwenden einer gespeicherten Prozedur zum Trainieren eines R-Modells und Speichern in der Datenbank

+ Ausführen der Bewertung auf dem Modell mit dem Skripttask und dem Task „SQL ausführen“

##  <a name="bkmk_ssrs"></a> Verwenden von Reporting Services für die Datenvisualisierung

Obwohl R Diagramme und interessante Visualisierungen erstellen kann, ist es nicht gut mit externen Datenquellen integriert, was bedeutet, dass jedes Diagramm oder jeder Graph einzeln erstellt werden muss. Gemeinsame Nutzung kann auch schwierig sein.

Mithilfe von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] können Sie komplexe Vorgänge in R über gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren ausführen, die problemlos von einer Vielzahl von Tools für Unternehmensberichte, einschließlich [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und Power BI, genutzt werden können.

+ Visualisieren von Grafikobjekten, die über ein R-Skript mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]zurückgegeben werden
+ Verwenden der Tabelle in Power BI

### <a name="examples"></a>Beispiele

[R Graphics Device for Microsoft Reporting Services (SSRS) (R-Grafikgerät für Microsoft Reporting Services (SSRS))](https://rgraphicsdevice.codeplex.com/)

Dieses CodePlex-Projekt enthält den Code, mit dem Sie ein benutzerdefiniertes Berichtselement erstellen können, das die Grafikausgabe von R als Bild zur Verwendung in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichten rendert.  Mit dem benutzerdefinierten Berichtselement können Sie folgende Aktionen ausführen:

+ Veröffentlichen von Diagrammen und mit dem R-Grafikgerät erstellten Plots an [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dashboards

+ Übergeben von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Parametern an R-Plots

> [!NOTE]
> In diesem Beispiel muss der Code, der das R-Grafikgerät für Reporting Services unterstützt sowohl auf dem Reporting Services-Server als auch in Visual Studio installiert werden. Manuelle Kompilierung und Konfiguration sind ebenfalls erforderlich.
