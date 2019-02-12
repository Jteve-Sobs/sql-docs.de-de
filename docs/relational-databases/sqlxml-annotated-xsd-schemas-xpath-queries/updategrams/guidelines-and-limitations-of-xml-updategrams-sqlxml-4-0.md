---
title: Richtlinien und Einschränkungen von XML-Updategrams (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ce4187ca3dfa49d98e70396cdaee5aa7f9439d72
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56033901"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Richtlinien und Einschränkungen von XML-Updategrams (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn Sie XML-Updategrams verwenden, sind folgende Überlegungen zu berücksichtigen:  
  
-   Bei Verwendung ein Updategrams für einen Einfügevorgang mit nur ein einzelnes Paar von  **\<vor >** und  **\<nach >** Blöcke, die  **\<vor >** Block kann ausgelassen werden. Im Gegensatz dazu bei einem Löschvorgang der  **\<nach >** Block kann ausgelassen werden.  
  
-   Bei Verwendung ein Updategrams mit mehreren  **\<vor >** und  **\<nach >** , freigegebene Blöcke in der  **\<Sync >** zu markieren, beide  **\<vor >** Blöcke und  **\<nach >** Blöcke müssen angegeben werden, um Formular  **\<vor >** und  **\<nach >** Paare.  
  
-   Die Updates in einem Updategram werden auf die XML-Sicht angewendet, die vom XML-Schema bereitgestellt wird. Daher müssen Sie für eine erfolgreiche Standardzuordnung den Schemadateinamen im Updategram angeben. Falls der Dateiname nicht bereitgestellt wird, müssen die Element- und Attributnamen mit den Tabellen- und Spaltennamen in der Datenbank übereinstimmen.  
  
-   SQLXML 4.0 setzt voraus, dass alle Spaltenwerte in einem Updategram ausdrücklich im bereitgestellten Schema (XDR oder XSD) zugeordnet werden, um die XML-Sicht für die untergeordneten Elemente zu erstellen. Dieses Verhalten unterscheidet sich von früheren Versionen von SQLXML, die zulässige Wert für eine Spalte, die nicht im Schema zugeordnet, wenn es als Teil des Fremdschlüssels in impliziert wurde eine **SQL: Relationship** Anmerkung. (Beachten Sie, dass sich diese Änderung nicht auf die Propagierung von Primärschlüsselwerten an untergeordnete Elemente auswirkt, was immer noch für SQLXML 4.0 gilt, wenn für das untergeordnete Element kein Wert ausdrücklich angegeben wird.)  
  
-   Wenn Sie ein Updategram verwenden, um Daten in einer binären Spalte zu ändern (z. B. die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Image** -Datentyp), müssen Sie ein Zuordnungsschema, in dem Angeben der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp (z. B. **SQL: datatype = "image"** ) und den XML-Datentyp (z. B. **dt: Type = "Binhex"** oder **dt: Type = "binbase64**) muss angegeben werden. Die Daten für die binäre Spalte müssen im Updategram angegeben werden; die **SQL: URL-codieren** Anmerkung, die im Zuordnungsschema angegeben ist, wird vom Updategram ignoriert.  
  
-   Wenn Sie schreiben ein XSD-Schema, bei dem Wert für die Angabe der **SQL: Relation** oder **SQL: field** Anmerkung enthält ein Sonderzeichen, wie z. B. ein Leerzeichen (z. B. in "Order Details" Table-Name), dieser Wert muss in eckige Klammern (z. B. "[Details Bestellung]") eingeschlossen werden.  
  
-   Wenn sie Updategrams verwenden, werden Kettenbeziehungen nicht unterstützt. Wenn beispielsweise die Tabellen A und C über eine Kettenbeziehung miteinander verknüpft sind, die Tabelle B verwendet, tritt der folgende Fehler auf, wenn Sie versuchen, das Updategram auszuführen:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Auch wenn Schema und Updategram ansonsten korrekt und gültig sind, tritt dieser Fehler auf, wenn eine Kettenbeziehung vorhanden ist.  
  
-   Updategrams erlauben nicht das Übergeben von **Image** Datentyp als Parameter während eines Updates.  
  
-   Binary large Object (BLOB) Typen wie zum Beispiel **Text/Ntext** und Images sollten nicht verwendet werden, der  **\<vor >** -block in bei der Verwendung von Updategrams verwendet wird, da auf diese Weise für die Verwendung in eingeschlossen werden Steuerung der Parallelität. Dies kann wegen der Einschränkungen auf Vergleich für BLOB-Typen Probleme mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verursachen. Z. B. das LIKE-Schlüsselwort werden in der WHERE-Klausel für den Vergleich zwischen den Spalten von der **Text** -Datentyps; Vergleiche schlägt jedoch fehl, im Fall von BLOB-Typen, in denen die Größe der Daten größer als 8 KB ist.  
  
-   Sonderzeichen in **Ntext** Daten können Probleme mit SQLXML 4.0 verursachen, aufgrund der Einschränkungen auf Vergleich für BLOB-Typen. Z. B. die Verwendung von "[Serializable]" in der  **\<vor >** -Block eines Updategrams, die bei der Verwendung in der parallelitätsprüfung einer Spalte vom **Ntext** Typ mit der folgenden SQLOLEDB fehl fehlerbeschreibung:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberlegungen zu Updategramms &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
