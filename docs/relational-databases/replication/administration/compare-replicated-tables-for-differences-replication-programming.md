---
title: Überprüfen replizierter Tabellen auf Unterschiede (Replikationsprogrammierung) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- tablediff utility
- comparing replicated tables
ms.assetid: cd253a17-0c85-42b4-912c-690169ebe799
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a1058103ba479917512ff5cc2e6893b9197bc371
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129560"
---
# <a name="compare-replicated-tables-for-differences-replication-programming"></a>Überprüfen replizierter Tabellen auf Unterschiede (Replikationsprogrammierung)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Mithilfe der Artikelüberprüfung wird ermittelt, ob veröffentlichte Daten für Tabellenartikel auf dem Verleger und dem Verteiler identisch sind. Unterschiede können auf Nichtkonvergenz hinweisen. Weitere Informationen zur Überprüfung finden Sie unter [Überprüfen von replizierten Daten](../../../relational-databases/replication/validate-data-at-the-subscriber.md). Die Überprüfung gibt jedoch lediglich Auskunft darüber, ob die Daten identisch sind oder nicht. Details zu Unterschieden zwischen der Quell- und der Zieltabelle werden nicht zurückgegeben. Das Befehlszeilenhilfsprogramm **tablediff** gibt ausführliche Informationen zu den Unterschieden zwischen zwei Tabellen zurück und kann sogar ein [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Skript generieren, mit dem ein Abonnement mit den Daten auf dem Verleger in Übereinstimmung gebracht werden kann.  
  
> [!NOTE]  
>  Das Hilfsprogramm **tablediff** wird nur für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Server unterstützt.  
  
### <a name="to-compare-replicated-tables-for-differences-using-tablediff"></a>So überprüfen Sie replizierte Tabellen mithilfe von "tablediff" auf Unterschiede  
  
1.  Führen Sie an der Eingabeaufforderung auf einem beliebigen Server in einer Replikationstopologie [tablediff Utility](../../../tools/tablediff-utility.md)aus. Geben Sie die folgenden Parameter an:  
  
    -   **-sourceserver** - Name des Servers, auf dem die Daten korrekt sind (in der Regel der Verleger).  
  
    -   **-sourcedatabase** - Name der Datenbank, die die richtigen Daten enthält.  
  
    -   **-sourcetable** - Name der Quelltabelle für den Artikel, der verglichen wird.  
  
    -   (Optional) **-sourceschema** - Schemabesitzer der Quelltabelle, wenn nicht das Standardschema verwendet wird.  
  
    -   (Optional) **-sourceuser** und **-sourcepassword** bei Verwendung der SQL Server-Authentifizierung zum Herstellen der Verbindung mit dem Verleger.  
  
        > [!IMPORTANT]  
        >  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn Sie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung verwenden müssen, sollten die Benutzer zur Laufzeit zur Eingabe der Sicherheitsanmeldeinformationen aufgefordert werden. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
    -   **-destinationserver** - Name des Servers, auf dem die Daten verglichen werden (in der Regel ein Abonnent).  
  
    -   **-destinationdatabase** - Name der Datenbank, die verglichen wird.  
  
    -   **-destinationtable** - Name der Tabelle, die verglichen wird.  
  
    -   (Optional) **-destinationschema** - Schemabesitzer der Zieltabelle, wenn nicht das Standardschema verwendet wird.  
  
    -   (Optional) **-destinationuser** und **-destinationpassword** bei Verwendung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung zum Herstellen der Verbindung mit dem Abonnenten.  
  
        > [!IMPORTANT]  
        >  Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn Sie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Authentifizierung verwenden müssen, sollten die Benutzer zur Laufzeit zur Eingabe der Sicherheitsanmeldeinformationen aufgefordert werden. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
    -   (Optional) Verwenden Sie **-c** , um einen Vergleich auf Spaltenebene auszuführen.  
  
    -   (Optional) Verwenden Sie **-q** , um einen schnellen Vergleich auszuführen, bei dem lediglich die Zeilenanzahl und das Schema berücksichtigt werden.  
  
    -   (Optional) Geben Sie einen Dateinamen und einen Pfad für **-o** an, damit die Ergebnisse in eine Datei ausgegeben werden.  
  
    -   (Optional) Geben Sie eine Tabelle in der Abonnementdatenbank an, in die die Ergebnisse für **-et**eingefügt werden. Wenn die Tabelle bereits vorhanden ist, geben Sie **-dt** an, um die Tabelle zunächst zu löschen.  
  
    -   (Optional) Verwenden Sie **-f** , um eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Datei zu generieren und die Daten auf dem Abonnenten zu korrigieren, sodass sie mit den Daten auf dem Verleger übereinstimmen. Verwenden Sie **-df** , um die Anzahl von [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen in jeder Datei anzugeben.  
  
    -   (Optional) Verwenden Sie **-rc** bzw. **-ri** , um anzugeben, wie oft ein Vorgang wiederholt wird, bzw. um das Wiederholungsintervall anzugeben.  
  
    -   (Optional) Verwenden Sie **-strict** , um einen strikten Schemavergleich zwischen Quell- und Zieltabelle zu erzwingen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überprüfen der Daten am Abonnenten](../../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
