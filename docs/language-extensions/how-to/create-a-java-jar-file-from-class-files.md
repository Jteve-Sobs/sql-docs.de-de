---
title: Erstellen einer Java-JAR-Datei aus Klassendateien
description: Erfahren Sie, wie Sie eine Java-JAR-Datei aus Klassendateien erstellen.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a105dde9046167257a86705f678466872785b4be
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735095"
---
# <a name="create-a-java-jar-file-from-class-files"></a>Erstellen einer Java-JAR-Datei aus Klassendateien
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Hier erfahren Sie, wie Sie Klassendateien in eine JAR-Datei packen können, wenn Sie [SQL Server-Spracherweiterungen](../language-extensions-overview.md) für die Ausführung von Java-Code verwenden. Wir empfehlen, die Dateien zu packen.

## <a name="create-a-jar-file"></a>Erstellen einer JAR-Datei

Um eine JAR-Datei aus Klassendateien zu erstellen, navigieren zu dem Ordner, der Ihre Klassendatei enthält, und führen Sie den folgenden Befehl aus:

```cmd
jar -cf <MyJar.jar> *.class
```

Stellen Sie sicher, dass der Pfad zu `jar.exe` Teil der Systempfadvariable ist. Alternativ dazu können Sie auch den vollständigen Pfad zur JAR-Datei angeben, den Sie im JDK-Ordner unter `/bin` finden. Beispiel:

```cmd
C:\Users\MyUser\Desktop\jdk1.8.0_201\bin\jar -cf <MyJar.jar> *.class
```

## <a name="next-steps"></a>Nächste Schritte

+ [Aufrufen der Java-Runtime in SQL Server-Spracherweiterungen](../how-to/call-java-from-sql.md)