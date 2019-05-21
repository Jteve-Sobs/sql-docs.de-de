---
title: Verwenden der SSL-Verschlüsselung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1453daf6bf9e806a4b3ac79ae8c9a322e5bd0bac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771524"
---
# <a name="using-ssl-encryption"></a>Verwenden der SSL-Verschlüsselung

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Mit der SSL-Verschlüsselung (Secure Sockets Layer) können verschlüsselte Daten in einem Netzwerk zwischen einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und einer Clientanwendung übertragen werden.  
  
Secure Sockets Layer (SSL) ist ein Protokoll zum Einrichten eines sicheren Kommunikationskanals, um das Abfangen von kritischen oder vertraulichen Informationen im Netzwerk und bei anderen Internetkommunikationen zu verhindern. Durch SSL können der Client und der Server die Identität des anderen authentifizieren. Nach dem Authentifizieren der Teilnehmer stellt SSL verschlüsselte Verbindungen zwischen ihnen bereit, damit die Nachrichten sicher übertragen werden können.  
  
[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] stellt eine Infrastruktur bereit, mit der die Verschlüsselung für eine bestimmte Verbindung auf Grundlage der benutzerdefinierten Verbindungseigenschaften und der Server- und Clienteinstellungen aktiviert und deaktiviert werden kann. Der Benutzer kann den Speicherort des Zertifikatspeichers und das Kennwort sowie einen Hostnamen zum Überprüfen des Zertifikats angeben und festlegen, wann der Verbindungskanal verschlüsselt werden soll.  
  
Das Aktivieren der SSL-Verschlüsselung erhöht die Sicherheit von Daten, die netzwerkübergreifend zwischen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Anwendungen übertragen werden. Durch das Aktivieren der Verschlüsselung kommt es jedoch zu Leistungseinbußen.  
  
In den Themen in diesem Abschnitt werden die Unterstützung der SSL-Verschlüsselung in der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Version und neue Verbindungseigenschaften sowie das Konfigurieren des Vertrauensspeichers auf Clientseite beschrieben.  
  
> [!NOTE]  
> Die **HostNameInCertificate** Connection-Eigenschaft wird empfohlen, um ein SSL-Zertifikat zu überprüfen.  

## <a name="in-this-section"></a>In diesem Abschnitt  

| Thema                                                                                                        | Beschreibung                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Grundlegendes zur SSL-Unterstützung](../../connect/jdbc/understanding-ssl-support.md)                                 | Beschreibt die Unterstützung der SSL-Verschlüsselung in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].                                              |
| [Herstellen von Verbindungen mit SSL-Verschlüsselung](../../connect/jdbc/connecting-with-ssl-encryption.md)                       | Beschreibt das Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank mithilfe der neuen SSL-spezifischen Verbindungseigenschaften. |
| [Konfigurieren des Clients für SSL-Verschlüsselung](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md) | Beschreibt das Konfigurieren des Standardvertrauensspeichers auf Clientseite und das Importieren eines privaten Zertifikats im Vertrauensspeicher des Clientcomputers.   |
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Sichern von JDBC-Treiberanwendungen](../../connect/jdbc/securing-jdbc-driver-applications.md)  
