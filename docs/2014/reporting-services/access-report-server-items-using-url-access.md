---
title: Zugreifen auf Berichtsserverelemente über den URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb841d8014bd1a66d533c10c4740c016bb13e737
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66110099"
---
# <a name="access-report-server-items-using-url-access"></a>Zugreifen auf Berichtsserverelemente über den URL-Zugriff
  In diesem Thema wird beschrieben, wie Sie in einer Berichtsserver-Datenbank oder auf einer SharePoint-Website unter Verwendung von *rs:Befehl*=*Wert*auf Katalogelemente mit unterschiedlichen Typen zugreifen.  
  
 Es ist nicht erforderlich, diese Parameterzeichenfolge hinzuzufügen. Wenn Sie sie weglassen, wertet der Berichtsserver den Elementtyp aus und wählt den entsprechenden Parameterwert automatisch aus. Durch die Verwendung der *rs:Command*=*Value* -Zeichenfolge in der URL verbessert sich jedoch die Leistung des Berichtsservers.  
  
 Beachten Sie in den Beispielen unten die `_vti_bin` -Proxysyntax. Weitere Informationen zum Verwenden der Proxysyntax finden Sie unter [URL Access Parameter Reference](url-access-parameter-reference.md).  
  
## <a name="access-a-report"></a>Zugreifen auf einen Bericht  
 Um einen Bericht im Browser anzuzeigen, verwenden Sie den *RS: Command*=-*Rendering* -Parameter. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Es ist wichtig, dass die URL die `_vti_bin` -Proxysyntax zur Weiterleitung der Anforderung über SharePoint sowie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -HTTP-Proxy enthält. Durch den Proxy wird der HTTP-Anforderung Kontext hinzugefügt. Dieser ist erforderlich, damit der Bericht auf Berichtsservern im SharePoint-Modus ordnungsgemäß ausgeführt wird.  
  
## <a name="access-a-resource"></a>Zugreifen auf eine Ressource  
 Verwenden Sie den *RS: Command*=*GetResourceContents* -Parameter, um auf eine Ressource zuzugreifen. Wenn die Ressource mit dem Browser kompatibel ist (z. b. ein Bild), wird Sie im Browser geöffnet. Andernfalls werden Sie aufgefordert, die Datei oder Ressource zu öffnen oder auf dem Datenträger zu speichern.  
  
 `Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>Zugreifen auf eine Datenquelle  
 Um auf eine Datenquelle zuzugreifen, verwenden Sie den Parameter *RS: Command*=*GetDataSourceContents* . Wenn Ihr Browser XML unterstützt, wird die Datenquellendefinition angezeigt, wenn Sie ein für die Datenquelle authentifizierter Benutzer mit der Berechtigung `Read Contents` sind. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 Die XML-Struktur kann Ähnlichkeit mit folgendem Beispiel haben:  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 Die Verbindungszeichenfolge wird auf Grundlage der **SecureConnectionLevel** -Einstellung des Berichtsservers zurückgegeben. Weitere Informationen zur **SecureConnectionLevel** -Einstellung finden Sie unter [Using Secure Web Service Methods](report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Zugreifen auf den Inhalt eines Ordners  
 Um auf den Inhalt eines Ordners zuzugreifen, verwenden Sie den *RS: Command*=*GetChildren* -Parameter. Es wird eine generische Seite zur Ordnernavigation zurückgegeben, die Links zu den Unterordnern, Berichten, Datenquellen und Ressourcen im angeforderten Ordner enthält. Zum Beispiel:  
  
 `Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 Die angezeigte Benutzeroberfläche hat Ähnlichkeit mit dem Verzeichnissuchmodus, der von [!INCLUDE[msCoName](../includes/msconame-md.md)] IIS (Internet Information Server) verwendet wird. Die Versionsnummer, einschließlich der Buildnummer des Berichtsservers, wird ebenfalls unter der Ordnerliste angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [URL-Zugriff &#40;SSRS-&#41;](url-access-ssrs.md)   
 [URL-Zugriffsparameterreferenz](url-access-parameter-reference.md)  
  
  
