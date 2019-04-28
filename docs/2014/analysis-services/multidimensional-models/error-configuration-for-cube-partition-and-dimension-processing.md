---
title: Fehlerkonfiguration für die Cubes, Partition und Dimension verarbeiten (SSAS – mehrdimensional) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.cubeproperties.errorconfiguration.f1
- sql12.asvs.sqlserverstudio.dimensionproperties.errorconfiguration.f1
- sql12.asvs.sqlserverstudio.partitionproperties.errorconfiguration.f1
ms.assetid: 3f442645-790d-4dc8-b60a-709c98022aae
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ec0d1acbe1714159d6777f6cb91056e4e14b356
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62726035"
---
# <a name="error-configuration-for-cube-partition-and-dimension-processing-ssas---multidimensional"></a>Fehlerkonfiguration für die Verarbeitung von Cubes, Partitionen und Dimensionen (SSAS - mehrdimensional)
  Anhand von Fehlerkonfigurationseigenschaften für Cube-, Partitions- oder Dimensionsobjekte wird bestimmt, wie der Server während der Verarbeitung auf Datenintegritätsfehler reagiert. Diese Fehler werden normalerweise durch doppelte Schlüssel, fehlende Schlüssel und NULL-Werte in einer Schlüsselspalte ausgelöst. Dabei wird der Datensatz, der den Fehler verursacht hat, der Datenbank nicht hinzugefügt. Mithilfe von Eigenschaften können Sie die nächsten auszuführenden Schritte festlegen. Standardmäßig wird die Verarbeitung beendet. Manchmal ist es während der Cubeentwicklung jedoch erwünscht, dass die Verarbeitung bei Fehlern fortgesetzt wird, z. B. um das Cubeverhalten mit importierten und sogar unvollständigen Daten zu testen.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Ausführungsreihenfolge](#bkmk_exec)  
  
-   [Standardverhalten](#bkmk_default)  
  
-   [Fehlerkonfigurationseigenschaften](#bkmk_props)  
  
-   [Wo Fehlerkonfigurationseigenschaften festgelegt werden](#bkmk_tools)  
  
-   [Fehlende Schlüssel (KeyNotFound)](#bkmk_missing)  
  
-   [NULL-Fremdschlüssel in einer Faktentabelle (KeyNotFound)](#bkmk_nullfact)  
  
-   [NULL-Schlüssel in einer Dimension](#bkmk_nulldim)  
  
-   [Doppelte Schlüssel, die zu inkonsistenten Beziehungen führen (KeyDuplicate)](#bkmk_dupe)  
  
-   [Ändern der Fehlergrenze oder der Aktion, die bei Erreichen der Fehlergrenze ausgeführt wird](#bkmk_limit)  
  
-   [Festlegen des Fehlerprotokollpfads](#bkmk_log)  
  
-   [Nächster Schritt](#bkmk_next)  
  
##  <a name="bkmk_exec"></a> Ausführungsreihenfolge  
 Der Server führt für jeden Datensatz immer `NullProcessing`-Regeln vor `ErrorConfiguration`-Regeln aus. Dieses Verhalten sollte berücksichtigt werden, da Eigenschaften für das Verarbeiten von NULL-Werten, durch die NULL-Werte in Nullen (0) konvertiert werden, Fehler aufgrund doppelter Schlüssel verursachen können, wenn mindestens zwei Fehlerdatensätze in einer Schlüsselspalte den Wert 0 aufweisen.  
  
##  <a name="bkmk_default"></a> Standardverhalten  
 Standardmäßig wird die Verarbeitung beim ersten Fehler beendet, der eine Schlüsselspalte betrifft. Dieses Verhalten wird durch eine Fehlergrenze gesteuert, für die die Anzahl zulässiger Fehler auf 0 (null) festgelegt ist, sowie durch die Direktive Verarbeitung beenden, die den Server anweist, die Verarbeitung bei Erreichen der Fehlergrenze zu beenden.  
  
 Datensätze, die einen Fehler aufgrund von fehlenden, doppelten oder NULL-Werten auslösen, werden entweder in das unbekannte Element konvertiert oder verworfen. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht importiert.  
  
-   Aufgrund der `ConvertToUnknown`-Einstellung für `KeyErrorAction` erfolgt standardmäßig eine Konvertierung in das unbekannte Element. Datensätze, die dem unbekannten Element zugeordnet sind und auf ein potenzielles Problem hindeuten, werden in der Datenbank unter Quarantäne gestellt und können nach Abschluss der Verarbeitung untersucht werden.  
  
     Unbekannte Elemente werden aus abfragearbeitsauslastungen ausgeschlossen, aber in einigen Clientanwendungen sichtbar. wenn die `UnknownMember` nastaven NA hodnotu **Visible**.  
  
     Wenn Sie nachverfolgen möchten, wie viele NULL-Werte in das unbekannte Element konvertiert wurden, können Sie die `NullKeyConvertedToUnknown`-Eigenschaft so konfigurieren, dass diese Fehler im Protokoll oder im Verarbeitungsfenster gemeldet werden.  
  
-   Wenn Sie die `KeyErrorAction`-Eigenschaft manuell auf `DiscardRecord` festlegen, wird der Datensatz verworfen.  
  
 Mithilfe von Fehlerkonfigurationseigenschaften können Sie bestimmen, wie der Server bei Auftreten eines Fehlers reagiert. Sie können beispielsweise die Verarbeitung sofort beenden, die Verarbeitung fortsetzen und gleichzeitig die Protokollierung beenden oder sowohl die Verarbeitung als auch die Fehlerprotokollierung fortsetzen. Die Standardwerte variieren abhängig vom Schweregrad des Fehlers.  
  
 Mit dem Fehlerzähler wird die Anzahl der aufgetretenen Fehler verfolgt. Wenn Sie eine Obergrenze festlegen, ändert sich bei Erreichen des Grenzwerts die Reaktion des Servers. Standardmäßig wird die Verarbeitung vom Server beendet, sobald der Grenzwert erreicht wurde. Der Standardgrenzwert ist 0 und bewirkt, dass die Verarbeitung beim ersten aufgezeichneten Fehler beendet wird.  
  
 Schwerwiegende Fehler, wie ein fehlender Schlüssel oder NULL-Wert in einem Schlüsselfeld, sollten umgehend behandelt werden. Bei diesen Fehlern wird standardmäßig das Serververhalten `ReportAndContinue` angewendet, d. h., der Fehler wird vom Server abgefangen, zur Fehleranzahl hinzuaddiert und die Verarbeitung fortgesetzt (es sei denn, die Fehlergrenze ist 0 und die Verarbeitung wird sofort beendet).  
  
 Andere Fehler werden zwar generiert, aber nicht standardmäßig gezählt oder protokolliert (dies entspricht der `IgnoreError`-Einstellung), da der Fehler nicht unbedingt ein Datenintegritätsproblem darstellt.  
  
 Die Fehleranzahl wird durch Einstellungen für die Verarbeitung von NULL-Werten beeinflusst. Bei Dimensionsattributen bestimmen die Optionen für die Verarbeitung von NULL-Werten, wie der Server reagiert, wenn NULL-Werte gefunden werden. NULL-Werte in einer numerischen Spalte werden standardmäßig in Nullen (0) konvertiert, während NULL-Werte in einer Zeichenfolgenspalte als leere Zeichenfolgen verarbeitet werden. Sie können `NullProcessing`-Eigenschaften überschreiben, um NULL-Werte abzufangen, bevor sie zu einem `KeyNotFound`-Fehler oder `KeyDuplicate`-Fehler werden. Einzelheiten dazu finden Sie unter [NULL-Schlüssel in einer Dimension](#bkmk_nulldim) .  
  
 Fehler werden im Dialogfeld Verarbeiten protokolliert, aber nicht gespeichert. Sie können eine Protokolldatei für Schlüsselfehler benennen, um Fehler in einer Textdatei zu sammeln.  
  
##  <a name="bkmk_props"></a> Fehlerkonfigurationseigenschaften  
 Es gibt neun Fehlerkonfigurationseigenschaften. Mithilfe von fünf Eigenschaften wird bestimmt, wie der Server auf bestimmte Fehler reagiert. Die übrigen vier Eigenschaften beziehen sich auf Arbeitsauslastungen im Rahmen der Fehlerkonfiguration, also beispielsweise darauf, wie viele Fehler zulässig sind, welche Maßnahmen bei Erreichen des Grenzwerts getroffen werden und ob Fehler in einer Protokolldatei gesammelt werden.  
  
 **Reaktion des Servers auf bestimmte Fehler**  
  
|Eigenschaft|Standard|Andere Werte|  
|--------------|-------------|------------------|  
|`CalculationError`<br /><br /> Tritt auf, wenn die Fehlerkonfiguration initialisiert wird.|Bei `IgnoreError` wird der Fehler weder protokolliert noch gezählt. Die Verarbeitung wird fortgesetzt, solange die Fehleranzahl unter dem Grenzwert liegt.|Bei `ReportAndContinue` wird der Fehler protokolliert und gezählt.<br /><br /> Bei `ReportAndStop` wird der Fehler gemeldet, und die Verarbeitung wird unabhängig von der Fehlergrenze umgehend beendet.|  
|`KeyNotFound`<br /><br /> Tritt auf, wenn ein Fremdschlüssel in einer Faktentabelle keinen übereinstimmenden Primärschlüssel in einer verknüpften Dimensionstabelle aufweist (beispielsweise, wenn eine Faktentabelle für Umsatzwerte einen Datensatz mit einer Produkt-ID enthält, die in der Produktdimensionstabelle nicht vorhanden ist). Dieser Fehler kann bei der Verarbeitung von Partitionen oder von Schneeflockendimensionen auftreten.|Bei `ReportAndContinue` wird der Fehler protokolliert und gezählt.|Bei `ReportAndStop` wird der Fehler gemeldet, und die Verarbeitung wird unabhängig von der Fehlergrenze umgehend beendet.<br /><br /> Bei `IgnoreError` wird der Fehler weder protokolliert noch gezählt. Die Verarbeitung wird fortgesetzt, solange die Fehleranzahl unter dem Grenzwert liegt. Datensätze, durch die dieser Fehler ausgelöst wird, werden standardmäßig in das unbekannte Element konvertiert, Sie können die `KeyErrorAction`-Eigenschaft jedoch auch so ändern, dass die Datensätze stattdessen verworfen werden.|  
|`KeyDuplicate`<br /><br /> Tritt auf, wenn in einer Dimension doppelte Attributschlüssel gefunden werden. In den meisten Fällen sind doppelte Attributschlüssel zulässig. Durch diesen Fehler werden Sie jedoch auf die Duplikate hingewiesen, damit Sie den Dimensionsentwurf auf Fehler überprüfen können, die inkonsistente Beziehungen zwischen Attributen verursachen könnten.|Bei `IgnoreError` wird der Fehler weder protokolliert noch gezählt. Die Verarbeitung wird fortgesetzt, solange die Fehleranzahl unter dem Grenzwert liegt.|Bei `ReportAndContinue` wird der Fehler protokolliert und gezählt.<br /><br /> Bei `ReportAndStop` wird der Fehler gemeldet, und die Verarbeitung wird unabhängig von der Fehlergrenze umgehend beendet.|  
|`NullKeyNotAllowed`<br /><br /> Tritt auf, wenn `NullProcessing`  =  `Error` festgelegt ist, für ein Dimensionsattribut, oder wenn null-Werte enthalten sind, in einer attributschlüsselspalte, ein Element eindeutig identifiziert.|Bei `ReportAndContinue` wird der Fehler protokolliert und gezählt.|Bei `ReportAndStop` wird der Fehler gemeldet, und die Verarbeitung wird unabhängig von der Fehlergrenze umgehend beendet.<br /><br /> Bei `IgnoreError` wird der Fehler weder protokolliert noch gezählt. Die Verarbeitung wird fortgesetzt, solange die Fehleranzahl unter dem Grenzwert liegt. Datensätze, durch die dieser Fehler ausgelöst wird, werden standardmäßig in das unbekannte Element konvertiert, Sie können die `KeyErrorAction`-Eigenschaft jedoch auch so festlegen, dass die Datensätze stattdessen verworfen werden.|  
|`NullKeyConvertedToUnknown`<br /><br /> Tritt auf, wenn NULL-Werte nachfolgend in das unbekannte Element konvertiert werden. Festlegen von `NullProcessing`  =  `ConvertToUnknown` für eine Dimension Attribut dieser Fehler wird ausgelöst.|Bei `IgnoreError` wird der Fehler weder protokolliert noch gezählt. Die Verarbeitung wird fortgesetzt, solange die Fehleranzahl unter dem Grenzwert liegt.|Wenn dieser Fehler nur zu Informationszwecken gemeldet werden soll, behalten Sie den Standardwert bei. Andernfalls können Sie `ReportAndContinue` auswählen, damit der Fehler im Verarbeitungsfenster gemeldet und bei der Fehlerzählung berücksichtigt wird.<br /><br /> Bei `ReportAndStop` wird der Fehler gemeldet, und die Verarbeitung wird unabhängig von der Fehlergrenze umgehend beendet.|  
  
 **Allgemeine Eigenschaften**  
  
|**Eigenschaft**|**Werte**|  
|------------------|----------------|  
|`KeyErrorAction`|Dies ist die Aktion, die bei Auftreten eines `KeyNotFound`-Fehlers vom Server ausgeführt wird. Gültige Serverreaktionen auf diesen Fehler sind `ConvertToUnknown` oder `DiscardRecord`.|  
|`KeyErrorLogFile`|Dies ist ein benutzerdefinierter Dateiname, der über die Dateierweiterung .log verfügen und in einem Ordner gespeichert sein muss, für den das Dienstkonto Lese-/Schreibberechtigungen besitzt. Die Protokolldatei enthält nur Fehler, die während der Verarbeitung generiert wurden. Verwenden Sie Flight Recorder, wenn Sie ausführlichere Informationen benötigen.|  
|`KeyErrorLimit`|Dies ist die maximale Anzahl von Datenintegritätsfehlern, die der Server toleriert, bevor die Verarbeitung fehlschlägt. Der Wert -1 steht für eine unbegrenzte Anzahl. Der Standardwert ist 0 und bewirkt, dass die Verarbeitung nach Auftreten des ersten Fehlers beendet wird. Sie können ihn auch auf eine ganze Zahl festlegen.|  
|`KeyErrorLimitAction`|Dies ist die Aktion, die vom Server ausgeführt wird, nachdem die Obergrenze von Schlüsselfehlern erreicht wurde. Bei **Verarbeitung beenden**wird die Verarbeitung sofort beendet. Mit **Protokollierung beenden**wird der Verarbeitungsvorgang weiter ausgeführt; allerdings werden keine Fehler mehr gemeldet oder gezählt.|  
  
##  <a name="bkmk_tools"></a> Wo Fehlerkonfigurationseigenschaften festgelegt werden  
 Verwenden Sie die Eigenschaftenseiten in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , nachdem die Datenbank bereitgestellt wurde, oder im Modellprojekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Beide Tools enthalten dieselben Eigenschaften. Sie können Fehlerkonfigurationseigenschaften auch in der Datei msmdrsrv.ini festlegen, um Serverstandardeinstellungen für die Fehlerkonfiguration zu ändern, sowie im `Batch`-Befehl und im `Process`-Befehl, wenn die Verarbeitung skriptbasiert ausgeführt wird.  
  
 Sie können die Fehlerkonfiguration für jedes Objekt festlegen, das in einem eigenständigen Vorgang verarbeitet werden kann.  
  
#### <a name="sql-server-management-studio"></a>SQL Server Management Studio  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste für eines der folgenden Objekte auf **Eigenschaften** : Dimension, Cube oder Partition.  
  
2.  Klicken Sie in den Eigenschaften auf **Fehlerkonfiguration**.  
  
#### <a name="sql-server-data-tools"></a>SQL Server Data Tools  
  
1.  Doppelklicken Sie im Projektmappen-Explorer auf eine Dimension oder einen Cube. `ErrorConfiguration` wird in den Eigenschaften im unteren Bereich angezeigt.  
  
2.  Sie können auch nur eine einzelne Dimension, mit der rechten Maustaste der Dimensions im Projektmappen-Explorer, wählen Sie `Process`, und wählen Sie dann **Einstellungen ändern** im Dialogfeld Dimension aufbereiten. Optionen für die Fehlerkonfiguration werden auf der Registerkarte Dimensionsschlüsselfehler angezeigt.  
  
##  <a name="bkmk_missing"></a> Fehlende Schlüssel (KeyNotFound)  
 Datensätze mit einem fehlenden Schlüsselwert können der Datenbank auch dann nicht hinzugefügt werden, wenn Fehler ignoriert werden oder eine unbegrenzte Fehleranzahl festgelegt wurde.  
  
 Der Server generiert den `KeyNotFound`-Fehler während der Partitionsverarbeitung, wenn eine Tabelle in einem Faktendatensatz einen Fremdschlüsselwert enthält, der Fremdschlüssel aber keinen entsprechenden Datensatz in einer verknüpften Dimensionstabelle aufweist. Dieser Fehler tritt auch bei der Verarbeitung von verknüpften oder Schneeflocken-Dimensionstabellen auf, wenn von einem Datensatz in einer Dimension ein Fremdschlüssel angegeben wird, der in der verknüpften Dimension nicht vorhanden ist.  
  
 Wenn ein `KeyNotFound`-Fehler auftritt, wird der problematische Datensatz dem unbekannten Element zugeordnet. Dieses Verhalten wird gesteuert, durch die **Schlüsselaktion**, legen Sie auf `ConvertToUnknown`, sodass Sie zur weiteren Untersuchung die zugeordneten Datensätze anzeigen können.  
  
##  <a name="bkmk_nullfact"></a> NULL-Fremdschlüssel in einer Faktentabelle (KeyNotFound)  
 Ein NULL-Wert in einer Fremdschlüsselspalte einer Faktentabelle wird standardmäßig in 0 konvertiert. In der Annahme, dass 0 kein gültiger Fremdschlüsselwert ist, wird der `KeyNotFound`-Fehler protokolliert und auf die Fehlergrenze, die standardmäßig 0 ist, angerechnet.  
  
 Damit die Verarbeitung fortgesetzt werden kann, können Sie den NULL-Wert behandeln, bevor er konvertiert und auf Fehler überprüft wird. Legen Sie zu diesem Zweck `NullProcessing` zu `Error`.  
  
#### <a name="set-nullprocessing-property-on-a-measure"></a>Festlegen der NullProcessing-Eigenschaft für ein Measure  
  
1.  Doppelklicken Sie im Projektmappen-Explorer von SQL Server Data Tools auf den Cube, um ihn im Cube-Designer zu öffnen.  
  
2.  Klicken Sie im Bereich „Measures“ mit der rechten Maustaste auf ein Measure, und wählen Sie **Eigenschaften**aus.  
  
3.  Erweitern Sie in den Eigenschaften, **Quelle** anzeigen `NullProcessing` Eigenschaft. Die Eigenschaft ist standardmäßig auf **Automatic** festgelegt. Bei OLAP-Elementen bewirkt diese Einstellung, dass NULL-Werte für Felder mit numerischen Daten in Nullen (0) konvertiert werden.  
  
4.  Ändern Sie den Wert auf `Error` , schließen Sie alle Datensätze mit einem null-Wert, der Konvertierung von Null-in numerische Werte (null) zu unterbinden. Diese Änderung können Fehler aufgrund doppelter Schlüssel mit mehreren Datensätzen in der Schlüsselspalte den Wert 0 zu vermeiden, und vermeiden Sie auch `KeyNotFound` Fehler, wenn ein NULL-Fremdschlüssel keinen Primärschlüssel entspricht einer verknüpften Dimensionstabelle aufweist.  
  
##  <a name="bkmk_nulldim"></a> NULL-Schlüssel in einer Dimension  
 Um die Verarbeitung fortzusetzen, wenn in Fremdschlüsseln in einer Schneeflockendimension NULL-Werte gefunden werden, behandeln Sie zunächst die NULL-Werte, indem Sie für die `NullProcessing` des Dimensionsattributs `KeyColumn` festlegen. Dadurch wird der Datensatz verworfen oder konvertiert, bevor der `KeyNotFound`-Fehler auftreten kann.  
  
 NULL-Werte können für das Dimensionsattribut auf zwei Weisen behandelt werden:  
  
-   Legen Sie `NullProcessing` = `UnknownMember` auf Datensätze mit null-Werten dem unbekannten Element zuzuordnen. Dadurch wird der `NullKeyConvertedToUnknown`-Fehler erzeugt, der standardmäßig ignoriert wird.  
  
-   Legen Sie `NullProcessing` = `Error` um Datensätze mit null-Werten auszuschließen. Dadurch wird der `NullKeyNotAllowed`-Fehler erzeugt, der protokolliert und auf den Grenzwert für Schlüsselfehler angerechnet wird. Sie können die fehlerkonfigurationseigenschaft für festlegen **Null-Schlüssel nicht zulässig** zu `IgnoreError` , damit die Verarbeitung, um den Vorgang fortzusetzen.  
  
 NULL-Werte können für Nichtschlüsselfelder insofern problematisch sein, als MDX-Abfragen unterschiedliche Werte zurückgeben können. Das ist abhängig davon, ob NULL als 0 oder leerer Wert interpretiert wird. Aus diesem Grund bietet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Optionen für die Verarbeitung von NULL-Werten, mit denen Sie das gewünschte Konvertierungsverhalten vordefinieren können. Einzelheiten dazu finden Sie unter [Definieren von unbekannten Elementen und Eigenschaften für das Verarbeiten von NULL-Werten](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md) -Befehl und im <xref:Microsoft.AnalysisServices.NullProcessing> .  
  
#### <a name="set-nullprocessing-property-on-a-dimension-attribute"></a>Festlegen der NullProcessing-Eigenschaft für ein Dimensionsattribut  
  
1.  Doppelklicken Sie im Projektmappen-Explorer von SQL Server Data Tools auf die Dimension, um sie im Dimensions-Designer zu öffnen.  
  
2.  Klicken Sie im Bereich „Attribute“ mit der rechten Maustaste auf ein Attribut, und wählen Sie **Eigenschaften**aus.  
  
3.  Erweitern Sie in den Eigenschaften, **KeyColumns** anzeigen `NullProcessing` Eigenschaft. Die Eigenschaft ist standardmäßig auf **Automatic** festgelegt, wodurch NULL-Werte für Felder mit numerischen Daten in Nullen (0) konvertiert werden. Ändern Sie den Wert entweder `Error` oder `UnknownMember`.  
  
     Diese Änderung entfernt die zugrunde liegenden Bedingungen zum Auslösen `KeyNotFound` von entweder verworfen oder konvertiert des Datensatzes aus, bevor er auf Fehler überprüft wird.  
  
     Abhängig von der Fehlerkonfiguration kann eine dieser Aktionen zu einem Fehler führen, der gemeldet und gezählt wird. Sie müssen möglicherweise zusätzliche Eigenschaften, z. B. Einstellung anpassen `KeyNotFound` zu `ReportAndContinue` oder `KeyErrorLimit` auf einen Wert ungleich NULL, um damit die Verarbeitung fortgesetzt, wenn diese Fehler gemeldet und gezählt werden.  
  
##  <a name="bkmk_dupe"></a> Doppelte Schlüssel, die zu inkonsistenten Beziehungen führen (KeyDuplicate)  
 Standardmäßig führt ein doppelter Schlüssel nicht dazu, dass die Verarbeitung beendet wird; allerdings wird der Fehler ignoriert und der doppelte Datensatz aus der Datenbank ausgeschlossen.  
  
 Um dieses Verhalten zu ändern, legen Sie `KeyDuplicate` auf `ReportAndContinue` oder auf `ReportAndStop` fest, damit der Fehler gemeldet wird. Anschließend können Sie den Fehler untersuchen, um mögliche Fehler im Dimensionsentwurf zu ermitteln.  
  
##  <a name="bkmk_limit"></a> Ändern der Fehlergrenze oder der Aktion, die bei Erreichen der Fehlergrenze ausgeführt wird  
 Sie können die Fehlergrenze heraufsetzen, damit während der Verarbeitung mehr Fehler toleriert werden. Es gibt keine allgemeinen Vorgaben zum Erhöhen der Fehlergrenze, da sich der geeignete Wert nach dem jeweiligen Szenario richtet. Fehlergrenzen werden als `KeyErrorLimit` in `ErrorConfiguration` Eigenschaften in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], oder als **Anzahl von Fehlern** in der Registerkarte Fehlerkonfiguration für Eigenschaften von Dimensionen, Cubes oder Measuregruppen gruppiert [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Sie können festlegen, dass die Verarbeitung oder Protokollierung bei Erreichen der Fehlergrenze beendet wird. Gehen wir z. B. davon aus, dass bei einer Fehlergrenze von 100 die Aktion `StopLogging` ausgeführt wird. Bei Fehler Nummer 101 wird die Verarbeitung fortgesetzt, während Fehler jedoch nicht mehr protokolliert oder gezählt werden. Fehler Grenzwert angegeben sind als `KeyErrorLimitAction` in `ErrorConfiguration` Eigenschaften in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], oder als **Aktion bei Fehler** in der Registerkarte Fehlerkonfiguration für Eigenschaften von Dimensionen, Cubes oder Measuregruppen gruppiert [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
##  <a name="bkmk_log"></a> Festlegen des Fehlerprotokollpfads  
 Sie können eine Datei angeben, in der schlüsselspezifische Fehlermeldungen gespeichert werden, die während der Verarbeitung gemeldet werden. Fehler werden während der interaktiven Verarbeitung standardmäßig im Verarbeitungsfenster angezeigt und verworfen, wenn Sie das Fenster oder die Sitzung schließen. Das Protokoll enthält nur Fehlerinformationen zu Schlüsseln, die sich direkt auf die Fehler beziehen, die in den Verarbeitungsdialogfeldern angezeigt werden.  
  
 Fehler werden in einer Textdatei mit der Dateierweiterung .log protokolliert. Die Datei ist leer, bis Fehler auftreten. Standardmäßig wird eine Datei im Ordner DATA erstellt. Sie können einen anderen Ordner angeben, solange das Analysis Services-Dienstkonto eine Schreibberechtigung für diesen Speicherort besitzt.  
  
##  <a name="bkmk_next"></a> Nächster Schritt  
 Entscheiden Sie, ob Fehler zu einer Beendigung der Verarbeitung führen oder ignoriert werden. Beachten Sie, dass nur der Fehler ignoriert wird. Der Datensatz, der den Fehler verursacht hat, wird nicht ignoriert und entweder verworfen oder in ein unbekanntes Element konvertiert. Datensätze, die gegen die Regeln der Datenintegrität verstoßen, werden der Datenbank niemals hinzugefügt. Die Verarbeitung wird standardmäßig beim ersten Fehler beendet. Sie können diese Einstellung jedoch ändern, indem Sie die Fehlergrenze heraufsetzen. Bei der Cubeentwicklung kann es von Nutzen sein, die Regeln für die Fehlerkonfiguration zu lockern und die Verarbeitung fortzusetzen, um Testdaten zu sammeln.  
  
 Entscheiden Sie, ob das Standardverhalten für die Verarbeitung von NULL-Werten geändert werden soll. NULL-Werte in einer Zeichenfolgenspalte werden standardmäßig als leere Werte verarbeitet, während NULL-Werte in einer numerischen Spalte als Nullen (0) verarbeitet werden. Anweisungen dazu, wie Sie die Verarbeitung von NULL-Werten für ein Attribut festlegen, finden Sie unter [Definieren von unbekannten Elementen und Eigenschaften für das Verarbeiten von NULL-Werten](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md) .  
  
## <a name="see-also"></a>Siehe auch  
 [Protokolleigenschaften](../server-properties/log-properties.md)   
 [Definieren von unbekannten Elementen und Eigenschaften für das Verarbeiten von NULL-Werten](../lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
  
  
