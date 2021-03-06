---
description: Microsoft OLE DB-Anbieter für Microsoft Active Directory Service
title: Microsoft OLE DB-Anbieter für Microsoft Active Directory Service | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADSI provider [ADO]
- Active Directory Service Interfaces provider [ADO]
- providers [ADO], OLE DB provider for Active Directory service
- OLE DB provider for Active Directory service [ADO]
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
author: rothja
ms.author: jroth
ms.openlocfilehash: f5a2513d8440adedaa0faecae2b544c9ea99bef0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454122"
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Microsoft OLE DB-Anbieter für Microsoft Active Directory Service
Der ADSI-Anbieter (Active Directory Service Interfaces) ermöglicht ADO das Herstellen einer Verbindung mit heterogenen Verzeichnisdiensten über ADSI. Dies ermöglicht ADO-Anwendungen einen schreibgeschützten Zugriff auf die Verzeichnisdienste Microsoft Windows NT 4,0 und Microsoft Windows 2000, zusätzlich zu allen LDAP-kompatiblen Verzeichnisdienst-und Novell-Verzeichnisdiensten. ADSI selbst basiert auf einem Anbieter Modell. wenn es also einen neuen Anbieter gibt, der Zugriff auf ein anderes Verzeichnis bietet, kann die ADO-Anwendung nahtlos darauf zugreifen. Der ADSI-Anbieter ist frei Thread-und Unicode-fähig.  
  
## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge  
 Legen Sie das **Provider** -Argument der [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf Folgendes fest, um eine Verbindung mit diesem Anbieter herzustellen:  
  
```vb
ADSDSOObject  
```  
  
 Wenn Sie die [Provider](../../../ado/reference/ado-api/provider-property-ado.md) -Eigenschaft lesen, wird auch diese Zeichenfolge zurückgegeben.  
  
## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge  
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet wie folgt:  
  
```vb
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 Die Zeichenfolge besteht aus den folgenden Schlüsselwörtern.  
  
|Schlüsselwort|Beschreibung|  
|-------------|-----------------|  
|**Anbieter**|Gibt den OLE DB Anbieter für Active Directory Dienst an.|  
|**Benutzer-ID**|Gibt den Benutzernamen an. Wenn dieses Schlüsselwort weggelassen wird, wird die aktuelle Anmeldung verwendet.|  
|**Kennwort**|Gibt das Benutzer Kennwort an. , Wenn dieses Schlüsselwort ausgelassen wird. Anschließend wird die aktuelle Anmeldung verwendet.|  
  
> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.  
  
## <a name="command-text"></a>Befehlstext  
 Eine vierteilige Befehls Text Zeichenfolge wird vom Anbieter in der folgenden Syntax erkannt:  
  
```vb
"Root; Filter; Attributes[; Scope]"  
```  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|*Fasst*|Gibt das **ADsPath** -Objekt an, aus dem die Suche gestartet werden soll (d. h. der Stamm der Suche).|  
|*Filter*|Gibt den Suchfilter im RFC 1960-Format an.|  
|*Attribute*|Gibt eine durch Trennzeichen getrennte Liste von Attributen an, die zurückgegeben werden sollen.|  
|*Umfang*|Optional. Eine **Zeichenfolge** , die den Suchbereich angibt. Dabei kann es sich um eine der folgenden Methoden handeln:<br /><br /> -Base: sucht nur nach dem Basisobjekt (Stamm der Suche).<br />-Onelevel-nur eine Ebene suchen.<br />-Subtree: Durchsuchen Sie die gesamte Unterstruktur.|  
  
 Beispiel:  
  
```vb
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Der Anbieter unterstützt auch SQL SELECT für den Befehls Text. Beispiel:  
  
```vb
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Der Anbieter akzeptiert keine Aufrufe gespeicherter Prozeduren oder einfache Tabellennamen (die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) -Eigenschaft ist z. b. immer **adCmdText**). Eine ausführlichere Beschreibung der Befehls Textelemente finden Sie in der Dokumentation zu den Active Directory-Dienst Schnittstellen.  
  
## <a name="recordset-behavior"></a>Recordsetverhalten  
 In der folgenden Tabelle sind die verfügbaren Funktionen für ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt aufgeführt, das mit diesem Anbieter geöffnet wurde. Nur der statische Cursortyp (**adopdestatic**) ist verfügbar.  
  
 Weitere Informationen zum **recordsetverhalten** ihrer Anbieter Konfiguration erhalten Sie, wenn Sie die [unterstützte](../../../ado/reference/ado-api/supports-method.md) Methode ausführen und die [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung des **Recordsets** auflisten, um zu bestimmen, ob anbieterspezifische dynamische Eigenschaften vorhanden sind.  
  
 **Verfügbarkeit von Eigenschaften des Standard-ADO-Recordsets:**  
  
|Eigenschaft|Verfügbarkeit|  
|--------------|------------------|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|Lesen/Schreiben|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|Lesen/Schreiben|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|schreibgeschützt|  
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|  
|[Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md)|Lesen/Schreiben|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|Lesen/Schreiben|  
|[CursorLocation –](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|immer **AD-eServer**|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Always **adop-static**|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|immer **adEditNone**|  
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|  
|[Filter](../../../ado/reference/ado-api/filter-property.md)|Lesen/Schreiben|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Lesen/Schreiben|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|nicht verfügbar|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|Lesen/Schreiben|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|schreibgeschützt|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|Lesen/Schreiben|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|schreibgeschützt|  
|[Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md)|Lesen/Schreiben|  
|[State](../../../ado/reference/ado-api/state-property-ado.md)|schreibgeschützt|  
|[Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)|schreibgeschützt|  
  
 **Verfügbarkeit der standardmäßigen ADO-recordsetmethoden:**  
  
|Methode|Verfügbar?|  
|------------|----------------|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Nein|  
|[Abbrechen](../../../ado/reference/ado-api/cancel-method-ado.md)|Nein|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Nein|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Nein|  
|[Klonen](../../../ado/reference/ado-api/clone-method-ado.md)|Ja|  
|[Schließen](../../../ado/reference/ado-api/close-method-ado.md)|Ja|  
|[Löschen](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Nein|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Ja|  
|[Verschieben](../../../ado/reference/ado-api/move-method-ado.md)|Ja|  
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Ja|  
|[Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Ja|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Ja|  
|[Erneut synchronisieren](../../../ado/reference/ado-api/resync-method.md)|Ja|  
|[Unterstützt](../../../ado/reference/ado-api/supports-method.md)|Ja|  
|[Aktualisieren](../../../ado/reference/ado-api/update-method.md)|Nein|  
|[Update Batch](../../../ado/reference/ado-api/updatebatch-method.md)|Nein|  
  
 Weitere Informationen zu ADSI und den Besonderheiten des Anbieters finden Sie in der Dokumentation zu den Active Directory-Dienst Schnittstellen oder auf der ADSI-Webseite.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CommandType-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [ConnectionString-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Provider-Eigenschaft (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Supports-Methode](../../../ado/reference/ado-api/supports-method.md)
