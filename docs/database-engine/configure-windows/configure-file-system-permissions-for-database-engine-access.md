---
title: Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/06/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: ef8e2fd80accc21e3497d3c2f3671116f824902f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799434"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>Konfigurieren von Dateisystemberechtigungen für den Datenbank-Engine-Zugriff
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]Dateisystemzugriff auf den Ort gewährt wird, an dem die Datenbankdateien gespeichert sind. Der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Dienst muss vom Windows-Dateisystem die Berechtigung für den Zugriff auf den Dateiordner erhalten, in dem die Datenbankdateien gespeichert sind. Die Berechtigung für den Zugriff auf den Standardspeicherort wird bei der Ausführung von Setup konfiguriert. Wenn Sie Datenbankdateien an einem anderen Ort ablegen, müssen Sie u. U. die folgenden Schritte ausführen, um dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] die Vollzugriffsberechtigung auf diesen Ort zu gewähren.  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden der Pro-Dienst-SID Berechtigungen für alle enthaltenen Dienste zugewiesen. Dieses System unterstützt die Dienstisolierung und den gründlichen Schutz. Die Pro-Dienst-SID ergibt sich aus dem Dienstnamen und ist für jeden Dienst eindeutig. Im Thema [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) werden die Pro-Dienst-SID beschrieben und Namen im Abschnitt **Windows-Berechtigungen und Rechte**bereitgestellt. Der Pro-Dienst-SID muss die Zugriffsberechtigung für den Dateispeicherort zugewiesen werden.  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>So gewähren Sie der Pro-Dienst-SID eine Dateisystemberechtigung  
  
1.  Navigieren Sie im Windows-Explorer zu dem Speicherort im Dateisystem, an dem die Datenbankdateien gespeichert sind. Klicken Sie mit der rechten Maustaste auf den Dateisystemordner, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf der Registerkarte **Sicherheit** auf **Bearbeiten**und dann auf **Hinzufügen**.  
  
3.  Klicken Sie im Dialogfeld zum **Auswählen von Benutzern, Computer, Dienstkonto oder Gruppen** oben in der Speicherortliste auf **Speicherorte**, wählen Sie den Computernamen aus, und klicken Sie auf **OK**.  
  
4.  Geben Sie im Feld **Geben Sie die Namen der auszuwählenden Objekte ein** den Namen der Pro-Dienst-SID aus dem Thema [**Konfigurieren von Windows-Dienstkonten und -Berechtigungen**](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)der Onlinedokumentation ein. (Verwenden Sie als Pro-Dienst-SID-Namen des [!INCLUDE[ssDE](../../includes/ssde-md.md)] s **NT SERVICE\MSSQLSERVER** für eine Standardinstanz bzw. **NT SERVICE\MSSQL$InstanceName** für eine benannte Instanz.)  
  
5.  Klicken Sie auf **Namen überprüfen** , um den Eintrag zu überprüfen. (Wenn bei der Überprüfung ein Fehler zurückgegeben wird, kann dies darauf hindeuten, dass der Name nicht gefunden wurde. Wenn Sie auf **OK**klicken, wird das Dialogfeld **Mehrere Namen gefunden** angezeigt. den Pro-Dienst-SID-Namen – entweder **MSSQLSERVER** oder **NT SERVICE\MSSQL$InstanceName**– aus, und klicken Sie auf **OK**.  Klicken Sie erneut auf **OK** , um zum Dialogfeld **Berechtigungen** zurückzukehren.)   
6.  Wählen Sie im Feld **Gruppen- oder Benutzernamen** den Pro-Dienst-SID-Namen aus, und aktivieren Sie im Feld **Berechtigungen für** \<Name> für **Vollzugriff** das Kontrollkästchen **Zulassen**.  
  
7. Klicken Sie auf **Anwenden**und dann zweimal auf **OK** , um das Dialogfeld zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten der Datenbank-Engine-Dienste](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [Verschieben von Systemdatenbanken](../../relational-databases/databases/move-system-databases.md)   
 [Verschieben von Benutzerdatenbanken](../../relational-databases/databases/move-user-databases.md)  
  
  
