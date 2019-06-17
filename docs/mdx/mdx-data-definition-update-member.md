---
title: UPDATE MEMBER-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 829aabfa7028814e20bcecd47a53495f6dc6bc6a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62694820"
---
# <a name="mdx-data-definition---update-member"></a>MDX-Datendefinition – UPDATE MEMBER


  Aktualisiert ein vorhandenes berechnetes Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
UPDATE MEMBER Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Eine gültige Zeichenfolge, die den Namen des Cubes bereitstellt, in dem das Element enthalten ist.  
  
 *Member_Name*  
 Eine gültige Zeichenfolge, die den Namen eines vorhandenen Elements bereitstellt.  
  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), auf den das Element aktualisiert wird.  
  
 *Property_name*  
 Eine gültige Zeichenfolge, die den Namen einer Eigenschaft eines berechneten Elements bereitstellt.  
  
 *Property_Value*  
 Ein gültiger Skalarausdruck, der den Eigenschaftswert des berechneten Elements bereitstellt.  
  
## <a name="remarks"></a>Hinweise  
 Mit der UPDATE MEMBER-Anweisung wird ein vorhandenes berechnetes Element aktualisiert und gleichzeitig die relative Rangfolge des Elements in Bezug auf andere Berechnungen beibehalten. Deshalb können Sie die Lösungsreihenfolge (SOLVEORDER) mithilfe der UPDATE MEMBER-Anweisung nicht ändern.  
  
 Eine UPDATE MEMBER-Anweisung kann nicht im MDX-Skript für einen Cube angegeben werden.  
  
 Die Angabe eines anderen als des aktuell verbundenen Cubes verursacht einen Fehler. Daher sollten Sie den aktuellen Cube mithilfe von CURRENTCUBE statt mit dem Cubenamen angeben.  
  
 Weitere Informationen zu Elementeigenschaften, die durch OLE DB definiert sind, finden Sie in der OLE DB-Dokumentation.  
  
## <a name="standard-properties"></a>Standardeigenschaften  
 Jedes Element verfügt über Standardeigenschaften. In der folgenden Tabelle werden diese Standardeigenschaften aufgeführt.  
  
|Eigenschaftsbezeichner|Bedeutung|  
|-------------------------|-------------|  
|FORMAT_STRING|Ein Office Style-Formatzeichenfolge, die der Clientanwendung zum Anzeigen von Zellwerten verwenden kann.|  
|VISIBLE|Ein Wert, der bestimmt, ob das berechnete Element in einem Schemarowset sichtbar ist. Sichtbare berechnete Elemente hinzugefügt werden können, um eine Gruppe, die [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) Funktion. Ein Wert ungleich 0 zeigt an, dass das berechnete Element sichtbar ist. Der Standardwert für diese Eigenschaft ist *Visible*.<br /><br /> Berechnete Elemente, die nicht sichtbar sind, werden üblicherweise als Zwischenschritte in komplexeren berechneten Elementen verwendet. Auf diese berechneten Elemente können auch andere Arten von Elementen (z. B. Measures) verweisen.|  
|NON_EMPTY_BEHAVIOR|Das Measure oder die Menge, mit dem oder der MDX beim Auflösen leerer Zellen das Verhalten berechneter Elemente bestimmt.|  
|CAPTION|Ein Zeichenfolgenwert, der die Beschriftung angibt, die von der Clientanwendung zum Anzeigen des Elements verwendet wird.|  
|DISPLAY_FOLDER|Ein Zeichenfolgenwert, der den Pfad des Anzeigeordners angibt, in dem das Element von der Clientanwendung angezeigt wird. Das Trennzeichen für Ordnerebenen wird von der Clientanwendung definiert. Für Tools und Clients, die vom [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], den umgekehrten Schrägstrich (\\) als ebenentrennzeichen. Um mehrere Anzeigeordner für ein definiertes Element bereitzustellen, verwenden Sie ein Semikolon (;) als Trennzeichen für die Ordner.|  
|ASSOCIATED_MEASURE_GROUP|Der Name der Measuregruppe, der dieses Element zugeordnet wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [DROP MEMBER-Anweisung &#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [CREATE MEMBER-Anweisung &#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)   
 [MDX-Datendefinitionsanweisungen &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
