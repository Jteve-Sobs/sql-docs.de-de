---
description: DataControl-Objekt (RDS)
title: DataControl-Objekt (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl
- RDS.DataControl
helpviewer_keywords:
- DataControl object [ADO]
ms.assetid: d85ea4fc-451c-436e-97b8-58f92b149dd0
author: rothja
ms.author: jroth
ms.openlocfilehash: 6643fe176ef6281afa39845310812f5f6981d16b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439142"
---
# <a name="datacontrol-object-rds"></a>DataControl-Objekt (RDS)
Bindet ein Datenabfrage- [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) an ein oder mehrere Steuerelemente (z. b. ein Textfeld, ein Raster Steuerelement oder ein Kombinations Feld), um die **Recordsetdaten** auf einer Webseite anzuzeigen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="https://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
</OBJECT>  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Die Klassen-ID für das **RDS. Das DataControl** -Objekt ist BD96C556-65A3-11D0-983A-00C04FC29E33.  
  
> [!NOTE]
>  Wenn Sie eine Fehlermeldung erhalten, die ein RDS-ist [. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oder **RDS. Das DataControl** -Objekt wird nicht geladen. Stellen Sie sicher, dass Sie die richtige Klassen-ID verwenden. Die Klassen-IDs für diese Objekte haben sich von Version 1,0 und 1,1 geändert. Beachten Sie auch, dass auch Spalten, die NULL-Werte zulassen, festgelegt werden müssen, wenn Sie das **RDS-DataControl** -Objekt verwenden.  
  
 Für ein einfaches Szenario müssen Sie nur die **SQL**-, **Connect**-und **Server** -Eigenschaften des RDS festlegen **. DataControl** -Objekt, das automatisch das Standard Geschäftsobjekt [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)aufruft.  
  
 Alle Eigenschaften im **RDS. DataControl** ist optional, da benutzerdefinierte Geschäftsobjekte ihre Funktionalität ersetzen können.  
  
> [!NOTE]
>  Wenn Sie mehrere Ergebnisse Abfragen, wird nur das erste [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) zurückgegeben. Wenn mehrere Resultsets benötigt werden, weisen Sie jede der eigenen **DataControl**zu. Ein Beispiel für eine Abfrage für mehrere Ergebnisse könnte wie folgt lauten: `"Select * from Authors, Select * from Topics"`  
  
 Hinzufügen von "DFMode = 20;" zu ihrer Verbindungs Zeichenfolge, wenn Sie das **RDS verwenden. Das DataControl** -Objekt kann die Leistung des Servers beim Aktualisieren von Daten verbessern. Mit dieser Einstellung verwendet das **RDSServer. DataFactory** -Objekt auf dem Server einen weniger ressourcenintensiven Modus. Die folgenden Funktionen sind in dieser Konfiguration jedoch nicht verfügbar:  
  
-   Verwenden von parametrisierten Abfragen.  
  
-   Abrufen von Parameter-oder Spalten Informationen vor dem Aufrufen der **Execute** -Methode.  
  
-   Die **Transact-Updates** werden auf **true**festgelegt.  
  
-   Zeilen Status wird erhalten.  
  
-   Aufrufen der [Resync](../../../ado/reference/ado-api/resync-method.md) -Methode.  
  
-   Aktualisieren (explizit oder automatisch) über die Eigenschaft " [Resync aktualisieren](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) ".  
  
-   Festlegen der Eigenschaften von **Befehlen** oder [Recordsets](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) .  
  
-   Verwenden von **adCmdTableDirect**.  
  
 Das **RDS. Das DataControl** -Objekt wird standardmäßig im asynchronen Modus ausgeführt. Wenn Sie für Ihre Anwendung eine synchrone Ausführung benötigen, legen Sie den [ExecuteOptions](../../../ado/reference/rds-api/executeoptions-property-rds.md) -Parameter auf **adcExecSync** und den [FetchOptions](../../../ado/reference/rds-api/fetchoptions-property-rds.md) -Parameter auf **adcFetchUpFront**fest, wie im folgenden Beispiel gezeigt.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"   
    ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="https://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
   <PARAM NAME="ExecuteOptions" VALUE="1">   <PARAM NAME="FetchOptions" VALUE="1">  
</OBJECT>  
```  
  
 Verwenden Sie ein **RDS. DataControl** -Objekt, um die Ergebnisse einer einzelnen Abfrage mit einem oder mehreren visuellen Steuerelementen zu verknüpfen. Nehmen Sie beispielsweise an, Sie codieren eine Abfrage, die Kundendaten anfordert, z. b. Name, Residenz, Geburts Ort, Alter und Prioritäts Kunden Status. Sie können ein einzelnes **RDS verwenden. DataControl** -Objekt, um den Namen, das Alter und die Region eines Kunden in drei separaten Textfeldern anzuzeigen. Prioritäts Status von Kunden in einem Kontrollkästchen und alle Daten in einem Raster Steuerelement.  
  
 Verwenden Sie unterschiedliche **RDS. DataControl** -Objekte, mit denen die Ergebnisse mehrerer Abfragen mit verschiedenen visuellen Steuerelementen verknüpft werden können. Nehmen Sie beispielsweise an, Sie verwenden eine Abfrage, um Informationen zu einem Kunden abzurufen, und eine zweite Abfrage, um Informationen zu den vom Kunden erworbenen Waren zu erhalten. Sie möchten die Ergebnisse der ersten Abfrage in drei Textfeldern und einem Kontrollkästchen sowie die Ergebnisse der zweiten Abfrage in einem Raster Steuerelement anzeigen. Wenn Sie das Standard Geschäftsobjekt (**RDSServer. DataFactory**) verwenden, müssen Sie die folgenden Schritte ausführen:  
  
-   Fügen Sie zwei **RDS hinzu. DataControl** -Objekte auf Ihrer Webseite.  
  
-   Schreiben Sie zwei Abfragen, eine für jede **SQL** -Eigenschaft der beiden **RDS. DataControl** -Objekte. Ein **RDS. Das DataControl** -Objekt enthält eine SQL-Abfrage, die Kundeninformationen anfordert. die zweite enthält eine Abfrage, die eine Liste der vom Kunden erworbenen Waren anfordert.  
  
-   Geben Sie in den Objekt Tags der einzelnen gebundenen Steuerelemente den Datafld-Wert an, um die Werte für die Daten festzulegen, die Sie in jedem visuellen Steuerelement anzeigen möchten.  
  
 Es gibt keine Anzahl Beschränkung für die Anzahl von **RDS. DataControl** -Objekte, die Sie mithilfe von Objekt Tags auf einer einzelnen Webseite einbetten können.  
  
 Wenn Sie das **RDS definieren. DataControl** -Objekt auf einer Webseite verwenden Sie **Höhen** -und **breiten** Werte ungleich 0 (null), wie z. b. 1 (um die Aufnahme zusätzlicher Leerzeichen zu vermeiden).  
  
 Remote Data Service-Client Komponenten sind bereits als Teil von Internet Explorer 4,0 enthalten. Daher müssen Sie keinen CodeBase-Parameter in Ihren **RDS einschließen. DataControl** -Objekttag.  
  
 Mit Internet Explorer 4,0 oder höher können Sie Daten mithilfe von HTML-Steuerelementen und ActiveX-® Steuerelementen nur dann binden, wenn Sie als Apartment Modell-Steuerelemente markiert sind.  
  
> [!NOTE]
>  **Microsoft Visual Basic-Benutzer** Das **RDS. DataControl** ist für die Skripterstellung sicher und wird nur in webbasierten Anwendungen verwendet. Eine Visual Basic Client Anwendung ist nicht erforderlich.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [DataControl-Objekt (RDS) – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/rds-api/datacontrol-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataControl-Objekt – Beispiel (VBScript)](../../../ado/reference/rds-api/datacontrol-object-example-vbscript.md)






















