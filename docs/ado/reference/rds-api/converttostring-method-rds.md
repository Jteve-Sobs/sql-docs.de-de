---
description: ConvertToString-Methode (RDS)
title: ConvertTo String-Methode (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ConvertToString method [ADO]
ms.assetid: b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe
author: rothja
ms.author: jroth
ms.openlocfilehash: 58bfb25264c15f051bfd7144bdcaf01bbd1eda05
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439192"
---
# <a name="converttostring-method-rds"></a>ConvertToString-Methode (RDS)
Konvertiert ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in eine MIME-Zeichenfolge, die die Recordsetdaten darstellt.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataFactory*  
 Eine Objekt Variable, die ein [RDSServer. DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) -Objekt darstellt.  
  
 *Recordset*  
 Eine Objekt Variable, die ein **Recordset** -Objekt darstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie bei ASP-Dateien **convertdestring** , um das **Recordset** in eine HTML-Seite einzubetten, die auf dem Server generiert wird, um es an einen Client Computer zu transportieren.  
  
 **ConvertToString** lädt zuerst das **Recordset** in die Cursor Dienst Tabellen und generiert dann einen Stream im MIME-Format.  
  
 Auf dem Client kann der Remote Data Service die MIME-Zeichenfolge zurück in ein voll funktionsfähiges **Recordset**konvertieren. Es eignet sich gut für die Verarbeitung von weniger als 400 Daten Zeilen mit einer Breite von höchstens 1024 Byte pro Zeile. Sie sollten nicht zum Streamen von BLOB-Daten und großen Resultsets über HTTP verwendet werden. Für die Zeichenfolge wird keine Netzwerk Komprimierung durchgeführt, sodass sehr große Datasets im Vergleich zu dem vom Remote Datendienst als systemeigenen Transportprotokoll formatierten und vom Remote Datendienst bereitgestellten Format viel Zeit in Anspruch nehmen.  
  
> [!NOTE]
>  Wenn Sie Active Server Seiten verwenden, um die resultierende MIME-Zeichenfolge in eine Client-HTML-Seite einzubetten, beachten Sie, dass Versionen von VBScript vor Version 2,0 die Größe der Zeichenfolge auf 32 KB begrenzen. Wenn dieser Grenzwert überschritten wird, wird ein Fehler zurückgegeben. Behalten Sie den Abfrage Bereich relativ gering, wenn Sie MIME-Einbettungen über ASP-Dateien verwenden. Um dieses Problem zu beheben, laden Sie die neueste Version von VBScript von der Microsoft Windows Script Technologies-Website herunter.  
  
## <a name="applies-to"></a>Gilt für  
 [DataFactory-Objekt (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [ConvertTo String-Methode (Beispiel) (VB)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [ConvertToString-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)


