---
title: Projekteinstellungen (Typzuordnung) (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: cf426c69-6a8e-4d19-951d-6661d5ae2562
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 91498db5535c99c7c8afaba85efc35639510a079
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270004"
---
# <a name="project-settings-type-mapping-db2tosql"></a>Projekteinstellungen (Typzuordnung) (DB2ToSQL)
Die Seite Type Mapping der **Projekteinstellungen** Dialogfeld enthält Einstellungen, die anpassen, wie SSMA für DB2-Datentypen in konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen.  
  
Der Seite "Datentypzuordnung" steht in der **Projekteinstellungen** und **Projekt Standardeinstellungen** Dialogfelder.  
  
-   Die Einstellungen für alle zukünftigen SSMA-Projekten, auf die **Tools** klicken Sie auf **Projekt Standardeinstellungen**, wählen Sie die Migration-Projekttyp, die für die Einstellungen erforderlich sind, um angezeigt oder geändert werden, von **Migration Zielversion** Dropdownliste aus, und klicken Sie dann auf **Type Mapping** am unteren Rand im linken Bereich.  
  
-   Die Einstellungen für das aktuelle Projekt, auf die **Tools** klicken Sie im Menü **Projekteinstellungen**, und klicken Sie dann auf **Type Mapping** am unteren Rand im linken Bereich.  
  
Verwenden Sie zum Angeben von Einstellungen für das aktuelle Objekt oder eine Klasse von Objekten, die **Type Mapping** Registerkarte im primären SSMA-Fenster.  
  
## <a name="options"></a>Optionen  
Die folgende Tabelle zeigt die **Type Mapping** Registerkarte Optionen:  
  
**Quelltyp**  
Der zugeordnete DB2-Datentyp.  
  
**Zieltyp**  
Das Ziel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp für die angegebene DB2-Datentyps.  
  
Finden Sie in den Tabellen im nächsten Abschnitt für den standardmäßigen SSMA für DB2-datentypzuordnungen.  
  
**Hinzufügen**  
Klicken Sie auf diese Option, um einen Datentyp der Zuordnungsliste hinzuzufügen.  
  
**Bearbeiten**  
Klicken Sie auf diese Option, um den ausgewählten Datentyp in der Zuordnungsliste zu bearbeiten.  
  
**Entfernen**  
Klicken Sie auf diese Option, um die ausgewählte Zuordnung von Datentypen aus der Zuordnungsliste zu entfernen.  
  
**Standard wiederherstellen**  
Klicken Sie auf diese Option, um die Liste ' datentypzuordnung ' der SSMA-Standardwerte zurückzusetzen.  
  
## <a name="default-type-mappings"></a>Standard-Datentypzuordnungen  
In SSMA für DB2 können Sie benutzerdefinierte datentypzuordnungen für Argumente, Spalten, lokale Variablen und Rückgabewerten festlegen. Die standardzuordnung für Argumente und Rückgabetypen ist nahezu identisch.  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>Standard Argumenttyp und Typzuordnung Wert zurückgeben  
Die folgende Tabelle enthält die standardmäßige datentypzuordnung für Argumente und Rückgabewerte.  
  
|DB2-Datentyp|Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp|  
|-----------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|binary_integer|ssNoversion|  
|Blob|varbinary(max)|  
|boolean|bit|  
|char|varchar(max)|  
|char varying|varchar(max)|  
|character|varchar(max)|  
|character varying|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|Decimal|float[53]|  
|mit doppelter Genauigkeit|float[53]|  
|FLOAT|float[53]|  
|ssNoversion|ssNoversion|  
|integer|ssNoversion|  
|long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [\*... 8000]<sup>\*</sup>|Varbinary [\*]|  
|long raw[8001..\*]<sup>\*</sup>|varbinary(max)|  
|National char|nvarchar(max)|  
|National Char varying|nvarchar(max)|  
|nationale Zeichensätze|nvarchar(max)|  
|nationale Zeichensätze variieren.<sup>\*\*</sup>|nvarchar(max)|  
|nationale Zeichensätze varying<sup>\*</sup>|nvarchar(max)|  
|NCHAR|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|number|float[53]|  
|NUMERIC|float[53]|  
|nvarchar2|nvarchar(max)|  
|pls_integer|ssNoversion|  
|raw|varbinary(max)|  
|REAL|float[53]|  
|ROWID|UNIQUEIDENTIFIER|  
|Signtype|SMALLINT|  
|SMALLINT|SMALLINT|  
|String|varchar(max)|  
|timestamp|datetime2|  
|Zeitstempel mit der lokalen Zeitzone|datetimeoffset|  
|Zeitstempel mit Zeitzone|datetimeoffset|  
|UROWID|UNIQUEIDENTIFIER|  
|varchar|varchar(max)|  
|Varchar2|varchar(max)|  
|xmltype|xml|  
  
<sup>\*</sup> Zum Zurückgeben von Typ wertezuordnung nur gilt.  
  
<sup>\*\*</sup> Gilt für das Argument Typ nur zuordnen.  
  
### <a name="default-column-type-mapping"></a>Standardzuordnung für Spalten  
Die folgende Tabelle enthält die Standard-Typzuordnung für Spalten.  
  
|DB2-Datentyp|Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp|  
|-----------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|Blob|varbinary(max)|  
|char|char|  
|Char varying [\*... \*]|Varchar [\*]|  
|Char [\*... \*]|Char [\*]|  
|character|char|  
|unterschiedliche Zeichen [\*... \*]|Varchar [\*]|  
|Zeichen [\*... \*]|Char [\*]|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|DEC [\*... \*]|DEC [\*] [0]|  
|DEC [\*... \*][\*.. \*]|DEC [\*] [\*]|  
|Decimal|decimal[38][0]|  
|Dezimal [\*... \*]|Dezimal [\*] [0]|  
|Dezimal [\*... \*][\*.. \*]|decimal[\*][\*]|  
|mit doppelter Genauigkeit|float[53]|  
|FLOAT|float[53]|  
|"float" [\*... 53]|"float" [\*]|  
|float[54..\*]|float[53]|  
|ssNoversion|ssNoversion|  
|integer|ssNoversion|  
|long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [\*... 8000]|Varbinary [\*]|  
|long raw[8001..\*]|varbinary(max)|  
|long varchar|varchar(max)|  
|lange [\*... 8000]|Varchar [\*]|  
|long[8001..\*]|varchar(max)|  
|National char|NCHAR|  
|National Char varying [\*... \*]|Nvarchar [\*]|  
|National Char [\*... \*]|NCHAR [\*]|  
|nationale Zeichensätze|NCHAR|  
|nationale Zeichensätze zu unterschiedlichen [\*... \*]|Nvarchar [\*]|  
|nationale Zeichensätze [\*... \*]|NCHAR [\*]|  
|NCHAR|NCHAR|  
|NCHAR [\*]|NCHAR [\*]|  
|NCLOB|nvarchar(max)|  
|number|float[53]|  
|Anzahl [\*... \*]|numerische [\*]|  
|Anzahl [\*... \*][\*.. \*]|numeric[\*][\*]|  
|NUMERIC|NUMERIC|  
|numerische [\*... \*]|numerische [\*]|  
|numerische [\*... \*][\*.. \*]|numeric[\*][\*]|  
|NVARCHAR2 [\*... \*]|Nvarchar [\*]|  
|Rohdaten [\*... \*]|Varbinary [\*]|  
|REAL|float[53]|  
|ROWID|UNIQUEIDENTIFIER|  
|SMALLINT|SMALLINT|  
|timestamp|datetime2|  
|Zeitstempel mit der lokalen Zeitzone|datetimeoffset|  
|Zeitstempel mit der lokalen Zeitzone [\*... \*]|datetimeoffset[\*]|  
|Zeitstempel mit Zeitzone|datetimeoffset|  
|Zeitstempel mit Zeitzone [\*... \*]|datetimeoffset[\*]|  
|Timestamp [\*... \*]|datetime2 [\*]|  
|UROWID|UNIQUEIDENTIFIER|  
|UROWID [\*... \*]|UNIQUEIDENTIFIER|  
|Varchar [\*... \*]|Varchar [\*]|  
|VARCHAR2 [\*... \*]|Varchar [\*]|  
|Xmltype|xml|  
  
### <a name="default-local-variable-type-mapping"></a>Typ der lokalen Variablen der Standardzuordnung  
Die folgende Tabelle enthält die Standard-Typzuordnung für lokale Variablen.  
  
|DB2-Datentyp|Standard [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp|  
|-----------------|-------------------------------------------------------------------------|  
|Bfile|varbinary(max)|  
|binary_double|float[53]|  
|binary_float|float[53]|  
|binary_interger|ssNoversion|  
|Blob|varbinary(max)|  
|Boolean|bit|  
|Char|char|  
|Char varying [\*... 8000]|Varchar [\*]|  
|Char varying [8001..\*]|varchar(max)|  
|Char [\*... 8000]|Char [\*]|  
|char[8001..\*]|varchar(max)|  
|Zeichen|char|  
|unterschiedliche Zeichen [\*... 8000]|Varchar [\*]|  
|unterschiedliche Zeichen [8001..\*]|varchar(max)|  
|Zeichen [\*... 8000]|Char [\*]|  
|character[8001..\*]|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|DEC [\*... \*]|DEC [\*] [0]|  
|DEC [\*... \*][\*.. \*]|DEC [\*] [\*]|  
|Decimal|decimal[38][0]|  
|Dezimal [\*... \*]|Dezimal [\*] [0]|  
|Dezimal [\*... \*][\*.. \*]|decimal[\*][\*]|  
|mit doppelter Genauigkeit|float[53]|  
|float|float[53]|  
|"float" [\*... 53]|"float" [\*]|  
|float[54..\*]|float[53]|  
|int|ssNoversion|  
|Integer|ssNoversion|  
|ganze Zahl [\*... \*]|numerische [\*] [0]|  
|Long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [\*... 8000]|Varbinary [\*]|  
|long raw[8001..\*]|varbinary(max)|  
|National char|NCHAR|  
|National Char varying [\*... 4000]|Nvarchar [\*]|  
|National Char varying [4001..\*]|nvarchar(max)|  
|National Char [\*... 4000]|NCHAR [\*]|  
|National Char [4001..\*]|nvarchar(max)|  
|nationale Zeichensätze|NCHAR|  
|nationale Zeichensätze [\*... 4000]|Nvarchar [\*]|  
|nationale Zeichensätze [4001..\*]|nvarchar(max)|  
|nationale Zeichensätze zu unterschiedlichen [\*... 4000]|Nvarchar [\*]|  
|nationale Zeichensätze zu unterschiedlichen [4001..\*]|nvarchar(max)|  
|Nchar|NCHAR|  
|NCHAR [\*... 4000]|NCHAR [\*]|  
|nchar[4001..\*]|nvarchar(max)|  
|NCHAR unterschiedliche [\*... 4000]|Nvarchar [\*]|  
|NCHAR unterschiedliche [4001..\*]|nvarchar(max)|  
|Nclob|nvarchar(max)|  
|Number|float[53]|  
|Anzahl [\*... \*]|numerische [\*]|  
|Anzahl [\*... \*][\*.. \*]|numeric[\*][\*]|  
|Numerisch|numeric[38][0]|  
|numerische [\*... \*]|numerische [\*]|  
|numerische [\*... \*][\*.. \*]|numeric[\*][\*]|  
|NVARCHAR2 [\*... 4000]|Nvarchar [\*]|  
|NVARCHAR2 [4001..\*]|nvarchar(max)|  
|pls_integer|ssNoversion|  
|Rohdaten [\*... 8000]|Varbinary [\*]|  
|raw[8001..\*]|varbinary(max)|  
|Real|float[53]|  
|Rowid|UNIQUEIDENTIFIER|  
|Signtype|SMALLINT|  
|Smallint|SMALLINT|  
|Zeichenfolge [\*... 8000]|Varchar [\*]|  
|string[8001..\*]|varchar(max)|  
|timestamp|datetime2|  
|Zeitstempel mit der lokalen Zeitzone|datetimeoffset|  
|Zeitstempel mit Zeitzone|datetimeoffset|  
|Zeitstempel mit der lokalen Zeitzone [\*... \*]|datetimeoffset[\*]|  
|Zeitstempel mit Zeitzone [\*... \*]|datetimeoffset[\*]|  
|Timestamp [\*... \*]|datetime2 [\*]|  
|UROWID|UNIQUEIDENTIFIER|  
|UROWID [\*... \*]|UNIQUEIDENTIFIER|  
|Varchar [\*... 8000]|Varchar [\*]|  
|varchar[8001..\*]|varchar(max)|  
|VARCHAR2 [\*... 8000]|Varchar [\*]|  
|varchar2[8001..\*]|varcha(max)|  
|Xmltype|xml|  
  
## <a name="see-also"></a>Siehe auch  
[Referenz zur Benutzeroberfläche &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  
