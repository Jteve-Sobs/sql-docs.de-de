---
title: Erstellen den Server Connection Files (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Creating Server Connection Files
- Sybase Console,Server Connection File Validation
ms.assetid: 35ef396f-9f98-429d-9fc5-4f413d08fb37
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: ece41e157ddad4f62a041d8e06dde073f681d274
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029358"
---
# <a name="creating-the-server-connection-files-sybasetosql"></a>Erstellen der Serververbindungsdateien (SybaseToSQL)
Informationen zum Server kann entweder in den Bereich "Server", der Skriptdatei oder in eine separate Verbindung Serverdatei angegeben werden. Der Parameter über die Befehlszeile für die Server-Verbindungsdatei ist, `-c <serverconnectionfile>`. Wenn die gleiche Id in die Skriptdatei und die Server-Connection-Datei vorhanden ist, wird die Definition des Servers in der Skriptdatei als betrachtet.  
  
**Beispiel:**  
  
```  
1.<!--Sample of server connection file commands -->  
  
<sybase name="<source-server-unique-name>">  
  
  <standard-mode>  
  
    <provider value="Ole DB Provider"/>  
  
    <server-name value="<server-name>"/>  
  
    <server-port value="<port>"/>  
  
    <user-id value="<password>"/>  
  
  </standard-mode>  
  
</sybase>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication>  
  
    <database value="<database-name>"/>  
  
    <server value="<server-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
    <encrypt value="<true/false>"/>  
  
    <trust-server-certificate value="<true/false>"/>  
  
  </sql-server-authentication >  
  
</sql-server>  
```  
  
```  
2.<!-Sample of server connection file commands-->  
<sybase name="<source-server-unique-name>">  
  
  <advanced-mode>  
  
    <connection-string value="User ID=<user-name>;Password=<password>;Provider=ASEOLEDB.1;Server=<server-name>;Port=<port>;OLE DB Services = -2;"/>  
  
  </advanced-mode >  
  
</sybase>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication >  
  
    <database value="<database-name>"/>  
  
    <server value="<server-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
  </sql-server-authentication >  
  
</sql-server>  
```  
  
## <a name="server-connection-file-validation"></a>Datei-Überprüfung von Server-Verbindung  
Benutzer kann ganz einfach überprüfen, seine Verbindung-Serverdatei anhand der Schemadefinitionsdatei **S2SSConsoleScriptServersSchema.xsd** in den Ordner "Schemas" verfügbar.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt in der Konsole ausgeführt wird [Executing the SSMA Console ausführen &#40;SybaseToSQL&#41;](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Executing the SSMA Console (Ausführen der SSMA-Konsole)](executing-the-ssma-console-sybasetosql.md)  
  
