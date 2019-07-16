---
title: Systembasistabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system base tables [SQL Server]
- hobt [SQL Server]
- base tables
ms.assetid: 31f2df90-651f-4699-8067-19f59b60904f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 43f5e96a280614d3f69472c7d794489bf1a5ba58
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029559"
---
# <a name="system-base-tables"></a>Systembasistabellen
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Systembasistabellen sind die zugrunde liegenden Tabellen, in denen die Metadaten für eine bestimmte Datenbank gespeichert werden. Die **master** Datenbank ist in dieser Hinsicht, da sie einige zusätzlichen Tabellen enthält, die in einer anderen Datenbank nicht gefunden werden. Diese Tabellen enthalten permanente Metadaten, deren Bereich serverweit ist.  
  
> [!IMPORTANT]  
>  Die Systembasistabellen werden nur in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verwendet und dienen nicht der allgemeinen Verwendung durch Kunden. Sie können geändert werden, und ihre Kompatibilität wird nicht garantiert.  
  
## <a name="system-base-table-metadata"></a>Metadaten-Systembasistabelle  
 Hat ein Benutzer die CONTROL, ALTER oder VIEW DEFINITION-Berechtigung für eine Datenbank verfügt über sehen Basistabelle Systemmetadaten auf die **sys.objects** -Katalogsicht angezeigt. Der Empfänger kann auch die Namen auflösen und Objekt-IDs der systembasistabellen mithilfe von integrierten Funktionen wie z. B. [OBJECT_NAME](../../t-sql/functions/object-name-transact-sql.md) und [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md).  
  
 Um eine Bindung zu einer Systembasistabelle herzustellen, muss ein Benutzer eine dedizierte Administratorverbindung (Dedicated Administrator Connection, DAC) zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufbauen. Der Versuch, eine SELECT-Abfrage aus einer Systembasistabelle auszuführen, ohne dass mithilfe von DAC eine Verbindung hergestellt wurde, löst einen Fehler aus.  
  
> [!IMPORTANT]  
>  Zugriff auf Systembasistabellen mithilfe von DAC ist nur für [!INCLUDE[msCoName](../../includes/msconame-md.md)]-Mitarbeiter und nicht für die Verwendung durch Kunden vorgesehen.  
  
## <a name="system-base-tables"></a>Systembasistabellen  
 In der folgenden Tabelle werden die Systembasistabellen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgeführt und beschrieben.  
  
|Basistabelle|Beschreibung|  
|----------------|-----------------|  
|**Sys.sysschobjs**|Ist in jeder Datenbank vorhanden. Jede Zeile stellt ein Objekt in der Datenbank dar.|  
|**Sys.sysbinobjs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Service Broker-Entität in der Datenbank. Service Broker-Entitäten schließen Folgendes ein:<br /><br /> Nachrichtentyp<br /><br /> Dienstvertrag<br /><br /> Dienst<br /><br /> Die Namen und Typen verwenden binäre Sortierung, die nicht geändert wird.|  
|**Sys.sysclsobjs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede klassifizierte Entität, für die die gleichen allgemeinen Eigenschaften gelten, darunter die folgenden:<br /><br /> Assembly<br /><br /> Sicherungsmedium<br /><br /> Volltextkatalog<br /><br /> Partitionsfunktion<br /><br /> Partitionsschema<br /><br /> Dateigruppe<br /><br /> Verbergungsschlüssel|  
|**Sys.sysnsobjs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Namespace-bezogene Entität. Diese Tabelle wird zum Speichern von XML-Auflistungsentitäten verwendet.|  
|**Sys.syscolpars**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Spalte in einer Tabelle, Sicht oder Tabellenwertfunktion. Sie enthält auch Zeilen für jeden Parameter einer Prozedur oder einer Funktion.|  
|**Sys.systypedsubobjs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede typisierte untergeordnete Entität. Nur Parameter für Partitionsfunktionen fallen in diese Kategorie.|  
|**Sys.sysidxstats**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden Index oder Statistiken für Tabellen und indizierte Sichten<br /><br /> Hinweis: Jeder Index (Heap ausgenommen), die eine Statistik, die den gleichen Namen wie der Index zugeordnet ist.|  
|**Sys.sysiscols**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden permanenten Index und jede Statistikspalte.|  
|**Sys.sysscalartypes**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden benutzerdefinierten oder Systemtyp.|  
|**Sys.sysdbreg**|Vorhanden ist, der **master** nur Datenbank. Enthält eine Zeile für jede registrierte Datenbank.|  
|**Sys.sysxsrvs**|Vorhanden ist, der **master** nur Datenbank. Enthält eine Zeile für jeden lokalen, Verbindungs- oder Remoteserver.|  
|**Sys.sysrmtlgns**|Diese systembasistabelle ist vorhanden, der **master** nur Datenbank. Enthält eine Zeile für jede Remoteanmeldungszuordnung. Sie wird für die Zuordnung von eingehenden lokalen Anmeldungen, die vorgeben, von einem entsprechenden Server zu stammen, an eine tatsächliche lokale Anmeldung verwendet.|  
|**Sys.syslnklgns**|Vorhanden ist, der **master** nur Datenbank. Enthält eine Zeile für jede verknüpfte Anmeldungszuordnung. Verknüpfte Anmeldungszuordnungen werden von Remoteprozeduraufrufen und verteilten Abfragen vom lokalen Server zum entsprechenden Verbindungsserver verwendet.|  
|**Sys.sysxlgns**|Vorhanden ist, der **master** nur Datenbank. Enthält eine Zeile für jeden Serverprinzipal.|  
|**Sys.sysdbfiles**|Ist in jeder Datenbank vorhanden. Wenn die Spalte **Dbid** NULL ist, steht die Zeile für eine Datei, die auf diese Datenbank gehört. In der **master** -Datenbank, die Spalte **Dbid** ungleich NULL sein kann. Wenn dies der Fall ist, steht die Zeile für eine Masterdatei.|  
|**Sys.sysusermsg**|Vorhanden ist, der **master** nur Datenbank. Jede Zeile stellt eine benutzerdefinierte Fehlermeldung dar.|  
|**Sys.sysprivs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Berechtigung auf Datenbank- oder Serverebene.<br /><br /> Hinweis: Auf Serverebene Berechtigungen werden gespeichert, der **master** Datenbank.|  
|**Sys.sysowners**|Ist in jeder Datenbank vorhanden. Jede Zeile stellt einen Datenbankprinzipal dar.|  
|**Sys.sysobjkeycrypts**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden symmetrischen Schlüssel, jede Verschlüsselung oder kryptografische Eigenschaft, die einem Objekt zugeordnet ist.|  
|**Sys.syscerts**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jedes Zertifikat in einer Datenbank.|  
|**Sys.sysasymkeys**|Ist in jeder Datenbank vorhanden. Jede Zeile stellt einen asymmetrischen Schlüssel dar.|  
|**Sys.ftinds**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden Volltextindex in der Datenbank.|  
|**Sys.sysxprops**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede erweiterte Eigenschaft.|  
|**Sys.sysallocunits**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Speicherzuordnungseinheit.|  
|**Sys.sysrowsets**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jedes Partitionsrowset für einen Index oder einen Heap.|  
|**Sys.sysrowsetrefs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden Index eines Rowsetverweises.|  
|**Sys.syslogshippers**|Vorhanden ist, der **master** nur Datenbank. Enthält eine Zeile für jeden Datenbankspiegelungszeugen.|  
|**Sys.sysremsvcbinds**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Remotedienstbindung.|  
|**Sys.sysconvgroup**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Dienstinstanz von Service Broker.|  
|**Sys.sysxmitqueue**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede Übertragungswarteschlange von Service Broker.|  
|**Sys.sysdesend**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden sendenden Endpunkt einer Service Broker-Konversation.|  
|**Sys.sysdercv**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden empfangenden Endpunkt einer Service Broker-Konversation.|  
|**Sys.sysendpts**|Vorhanden ist, der **master** nur Datenbank. Enthält eine Zeile für jeden im Server erstellten Endpunkt.|  
|**Sys.syswebmethods**|Vorhanden ist, der **master** nur Datenbank. Enthält eine Zeile für jede für einen SOAP-aktivierten HTTP-Endpunkt definierte SOAP-Methode, die auf dem Server erstellt wird.|  
|**Sys.sysqnames**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden Namespace oder jeden qualifizierten Namen für ein 4-Byte-ID-Token.|  
|**Sys.sysxmlcomponent**|Ist in jeder Datenbank vorhanden. Jede Zeile stellt eine XML-Schema-Komponente dar.|  
|**Sys.sysxmlfacet**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jedes XML-Facet (Beschränkung) der XML-Typdefinition.|  
|**Sys.sysxmlplacement**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede XML-Platzierung für XML-Komponenten.|  
|**Sys.syssingleobjrefs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden allgemeinen N-zu-1-Verweis.|  
|**Sys.sysmultiobjrefs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden allgemeinen N-zu-N-Verweis.|  
|**Sys.sysobjvalues**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jede allgemeine Werteigenschaft einer Entität.|  
|**Sys.sysguidrefs**|Ist in jeder Datenbank vorhanden. Enthält eine Zeile für jeden GUID-klassifizierten ID-Verweis.|  
  
  
