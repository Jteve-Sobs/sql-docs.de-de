---
title: Sp_send_dbmail (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sendmail_sp_TSQL
- sendmail_sp
- SP_SEND_DBMAIL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_send_dbmail
ms.assetid: f1d7a795-a3fd-4043-ac4b-c781e76dab47
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52a89c0220bddde6944e759936dc22ad1f3e0ff2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126304"
---
# <a name="spsenddbmail-transact-sql"></a>sp_send_dbmail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Sendet eine E-Mail-Nachricht an die angegebenen Empfänger. Die Nachricht kann ein Abfrageresultset, Dateianlagen oder beides enthalten. Wenn e-Mail-Nachrichten erfolgreich in der Datenbank-Mail-Warteschlange platziert wird **Sp_send_dbmail** gibt die **Mailitem_id** der Nachricht. Diese gespeicherte Prozedur wird in der **msdb** -Datenbank gespeichert.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_send_dbmail [ [ @profile_name = ] 'profile_name' ]  
    [ , [ @recipients = ] 'recipients [ ; ...n ]' ]  
    [ , [ @copy_recipients = ] 'copy_recipient [ ; ...n ]' ]  
    [ , [ @blind_copy_recipients = ] 'blind_copy_recipient [ ; ...n ]' ]  
    [ , [ @from_address = ] 'from_address' ]  
    [ , [ @reply_to = ] 'reply_to' ]   
    [ , [ @subject = ] 'subject' ]   
    [ , [ @body = ] 'body' ]   
    [ , [ @body_format = ] 'body_format' ]  
    [ , [ @importance = ] 'importance' ]  
    [ , [ @sensitivity = ] 'sensitivity' ]  
    [ , [ @file_attachments = ] 'attachment [ ; ...n ]' ]  
    [ , [ @query = ] 'query' ]  
    [ , [ @execute_query_database = ] 'execute_query_database' ]  
    [ , [ @attach_query_result_as_file = ] attach_query_result_as_file ]  
    [ , [ @query_attachment_filename = ] query_attachment_filename ]  
    [ , [ @query_result_header = ] query_result_header ]  
    [ , [ @query_result_width = ] query_result_width ]  
    [ , [ @query_result_separator = ] 'query_result_separator' ]  
    [ , [ @exclude_query_output = ] exclude_query_output ]  
    [ , [ @append_query_error = ] append_query_error ]  
    [ , [ @query_no_truncate = ] query_no_truncate ]   
    [ , [ @query_result_no_padding = ] @query_result_no_padding ]   
    [ , [ @mailitem_id = ] mailitem_id ] [ OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_name = ] 'profile_name'` Ist der Name des Profils, das Senden der Nachricht aus. Die *Profile_name* ist vom Typ **Sysname**, hat den Standardwert NULL. Die *Profile_name* muss der Name eines vorhandenen Datenbank-Mail-Profils sein. Wenn kein *Profile_name* angegeben wird, **Sp_send_dbmail** als privates Standardprofil für den aktuellen Benutzer verwendet. Wenn der Benutzer nicht über ein privates Standardprofil verfügt **Sp_send_dbmail** verwendet das öffentliche Standardprofil für den **Msdb** Datenbank. Wenn der Benutzer verfügt nicht über ein privates Standardprofil und es kein öffentliches Standardprofil für die Datenbank ist **@profile_name** muss angegeben werden.  
  
`[ @recipients = ] 'recipients'` Ist eine durch Semikolons getrennte Liste der e-Mail-Adressen zum Senden der Nachricht auf. Die Empfängerliste ist vom Typ **varchar(max)** . Obwohl dieser Parameter optional ist, ist mindestens eine der **@recipients** , **@copy_recipients** , oder **@blind_copy_recipients** muss angegeben werden, oder **Sp_ Send_dbmail** gibt einen Fehler zurück.  
  
`[ @copy_recipients = ] 'copy_recipients'` Ist eine durch Semikolons getrennte Liste der e-Mail-Adressen, an eine Kopie der Nachricht an. Liste der Kopieempfänger ist vom Typ **varchar(max)** . Obwohl dieser Parameter optional ist, ist mindestens eine der **@recipients** , **@copy_recipients** , oder **@blind_copy_recipients** muss angegeben werden, oder **Sp_ Send_dbmail** gibt einen Fehler zurück.  
  
`[ @blind_copy_recipients = ] 'blind_copy_recipients'` Ist eine durch Semikolons getrennte Liste der e-Mail-Adressen, an der Blindkopie der Nachricht an. Die Liste der Blindkopie-Empfänger ist vom Typ **varchar(max)** . Obwohl dieser Parameter optional ist, ist mindestens eine der **@recipients** , **@copy_recipients** , oder **@blind_copy_recipients** muss angegeben werden, oder **Sp_ Send_dbmail** gibt einen Fehler zurück.  
  
`[ @from_address = ] 'from_address'` Ist der Wert der "von Adresse" die e-Mail-Nachricht. Dies ist ein optionaler Parameter, mit dem die Einstellungen im Mailprofil überschrieben werden. Dieser Parameter ist vom Typ **varchar(MAX)** . SMTP-Sicherheitseinstellungen stellen fest, ob diese Überschreibungen akzeptiert werden. Wenn kein Parameter angegeben ist, wird der Standardwert NULL verwendet.  
  
`[ @reply_to = ] 'reply_to'` Ist der Wert von "Antwortadresse" die e-Mail-Nachricht. Er akzeptiert nur eine E-Mail-Adresse als gültigen Wert. Dies ist ein optionaler Parameter, mit dem die Einstellungen im Mailprofil überschrieben werden. Dieser Parameter ist vom Typ **varchar(MAX)** . SMTP-Sicherheitseinstellungen stellen fest, ob diese Überschreibungen akzeptiert werden. Wenn kein Parameter angegeben ist, wird der Standardwert NULL verwendet.  
  
`[ @subject = ] 'subject'` Ist der Betreff der e-Mail-Nachricht. Der Betreff ist vom Typ **nvarchar(255)** . Wenn Sie keinen Betreff angeben, wird standardmäßig 'SQL Server-Nachricht' verwendet.  
  
`[ @body = ] 'body'` Ist der Text der e-Mail-Nachricht. Der Nachrichtentext ist vom Typ **nvarchar(max)** , hat den Standardwert NULL.  
  
`[ @body_format = ] 'body_format'` Ist das Format des Nachrichtentexts. Der Parameter ist vom Typ **varchar(20)** , hat den Standardwert NULL. Wenn der Parameter angegeben ist, wird in den Headern der ausgehenden Nachricht angezeigt, dass der Nachrichtentext das angegebene Format besitzt. Der Parameter kann einen der folgenden Werte enthalten:  
  
-   TEXT  
  
-   HTML  
  
 Der Standardwert ist TEXT.  
  
`[ @importance = ] 'importance'` Ist die Wichtigkeit der Meldung. Der Parameter ist vom Typ **varchar(6)** . Der Parameter kann einen der folgenden Werte enthalten:  
  
-   Niedrig  
  
-   Normal  
  
-   Hoch  
  
 Der Standardwert ist Normal.  
  
`[ @sensitivity = ] 'sensitivity'` Ist die Vertraulichkeit der Nachricht. Der Parameter ist vom Typ **varchar(12)** . Der Parameter kann einen der folgenden Werte enthalten:  
  
-   Normal  
  
-   Persönlich  
  
-   Privat  
  
-   Vertraulich  
  
 Der Standardwert ist Normal.  
  
`[ @file_attachments = ] 'file_attachments'` Ist eine durch Semikolons getrennte Liste der Dateinamen, die an die e-Mail-Nachricht anfügen. Die Dateien in der Liste müssen als absolute Pfade angegeben sein. Die Anlagenliste ist vom Typ **nvarchar(max)** . Standardmäßig beschränkt Datenbank-E-Mail Dateianlagen auf 1 MB pro Datei.  
  
`[ @query = ] 'query'` Ist eine auszuführende Abfrage. Die Ergebnisse der Abfrage können als Datei angefügt oder in den Text der E-Mail-Nachricht eingeschlossen werden. Die Abfrage ist vom Typ **nvarchar(max)** , und kann eine beliebige gültige enthalten [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen. Beachten Sie, dass die Abfrage, in einer separaten Sitzung, lokale Variablen in der aufrufenden Skript ausgeführt wird **Sp_send_dbmail** sind für die Abfrage nicht verfügbar.  
  
`[ @execute_query_database = ] 'execute_query_database'` Wird der Datenbankkontext, in dem die gespeicherte Prozedur die Abfrage ausgeführt wird. Der Parameter ist vom Typ **Sysname**, hat den Standardwert der aktuellen Datenbank. Dieser Parameter gilt nur für Wenn **@query** angegeben ist.  
  
`[ @attach_query_result_as_file = ] attach_query_result_as_file` Gibt an, ob das Resultset der Abfrage als Anlage zurückgegeben wird. *Attach_query_result_as_file* ist vom Typ **Bit**, hat den Standardwert 0.  
  
 Wenn der Wert 0 ist, sind die Ergebnisse der Abfrage im Text der e-Mail-Nachricht, hinter dem Inhalt des enthalten die **@body** Parameter. Ist der Wert 1, werden die Ergebnisse als Anlage zurückgegeben. Dieser Parameter gilt nur für Wenn **@query** angegeben ist.  
  
`[ @query_attachment_filename = ] query_attachment_filename` Gibt den Dateinamen an, die für das Resultset der abfrageanlage verwendet. *Query_attachment_filename* ist vom Typ **nvarchar(255)** , hat den Standardwert NULL. Dieser Parameter wird ignoriert, wenn *Attach_query_result* ist 0. Wenn *Attach_query_result* ist 1, und dieser Parameter NULL ist, Datenbank-e-Mails erstellt einen beliebigen Dateinamen.  
  
`[ @query_result_header = ] query_result_header` Gibt an, ob die Abfrageergebnisse Spaltenheader einschließen. Der Wert für query_result_header ist vom Typ **Bit**. Bei einem Wert von 1 enthalten die Abfrageergebnisse Spaltenheader. Bei einem Wert von 0 enthalten die Abfrageergebnisse keine Spaltenheader. Dieser Parameter ist standardmäßig **1**. Dieser Parameter gilt nur für Wenn **@query** angegeben ist.  
 
   >[!NOTE]
   > Der folgende Fehler kann auftreten, wenn Sie festlegen @query_result_header auf 0 und Einstellung @query_no_truncate auf 1:
   > <br> Msg 22050, Ebene 16, Status 1, Zeile 12: Fehler beim Initialisieren der Fehlernummer-2147024809 Sqlcmd-Bibliothek.
  
`[ @query_result_width = ] query_result_width` Ist die Linienstärke in Zeichen zum Formatieren der Ergebnisse der Abfrage. Die *Query_result_width* ist vom Typ **Int**, mit dem Standardwert 256. Der Wert muss zwischen 10 and 32767 liegen. Dieser Parameter gilt nur für Wenn **@query** angegeben ist.  
  
`[ @query_result_separator = ] 'query_result_separator'` Das Zeichen, der zum Trennen der Spalten in der Ausgabe der Abfrage verwendet wird. Das Trennzeichen ist vom Typ **char(1)** . Der Standardwert ist ' ' (Leerzeichen).  
  
`[ @exclude_query_output = ] exclude_query_output` Gibt an, ob die Ausgabe der abfrageausführung in die e-Mail-Nachricht zurückgegeben werden soll. **Exclude_query_output** bit und hat den Standardwert 0. Wenn dieser Parameter gleich 0 ist, der die **Sp_send_dbmail** gespeicherte Prozedur gibt die Meldung, die als Ergebnis der Ausführung der Abfrage zurückgegeben werden, in der Konsole. Wenn dieser Parameter gleich 1, die Ausführung der **Sp_send_dbmail** gespeicherte Prozedur wird keine der abfrageausführungsnachrichten auf der Konsole gedruckt.  
  
`[ @append_query_error = ] append_query_error` Gibt an, ob die E-mail zu senden, wenn einen Fehler, aus der Abfrage zurückgibt der **@query** Argument. **Append_query_error** ist **Bit**, hat den Standardwert 0. Ist dieser Parameter auf 1 festgelegt, sendet Datenbank-E-Mail die E-Mail-Nachricht und bezieht die Abfragefehlermeldung in den Text der E-Mail-Nachricht ein. Wenn dieser Parameter 0 ist, Datenbank-e-Mails sendet keine e-Mail-Nachricht, und **Sp_send_dbmail** endet mit dem Rückgabecode 1, um einen Fehler.  
  
`[ @query_no_truncate = ] query_no_truncate` Gibt an, ob die Abfrage mit der Option ausgeführt, der vermeidet, Abschneiden von Datentypen für große variabler Länge (**varchar(max)** , **nvarchar(max)** , **'varbinary(max)'** **Xml**, **Text**, **Ntext**, **Image**, und eine benutzerdefinierte Datentypen). Wenn fetgelegt, enthalten die Abfrageergebnisse keine Spaltenheader. Die *Query_no_truncate* Wert ist vom Typ **Bit**. Bei einem Wert von 0 oder wenn kein Wert angegeben ist, werden die Spalten in der Abfrage auf 256 Zeichen abgeschnitten. Bei einem Wert von 1 werden die Spalten in der Abfrage nicht abgeschnitten. Dieser Parameter hat den Standardwert 0.  
  
> [!NOTE]  
>  Bei Verwendung mit großen Mengen von Daten, die @**Query_no_truncate** Option werden zusätzliche Ressourcen belegt, und kann die serverleistung beeinträchtigen.  
  
`[ @query_result_no_padding ] @query_result_no_padding` Der Typ ist bit. Die Standardeinstellung ist 0. Wenn Sie auf 1 festlegen, werden die Ergebnisse der Abfrage reduziert sich die Dateigröße u. u. nicht aufgefüllt. Setzen Sie @query_result_no_padding auf 1 und Festlegen der @query_result_width -Parameter der @query_result_no_padding Parameter überschreibt die @query_result_width Parameter.  
  
 In diesem Fall tritt kein Fehler auf.  
 
  >[!NOTE]
  > Der folgende Fehler kann auftreten, wenn Sie festlegen @query_result_no_padding 1 und einen Parameter für die Bereitstellung @query_no_truncate:
  > <br> Msg 22050, Ebene 16, Status 1, Zeile 0: Fehler beim Ausführen der Abfrage, da die @query_result_no_append und @query_no_truncate Optionen schließen sich gegenseitig. 
  
 Setzen Sie die @query_result_no_padding auf 1 und Festlegen der @query_no_truncate Parameter, ein Fehler ausgelöst wird.  
  
`[ @mailitem_id = ] mailitem_id [ OUTPUT ]` Der optionale Ausgabeparameter gibt den *Mailitem_id* der Nachricht. Die *Mailitem_id* ist vom Typ **Int**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Ein Rückgabecode von 0 steht für Erfolg. Ein beliebiger anderer Wert steht für Fehler. Der Fehlercode für die fehlgeschlagene Anweisung befindet sich in der @@ERROR Variable.  
  
## <a name="result-sets"></a>Resultsets  
 Bei Erfolg wird die Nachricht "E-Mail in der Warteschlange" zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Vor der Verwendung muss Datenbank-e-Mails mithilfe des Datenbank-Mail-Assistenten, aktiviert sein oder **Sp_configure**.  
  
 **Sysmail_stop_sp** beendet Sie Datenbank-e-Mails durch das Beenden von Service Broker-Objekte, die vom externen Programm verwendet. **Sp_send_dbmail** nimmt e-Mail weiterhin, wenn Datenbank-e-Mails mit beendet wird **Sysmail_stop_sp**. Starten Sie Datenbank-E-Mail mithilfe von **sysmail_start_sp**.  
  
 Wenn **@profile** nicht angegeben ist, **Sp_send_dbmail** ein Standardprofil verwendet. Falls der Benutzer, der die E-Mail-Nachricht sendet, über ein privates Standardprofil verfügt, verwendet Datenbank-E-Mail dieses Profil. Wenn der Benutzer keine als privates Standardprofil verfügt **Sp_send_dbmail** als öffentliches Standardprofil verwendet. Wenn es keine als privates Standardprofil für den Benutzer und kein öffentliches Standardprofil **Sp_send_dbmail** gibt einen Fehler zurück.  
  
 **Sp_send_dbmail** unterstützt keine e-Mail-Nachrichten ohne Inhalt. Um eine e-Mail-Nachricht zu senden, müssen Sie angeben, mindestens eine der **@body** , **@query** , **@file_attachments** , oder **@subject** . Andernfalls **Sp_send_dbmail** gibt einen Fehler zurück.  
  
 Datenbank-E-Mail verwendet den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Sicherheitskontext des aktuellen Benutzers, um den Dateizugriff zu steuern. Aus diesem Grund mit authentifizierten Benutzern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung kann nicht angefügt werden Dateien mit **@file_attachments** . Windows lässt nicht zu, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldeinformationen von einem Remotecomputer für einen anderen Remotecomputer bereitstellt. Aus diesem Grund kann Datenbank-E-Mail möglicherweise Dateien aus einer Netzwerkfreigabe nicht anfügen, wenn der Befehl von einem anderen Computer als dem Computer mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
 Wenn beide **@query** und **@file_attachments** angegeben sind und die Datei wurde nicht gefunden, die Abfrage weiterhin ausgeführt, aber die E-mail nicht gesendet.  
  
 Wird eine Abfrage angegeben, wird das Resultset als Inlinetext formatiert. Binärdaten im Ergebnis werden im hexadezimalen Format gesendet.  
  
 Die Parameter **@recipients** , **@copy_recipients** , und **@blind_copy_recipients** sind durch Semikolons getrennte Listen der e-Mail-Adressen. Mindestens eine der folgenden Parameter bereitgestellt werden muss, oder **Sp_send_dbmail** gibt einen Fehler zurück.  
  
 Beim Ausführen **Sp_send_dbmail** ohne Transaktionskontext, Datenbank-e-Mails wird gestartet und führt einen Commit für eine implizite Transaktion. Beim Ausführen **Sp_send_dbmail** von innerhalb einer vorhandenen Transaktion, Datenbank-e-Mails basiert auf dem Benutzer, die ein commit oder ein Rollback von Änderungen. Es wird keine innere Transaktion gestartet.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen für **Sp_send_dbmail** standardmäßig alle Mitglieder der der **DatabaseMailUser** -Datenbankrolle in der **Msdb** Datenbank. Aber wenn der Benutzer sendet die Nachricht besitzt keine Berechtigung zum Verwenden des Profils für die Anforderung **Sp_send_dbmail** einen Fehler zurück und sendet die Nachricht nicht.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-sending-an-e-mail-message"></a>A. Senden einer E-Mail-Nachricht  
 In diesem Beispiel sendet eine e-Mail-Nachricht an Ihr Freund die e-Mail-Adresse `myfriend@Adventure-Works.com`. Die Nachricht hat den Betreff `Automated Success Message`. Der Nachrichtentext enthält den Satz `'The stored procedure finished successfully'`.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @body = 'The stored procedure finished successfully.',  
    @subject = 'Automated Success Message' ;  
```  
  
### <a name="b-sending-an-e-mail-message-with-the-results-of-a-query"></a>B. Senden einer E-Mail-Nachricht mit den Ergebnissen einer Abfrage  
 In diesem Beispiel sendet eine e-Mail-Nachricht an Ihr Freund die e-Mail-Adresse `yourfriend@Adventure-Works.com`. Die Nachricht hat den Betreff `Work Order Count` und führt eine Abfrage aus, die die Anzahl von Arbeitsaufträgen mit einem `DueDate`-Wert kleiner als zwei Tage nach dem 30. April 2004 anzeigt. Das Ergebnis wird als Textdatei von Datenbank-E-Mail angefügt.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @query = 'SELECT COUNT(*) FROM AdventureWorks2012.Production.WorkOrder  
                  WHERE DueDate > ''2004-04-30''  
                  AND  DATEDIFF(dd, ''2004-04-30'', DueDate) < 2' ,  
    @subject = 'Work Order Count',  
    @attach_query_result_as_file = 1 ;  
```  
  
### <a name="c-sending-an-html-e-mail-message"></a>C. Senden einer E-Mail-Nachricht im HTML-Format  
 In diesem Beispiel sendet eine e-Mail-Nachricht an Ihr Freund die e-Mail-Adresse `yourfriend@Adventure-Works.com`. Die Nachricht hat den Betreff `Work Order List` und enthält ein HTML-Dokument, das die Anzahl von Arbeitsaufträgen mit einem `DueDate`-Wert kleiner als zwei Tage nach dem 30. April 2004 anzeigt. Das Ergebnis wird im HTML-Format von Datenbank-E-Mail gesendet.  
  
```  
DECLARE @tableHTML  NVARCHAR(MAX) ;  
  
SET @tableHTML =  
    N'<H1>Work Order Report</H1>' +  
    N'<table border="1">' +  
    N'<tr><th>Work Order ID</th><th>Product ID</th>' +  
    N'<th>Name</th><th>Order Qty</th><th>Due Date</th>' +  
    N'<th>Expected Revenue</th></tr>' +  
    CAST ( ( SELECT td = wo.WorkOrderID,       '',  
                    td = p.ProductID, '',  
                    td = p.Name, '',  
                    td = wo.OrderQty, '',  
                    td = wo.DueDate, '',  
                    td = (p.ListPrice - p.StandardCost) * wo.OrderQty  
              FROM AdventureWorks.Production.WorkOrder as wo  
              JOIN AdventureWorks.Production.Product AS p  
              ON wo.ProductID = p.ProductID  
              WHERE DueDate > '2004-04-30'  
                AND DATEDIFF(dd, '2004-04-30', DueDate) < 2   
              ORDER BY DueDate ASC,  
                       (p.ListPrice - p.StandardCost) * wo.OrderQty DESC  
              FOR XML PATH('tr'), TYPE   
    ) AS NVARCHAR(MAX) ) +  
    N'</table>' ;  
  
EXEC msdb.dbo.sp_send_dbmail @recipients='yourfriend@Adventure-Works.com',  
    @subject = 'Work Order List',  
    @body = @tableHTML,  
    @body_format = 'HTML' ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail Configuration Objects](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Datenbank-e-Mails gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)  
  
  
