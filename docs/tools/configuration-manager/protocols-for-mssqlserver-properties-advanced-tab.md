---
title: Protokolle für MSSQLSERVER-Eigenschaften (Registerkarte „Erweitert“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 25573848ea6aa4a3bfb11c01fad9c9b72b04e5e3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660499"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a>Protokolle für MSSQLSERVER-Eigenschaften (Registerkarte "Erweitert")
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Mit der Registerkarte **Erweitert** im Dialogfeld **Protokolle für MSSQLSERVER-Eigenschaften** können Sie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]**Erweiterter Schutz für die Authentifizierung** konfigurieren. **Erweiterter Schutz** ist eine Funktion der vom Betriebssystem implementierten Netzwerkkomponenten. **Erweiterter Schutz** ist in Windows 7 und Windows Server 2008 R2 verfügbar und in Service Packs für ältere Betriebssysteme enthalten. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist sicherer, wenn Verbindungen möglichst mithilfe des **erweiterten Schutzes**hergestellt werden. Einige Funktionen von **Erweiterter Schutz** setzen die Auswahl von **Verschlüsselung erzwingen** auf der Registerkarte **Flags** voraus.  
  
> [!IMPORTANT]  
>  **Erweiterter Schutz** ist in Windows standardmäßig nicht aktiviert. Informationen zum Aktivieren von **Erweiterter Schutz** in Windows finden Sie im Knowledge Base-Artikel [Erweiterter Schutz für die Authentifizierung](https://go.microsoft.com/fwlink/?LinkId=178431).  
  
 Weitere Informationen zum Konfigurieren anderer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste und eine vollständige Beschreibung von **Erweiterter Schutz**finden Sie auf [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).  
  
 **Erweiterter Schutz** wird von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ab [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]vollständig unterstützt. Für andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clientanbieter wird **Erweiterter Schutz** derzeit nicht unterstützt.  
  
## <a name="options"></a>Tastatur  
 **Erweiterter Schutz**  
 Es gibt drei mögliche Werte:  
  
-   Bei der Einstellung **Aus**ist **Erweiterter Schutz** deaktiviert. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz akzeptiert Verbindungen von jedem beliebigen Client, unabhängig davon, ob er geschützt ist oder nicht. **Aus** ist mit älteren und nicht gepatchten Betriebssystemen kompatibel, bietet aber weniger Sicherheit. Verwenden Sie diese Einstellung nur, wenn Sie wissen, dass die Clientbetriebssysteme keinen erweiterten Schutz unterstützen.  
  
-   Bei der Einstellung **Zulässig**wird **Erweiterter Schutz** für Verbindungen von Betriebssystemen vorausgesetzt, die die Funktion **Erweiterter Schutz**unterstützen. Verbindungen von ungeschützten Clientanwendungen, die auf geschützten Clientbetriebssystemen ausgeführt werden, werden abgelehnt. **Erweiterter Schutz** wird für Verbindungen von ungeschützten Betriebssystemen ignoriert. Diese Einstellung ist sicherer als **Aus**, bietet jedoch nicht die höchste Sicherheit. Verwenden Sie diese Einstellung in gemischten Umgebungen, in denen einige Betriebssysteme oder Anwendungen die Funktion **Erweiterter Schutz** unterstützen, andere jedoch nicht.  
  
-   Bei der Einstellung **Erforderlich**werden nur Verbindungen von geschützten Anwendungen auf geschützten Betriebssystemen akzeptiert. Diese Einstellung ist die sicherste der drei Optionen. Von Betriebssystemen, die die Funktion **Erweiterter Schutz** nicht unterstützen, können jedoch keine Verbindungen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt werden.  
  
 **Akzeptierte NTLM-SPNs**  
 Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durch mehr als einen NTLM-Dienstprinzipalnamen (SPN) identifiziert wird, listen Sie die SPNs hier als eine Reihe von Zeichenfolgen auf, die von Semikolons getrennt wird. Der Wert **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com**zeigt beispielsweise an, dass Clients, die versuchen, eine Verbindung mit SPNs mit dem Namen **MSSQLSvc/HOST1.Contoso.com** und **MSSQLSvc/HOST2.Contoso.com** herzustellen, zulässig sind. Die maximale Länge der Variablen beträgt 2048 Zeichen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterter Schutz für die Authentifizierung mit Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)  
  
  
