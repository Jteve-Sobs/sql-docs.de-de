---
title: Verwenden der integrierten Kerberos-Authentifizierung für Verbindungen mit SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d67a368c1c33d9f3c85e36d15ad2b77fe7837c88
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "55736991"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Verwenden der integrierten Kerberos-Authentifizierung für Verbindungen mit SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Ab [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] können Anwendungen mithilfe der Verbindungseigenschaft **authenticationScheme** angeben, dass eine Verbindung mit einer Datenbank unter Verwendung der integrierten Kerberos-Authentifizierung Typ 4 hergestellt werden soll. Finden Sie unter [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md) für Weitere Informationen zu Verbindungseigenschaften. Weitere Informationen zu Kerberos finden Sie unter [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758).

Bei Verwendung der integrierten Authentifizierung mit dem Java-**Krb5LoginModule** können Sie das Modul mithilfe der [Klasse Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html) konfigurieren.

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] legt für Java-VMs von IBM die folgenden Eigenschaften fest:

- **useDefaultCcache = true**
- **ModuleBanner = "false"**

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] legt für alle anderen Java-VMs die folgenden Eigenschaften fest:

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Remarks

Vor dem [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], Anwendungen können die integrierte Authentifizierung (mithilfe von Kerberos oder NTLM, je nach Verfügbarkeit) angeben mithilfe der **IntegratedSecurity** -Verbindungseigenschaft und durch Verweisen auf  **"sqljdbc_auth.dll"**, wie in beschrieben [Building the Connection URL](../../connect/jdbc/building-the-connection-url.md).

Ab [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] können Anwendungen mit der Verbindungseigenschaft **authenticationScheme** angeben, dass eine Verbindung mit einer Datenbank mithilfe der integrierten Kerberos-Authentifizierung hergestellt werden soll, unter Verwendung der reinen Java-Kerberos-Implementierung:

- Wenn Sie die integrierte Authentifizierung verwenden möchten **Krb5LoginModule**, Sie müssen noch angeben, die **IntegratedSecurity = True** Connection-Eigenschaft. Sie würden dann auch angeben, die **AuthenticationScheme Java Kerberos =** Connection-Eigenschaft.

- Um den Vorgang fortzusetzen, integrierte Authentifizierung mit **"sqljdbc_auth.dll"**, geben Sie einfach **IntegratedSecurity = True** Connection-Eigenschaft (und optional **AuthenticationScheme = NativeAuthentication**).

- Bei Angabe von **AuthenticationScheme Java Kerberos =** jedoch nicht gleichzeitig angeben **IntegratedSecurity = True**, ignoriert der Treiber die **AuthenticationScheme** Connection-Eigenschaft, und sie erwarten, dass Benutzername und Kennwort-Anmeldeinformationen in der Verbindungszeichenfolge enthalten.

Wenn Verbindungen mit einer Datenquelle erstellt werden, können Sie das Authentifizierungsschema programmgesteuert mit **setAuthenticationScheme** und optional den SPN für Kerberos mithilfe von **setServerSpn** festlegen.

Zur Unterstützung der Kerberos-Authentifizierung wurde eine neue Protokollierung eingeführt: com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Weitere Informationen finden Sie unter [Tracing Driver Operation (Ablaufverfolgung für Treibervorgänge)](../../connect/jdbc/tracing-driver-operation.md).

Befolgen Sie beim Konfigurieren von Kerberos die folgenden Richtlinien:

1. Legen Sie **AllowTgtSessionKey** 1 in der Registrierung für Windows. Weitere Informationen finden Sie unter [Kerberos protocol registry entries and KDC configuration keys in Windows Server 2003 (KDC-Konfigurationsschlüssel in Windows Server 2003 und Kerberos-Protokoll-Registrierungseinträge)](https://support.microsoft.com/kb/837361).
2. Stellen Sie sicher, dass die Kerberos-Konfiguration (krb5.conf in UNIX-Umgebungen) auf den richtigen Bereich und KDC für Ihre Umgebung zeigt.
3. Initialisieren Sie den TGT-Cache mit "kinit" oder indem Sie sich bei der Domäne anmelden.
4. Bei Ausführung einer Anwendung, die **authenticationScheme=JavaKerberos** verwendet, unter dem Betriebssystem Windows Vista bzw. Windows 7 muss ein Standardbenutzerkonto verwendet werden. Wenn Sie jedoch die Anwendung unter einem Administratorkonto ausführen, muss sie mit Administratorberechtigungen ausgeführt werden.

> [!NOTE]  
> Das Verbindungsattribut „serverSpn“ wird nur vom Microsoft JDBC-Treiber 4.2 und höher unterstützt.

## <a name="service-principal-names"></a>Dienstprinzipalnamen

Ein Dienstprinzipalname (SPN, Service Principal Name) ist der Name, über den ein Client eine Instanz eines Diensts eindeutig identifiziert.

Sie können den SPN mithilfe der Verbindungseigenschaft **serverSpn** angeben oder ihn einfach vom Treiber erstellen lassen (Standardeinstellung). Diese Eigenschaft kann in der Form „MSSQLSvc/fqdn:port\@REALM“ angegeben werden, wobei „fqdn“ den vollqualifizierten Domänennamen, „Port“ die Portnummer und „REALM“ den Kerberos-Bereich des SQL Server-Computers in Großbuchstaben darstellen. Der Bereichsteil dieser Eigenschaft ist optional, wenn der Standardbereich Ihrer Kerberos-Konfiguration der gleiche Bereich wie der des Servers ist, und wird standardmäßig nicht angegeben. Wenn Sie ein bereichsübergreifendes Authentifizierungsszenario unterstützen möchten, in dem sich der Standardbereich der Kerberos-Konfiguration vom Bereich des Servers unterscheidet, müssen Sie den SPN mithilfe der Eigenschaft „serverSpn“ angeben.

Ihr SPN könnte beispielsweise folgendermaßen aussehen: "MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ. CORP. CONTOSO.COM"

Weitere Informationen zu Dienstprinzipalnamen (SPNs) finden Sie in folgendem Thema:

- [Verwenden der Kerberos-Authentifizierung in SQL Server](https://support.microsoft.com/kb/319723)

- [Verwenden von Kerberos mit SQL Server](https://go.microsoft.com/fwlink/?LinkId=207814)

> [!NOTE]  
> Vor 6.2 Version des JDBC-Treiber für die ordnungsgemäße Verwendung von Cross-Realm Kerberos verwendet, müssen Sie explizit festlegen der **"serverspn"**.
>
> Ab der Version 6.2 der Treiber werden zum Erstellen der **"serverspn"** standardmäßig, selbst wenn Cross-Realm Kerberos verwendet. Obwohl eine verwenden können **"serverspn"** explizit zu.

## <a name="creating-a-login-module-configuration-file"></a>Erstellen einer Anmeldemodul-Konfigurationsdatei

Sie können optional eine Kerberos-Konfigurationsdatei angeben. Wenn keine Konfigurationsdatei angegeben wird, gelten die folgenden Einstellungen:

Sun-JVM  
 com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;

IBM-JVM  
 com.ibm.security.auth.module.Krb5LoginModule required useDefaultCcache = true;

Wenn Sie selbstständig eine Anmeldemodul-Konfigurationsdatei erstellen, muss die Datei das folgende Format aufweisen:

```java
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```

Eine Anmeldemodul-Konfigurationsdatei enthält einen oder mehrere Einträge, die jeweils angeben, welche zugrunde liegende Authentifizierungstechnologie für eine bestimmte Anwendung bzw. für bestimmte Anwendungen verwendet werden soll. Beispiel:

```java
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```

Jeder Eintrag der Anmeldemodul-Konfigurationsdatei besteht aus einem Namen, auf den ein oder mehrere LoginModule-spezifische Einträge folgen. Jeder LoginModule-spezifische Eintrag wird jeweils durch ein Semikolon abgeschlossen, und die gesamte Gruppe von LoginModule-spezifischen Einträgen wird von geschweiften Klammern umschlossen. Jeder Konfigurationsdateieintrag wird durch ein Semikolon abgeschlossen.

Für den Treiber kann nicht nur festgelegt werden, dass Kerberos-Anmeldeinformationen mit den Einstellungen in der Anmeldemodul-Konfigurationsdatei erhalten werden können. Stattdessen kann der Treiber auch vorhandene Anmeldeinformationen verwenden. Dies kann hilfreich sein, wenn die Anwendung Verbindungen mit den Anmeldeinformationen mehrerer Benutzer herstellen muss.

Der Treiber versucht zunächst vorhandene Anmeldeinformationen zu verwenden (sofern diese verfügbar sind), bevor er die Anmeldung mit dem angegebenen Anmeldemodul ausführt. Bei Ausführung von Code unter einem bestimmten Kontext mithilfe der `Subject.doAs`-Methode wird daher eine Verbindung mit den Anmeldeinformationen erstellt, die an den Aufruf von `Subject.doAs` übergeben werden.

Weitere Informationen finden Sie unter [JAAS Login Configuration File (JAAS-Anmeldekonfigurationsdatei)](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) und [Class Krb5LoginModule (Klasse Krb5LoginModule)](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Ab Microsoft JDBC-Treiber 6.2, Name der Anmeldemodul-Konfigurationsdatei kann optional übergeben werden mithilfe der-Verbindungseigenschaft `jaasConfigurationName`, dadurch, dass jeder Verbindung, um eine eigene anmeldungskonfiguration verfügen.

## <a name="creating-a-kerberos-configuration-file"></a>Erstellen einer Kerberos-Konfigurationsdatei

Weitere Informationen zu Kerberos-Konfigurationsdateien finden Sie unter [Kerberos Requirements (Kerberos-Anforderungen)](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).

Dies ist eine Konfiguration für eine Beispieldomäne. YYYY und ZZZZ sind durch die Domänennamen zu ersetzen.

```ini
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  

[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  

[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  

        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  

```

## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>Aktivieren der Domänenkonfigurationsdatei und der Anmeldemodul-Konfigurationsdatei

Sie können eine Domänenkonfigurationsdatei mit -Djava.security.krb5.conf aktivieren. Sie können eine Anmeldemodul-Konfigurationsdatei mit aktivieren **-Djava.security.auth.login.config**.

Z. B. kann der folgende Befehl verwendet werden, um die Anwendung zu starten:

```bash
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  

```

## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Überprüfen des Zugriffs auf SQL Server über Kerberos

Führen Sie in SQL Server Management Studio die folgende Abfrage aus:

```sql
select auth_scheme from sys.dm_exec_connections where session_id=\@\@spid
```

Vergewissern Sie sich, dass Sie über die erforderliche Berechtigung zum Ausführen dieser Abfrage verfügen.

## <a name="constrained-delegation"></a>Eingeschränkte Delegierung

Ab Microsoft JDBC-Treiber 6.2, unterstützt der Treiber die eingeschränkte Kerberos-Delegierung. Die delegierten Anmeldeinformationen kann als org.ietf.jgss.GSSCredential-Objekt übergeben werden, diese Anmeldeinformationen werden vom Treiber verwendet, um die Verbindung herzustellen.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Kerberos-Verbindung mithilfe von Dienstprinzipalnamen und Kennwort

Ab Microsoft JDBC-Treiber 6.2, kann der Treiber herstellen Kerberos, die Verbindung mit dem Prinzipalname und Kennwort übergeben in der Verbindungszeichenfolge angegeben.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

Die Username-Eigenschaft ist kein Bereich erforderlich, wenn Benutzer die Default_realm, legen Sie in der Datei krb5.conf angehört. Wenn `userName` und `password` festgelegt ist, zusammen mit `integratedSecurity=true;` und `authenticationScheme=JavaKerberos;` -Eigenschaft, die Verbindung wird hergestellt, mit dem Wert des Benutzernamens als Kerberos-Prinzipal, zusammen mit dem angegebenen Kennwort.

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>Verwenden von Kerberos-Authentifizierung von Unix-Computern in der gleichen Domäne

Dieses Handbuch setzt voraus, eine funktionierende Kerberos-Einrichtung ist bereits vorhanden. Führen Sie den folgenden Code auf einem Windows-Computer mit Kerberos-Authentifizierung, um sicherzustellen, dass die oben genannte "true" ist. Der Code gibt "Authentifizierungsschema: KERBEROS"in der Konsole aus, wenn erfolgreich. Keine zusätzliche Flags der Laufzeit, Abhängigkeiten oder Netzwerktreiber sind außerhalb von den angebotenen erforderlich. Im gleiche Codeblock kann unter Linux, um zu überprüfen, ob erfolgreiche Verbindungen ausgeführt werden.

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("JavaKerberos");
ds.setDatabaseName("<database>");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

1. Domäne beitreten Client-Computer der gleichen Domäne wie der Server an.
2. (Optional) Legen Sie den Standardspeicherort für Kerberos-Ticket. Dies erfolgt am einfachsten durch Festlegen der `KRB5CCNAME` -Umgebungsvariablen angegeben.
3. Abrufen des Kerberos-Tickets, entweder durch Generieren eines neuen oder platzieren eine vorhandene eine am Standardspeicherort für Kerberos-Ticket. Um ein Ticket generieren, verwenden Sie einen Terminal, und initialisieren Sie das Ticket über `kinit USER@DOMAIN.AD` , in denen "USER" und "-Domäne. AD"wird der Prinzipal und der Domäne. Zum Beispiel `kinit SQL_SERVER_USER03@MICROSOFT.COM`. Das Ticket generiert werden, in der Standardspeicherort für das Ticket oder in der `KRB5CCNAME` Pfad Wenn festlegen.
4. Geben Sie das Terminal fordert zur Eingabe eines Kennworts, das Kennwort ein.
5. Überprüfen Sie die Anmeldeinformationen des Tickets über `klist` und bestätigen Sie die Anmeldeinformationen sind diejenigen, die Sie für die Authentifizierung verwenden möchten.
6. Führen Sie den obige Beispielcode aus, und bestätigen Sie, dass Kerberos-Authentifizierung erfolgreich war.

## <a name="see-also"></a>Weitere Informationen

[Verbinden von SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
