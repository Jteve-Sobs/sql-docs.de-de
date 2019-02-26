---
title: Dokumentation zu R- und Python-Machine Learning und -Programmiererweiterungen – SQL Server-Machine Learning
description: R und Python in SQL Server, mit integrierter Data Science-Modellierung und Algorithmen für maschinelles Lernen für umfangreiche Analysen von Unternehmensdaten
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/10/2019
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 61d7d969e4ec51914e2467895b5e8b9bc2e00f06
ms.sourcegitcommit: a13256f484eee2f52c812646cc989eb0ce6cf6aa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803457"
---
# <a name="sql-server-machine-learning"></a>SQL Server Machine Learning

::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"

## <a name="sql-server-machine-learning-and-programming-extensions-documentation"></a>SQL Server-Machine Learning und -Programmiererweiterungen – Dokumentation

Erfahren Sie anhand unserer Schnellstarts, Tutorials und Artikel, wie Sie die externen Bibliotheken von R und Python sowie die Sprachen selbst für residente, relationale Daten verwenden können. Die R- und Python-Bibliotheken in [SQL Server-Machine Learning](what-is-sql-server-machine-learning.md) umfassen Basisverteilungen, Data Science-Modelle, Algorithmen für maschinelles Lernen und Funktionen zum Durchführen von umfangreichen leistungsstarken Analysen, ohne dass Daten über das Netzwerk übertragen werden müssen.

In SQL Server 2019 verwendet die Java-Codeausführung das gleiche Erweiterungsframework wie R und Python, allerdings beinhaltet sie keine Bibliotheken für Funktionen für Data Science und maschinelles Lernen. Weitere Informationen zu neuen Features finden Sie unter [Neuerungen in SQL Server-Machine Learning Services](what-s-new-in-sql-server-machine-learning-services.md).

|   |   |
|---|:--|
| ![R-Logo](media/index/logo_r.png) | Open Source-R wurde um [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) und KI-Algorithmen von Microsoft in [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) erweitert. Diese Bibliotheken ermöglichen Ihnen Vorhersagen und Vorhersagemodelle, statistische Analysen, Visualisierungen und umfangreiche Datenbearbeitung.<br/>Die Integration von R wurde mit [SQL Server 2016](install/sql-r-services-windows-install.md) eingeführt und ist auch in [SQL Server 2017](install/sql-machine-learning-services-windows-install.md) verfügbar. |
| ![Python-Logo](media/index/logo_python.png) | Python-Entwickler können die Microsoft-Bibliotheken [revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) und [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) für Predictive Analytics und umfangreiches maschinelles Lernen verwenden. Mit Anaconda und Python 3.5 kompatible Bibliotheken entsprechen der Baselineverteilung.<br/>Die Integration von Python wurde mit [SQL Server 2017](install/sql-machine-learning-services-windows-install.md) eingeführt. |
| ![Java-Logo](media/index/logo_java.png) | Java-Entwickler können die [Java-Spracherweiterung](java/extension-java.md) verwenden, um Code in gespeicherte Prozeduren oder ein Binärformat einzubetten, zugänglich über Transact-SQL.<br/>Die Integration von Java wurde mit [SQL Server 2019 (Vorschau) ](install/sql-machine-learning-services-ver15.md) eingeführt. |
| &nbsp; | &nbsp; |
::: moniker-end

::: moniker range="=sql-server-2016||=sql-server-2017"

## <a name="sql-server-machine-learning-r-and-python-documentation"></a>R und Python in SQL Server-Machine Learning – Dokumentation

Erfahren Sie anhand unserer Schnellstarts, Tutorials und Artikel, wie Sie die externen Bibliotheken von R und Python sowie die Sprachen selbst für residente, relationale Daten verwenden können. Die R- und Python-Bibliotheken in [SQL Server-Machine Learning](what-is-sql-server-machine-learning.md) umfassen Basisverteilungen, Data Science-Modelle, Algorithmen für maschinelles Lernen und Funktionen zum Durchführen von umfangreichen leistungsstarken Analysen, ohne dass Daten über das Netzwerk übertragen werden müssen.

|   |   |
|---|:--|
| ![R-Logo](media/index/logo_r.png) | Open Source-R wurde um [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) und KI-Algorithmen von Microsoft in [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) erweitert. Diese Bibliotheken ermöglichen Ihnen Vorhersagen und Vorhersagemodelle, statistische Analysen, Visualisierungen und umfangreiche Datenbearbeitung.<br/>Die Integration von R wurde mit [SQL Server 2016](install/sql-r-services-windows-install.md) eingeführt und ist auch in [SQL Server 2017](install/sql-machine-learning-services-windows-install.md) verfügbar. |
| ![Python-Logo](media/index/logo_python.png) | Python-Entwickler können die Microsoft-Bibliotheken [revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) und [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) für Predictive Analytics und umfangreiches maschinelles Lernen verwenden. Mit Anaconda und Python 3.5 kompatible Bibliotheken entsprechen der Baselineverteilung.<br/>Die Integration von Python wurde mit [SQL Server 2017](install/sql-machine-learning-services-windows-install.md) eingeführt. |
| &nbsp; | &nbsp; |
::: moniker-end

## <a name="5-minute-quickstarts"></a>5-minütige Schnellstarts

- [Erstellen eines Vorhersagemodells in R](tutorials/rtsql-create-a-predictive-model-r.md)

- [Vorhersagen und Zeichnen aus dem Modell mit R](tutorials/rtsql-predict-and-plot-from-model.md)

## <a name="step-by-step-tutorials"></a>Schritt-für-Schritt-Tutorials

- [Hinzufügen von maschinellem Lernen und Erweiterungsframework zu SQL Server](install/sql-machine-learning-services-windows-install.md)

- [Ausführen von R in T-SQL und gespeicherten Prozeduren](tutorials/sqldev-in-database-r-for-sql-developers.md)

- [Verwenden von Embedded Analytics in Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="video-introduction"></a>Einführungsvideo

> [!VIDEO https://www.youtube.com/embed/ACejZ9optCQ]

## <a name="reference"></a>Referenz

| Package | Sprache | Description |
|:--------|:---------|:------------|
| [RevoScaleR](/machine-learning-server/r-reference/revoscaler/revoscaler) | R | Verteilte und Parallelverarbeitung für R-Aufgaben: Datentransformation, -exploration und -visualisierung, statistische Analysen und Predictive Analytics |
| [MicrosoftML](/machine-learning-server/r-reference/microsoftml/microsoftml-package) | R | Für R angepasste Funktionen, die auf den KI-Algorithmen von Microsoft basieren |
| [olapR](/machine-learning-server/r-reference/olapr/olapr) | R | Importiert Daten aus OLAP-Cubes |
| [sqlRUtils](/machine-learning-server/r-reference/sqlrutils/sqlrutils) | R | Hilfsfunktionen zum Kapseln von R und T-SQL |
[revoscalepy](/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | Python | Verteilte und Parallelverarbeitung für Python-Aufgaben: Datentransformation, -exploration und -visualisierung, statistische Analysen und Predictive Analytics |
| [microsoftml](/machine-learning-server/python-reference/microsoftml/microsoftml-package) | Python | Für Python angepasste Funktionen, die auf den KI-Algorithmen von Microsoft basieren |
| &nbsp; | &nbsp; | &nbsp; |
