---
title: CLR Strict Security | Microsoft-Dokumentation
description: Konfigurieren von CLR Strict Security in SQL Server
ms.custom: ''
ms.date: 06/20/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- clr strict security
- clr_strict_security_TSQL
- clr strict security
- strict_security_TSQL
helpviewer_keywords:
- assemblies [CLR integration], strick security
- clr strict security option
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 84c049f451572cb1119e695182a6c896f013e04b
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087340"
---
# <a name="clr-strict-security"></a>CLR Strict Security   
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Steuert die Interpretation der Berechtigungen `SAFE`, `EXTERNAL ACCESS` und `UNSAFE` in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].   

|Wert |BESCHREIBUNG | 
|----- |----- | 
|0 |Deaktiviert: Wird für die Abwärtskompatibilität bereitgestellt. Der Wert `Disabled` wird empfohlen. | 
|1 |Aktiviert: Dadurch ignoriert [!INCLUDE[ssde-md](../../includes/ssde-md.md)] die `PERMISSION_SET`-Information auf den Assemblys und interpretiert diese immer als `UNSAFE`.  `Enabled` ist der Standardwert, von [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] an. | 

> [!WARNING]
>  CLR verwendet die Codezugriffssicherheit (Code Access Security, CAS) im .NET Framework, die nicht länger als Sicherheitsbegrenzung unterstützt wird. Eine CLR-Assembly, die mit `PERMISSION_SET = SAFE` erstellt wurde, kann womöglich auf externe Systemressourcen zugreifen, nicht verwalteten Code aufrufen und sysadmin-Privilegien erwerben. Ab [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] wird eine `sp_configure`-Option mit der Bezeichnung `clr strict security` eingeführt, um die Sicherheit von CLR-Assemblys zu erhöhen. `clr strict security` ist standardmäßig aktiviert und behandelt `SAFE`- und `EXTERNAL_ACCESS`-Assemblys so, als wären Sie als `UNSAFE` gekennzeichnet. Die Option `clr strict security` kann für die Abwärtskompatibilität deaktiviert werden, es wird jedoch nicht empfohlen. Microsoft empfiehlt, dass alle Assemblys durch ein Zertifikat oder einen asymmetrischen Schlüssel mit einem entsprechenden Anmeldenamen signiert werden, dem `UNSAFE ASSEMBLY`-Berechtigung für die Masterdatenbank gewährt wurde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Administratoren können auch Assemblys einer Liste von Assemblys hinzufügen, der die Datenbank-Engine vertrauen sollte. Weitere Informationen finden Sie unter [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md).

## <a name="remarks"></a>Bemerkungen   

Falls die Option `PERMISSION_SET` aktiviert ist, wir sie in den Anweisungen `CREATE ASSEMBLY` und `ALTER ASSEMBLY` zur Laufzeit ignoriert, jedoch werden die `PERMISSION_SET`-Optionen in den Metadaten beibehalten. Das Ignorieren dieser Option vermindert die Trennung vorhandener Codeanweisungen.

`CLR strict security` ist eine `advanced option`.  

> [!IMPORTANT]
>  Nachdem Sie Strict Security aktiviert haben, können Assemblys, die nicht signiert sind, nicht geladen werden. Sie müssen jede Assembly entweder bearbeiten, ablegen oder neu erstellen, damit sie mit einem Zertifikat oder asymmetrischen Schlüssel signiert ist, der über einen entsprechenden Anmeldenamen mit der `UNSAFE ASSEMBLY`-Berechtigung auf dem Server verfügt.

## <a name="permissions"></a>Berechtigungen 

### <a name="to-change-this-option"></a>So ändern Sie diese Option  
Erfordert die `CONTROL SERVER`-Berechtigung oder die Mitgliedschaft in der festen `sysadmin`-Serverrolle.

### <a name="to-create-an-clr-assembly"></a>So erstellen Sie eine CRL-Assembly   
Die folgenden Berechtigungen werden zum Erstellen einer CLR-Assembly benötigt, wenn `CLR strict security` aktiviert ist:

- Der Benutzer muss über die `CREATE ASSEMBLY`-Berechtigung verfügen.  
- Eine der folgenden Bedingungen muss ebenfalls erfüllt sein:  
  - Die Assembly ist mit einem Zertifikat oder asymmetrischen Schlüssel signiert, der über einen entsprechenden Anmeldenamen mit der `UNSAFE ASSEMBLY`-Berechtigung auf dem Server verfügt. Es wird empfohlen, die Assembly zu signieren.  
  - Die `TRUSTWORTHY`-Eigenschaft der Datenbank ist auf `ON` festgelegt, und der Besitzer der Datenbank ist ein Anmeldename, der über `UNSAFE ASSEMBLY`-Berechtigungen auf dem Server verfügt. Diese Option wird nicht empfohlen.  

  
## <a name="see-also"></a>Weitere Informationen  
  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [CLR-fähig (Serverkonfigurationsoption)](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)
