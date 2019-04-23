---
title: Berichte mit Durchklicken (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- clickthrough reports
- customizing clickthrough reports
- clickthrough reports, customizing
ms.assetid: cf2c396e-b0c6-41f9-8c45-ddc8406f7e85
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6b86bcb059d2186254a001f59f074a40eef659fd
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59934506"
---
# <a name="clickthrough-reports-ssrs"></a>Berichte mit Durchklicken (SSRS)
  Ein Bericht, der detaillierte Informationen zu den im Hauptbericht enthaltenen Daten bereitstellt, wird als Bericht mit Durchklicken bezeichnet. Ein Bericht mit Durchklicken wird angezeigt, wenn der Benutzer auf die im Hauptbericht angezeigten interaktiven Daten klickt. Diese Berichte werden vom Berichtsserver automatisch generiert. Beim Erstellen eines Modells bestimmen Sie durch Festlegen der Eigenschaften `DefaultDetailAttribute` und `DefaultAggregateAttribute`, die Sie einer Entität im Berichtsmodell zuweisen, was in Berichten mit Durchklicken angezeigt wird.  
  
> [!NOTE]
>  Durchklickberichte sind nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Wenn Sie nicht genau wissen, welche Edition von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in Ihrer Organisation verwendet wird, sollten Sie sich mit dem Datenbankadministrator in Verbindung setzen.  
  
## <a name="using-default-templates"></a>Verwenden von Standardvorlagen  
 Der Berichtsserver generiert standardmäßig für jede Entität zwei Vorlagentypen für Berichte mit Durchklicken: eine Einzelinstanzvorlage sowie eine Multiinstanzvorlage. Das Element, auf das geklickt wird, bestimmt, welche Vorlage verwendet wird. Wenn der Leser des Berichts auf ein skalares Attribut klickt, wird die Einzelinstanzvorlage verwendet. Wenn der Leser des Berichts auf ein Aggregatattribut klickt, wird die Multiinstanzvorlage verwendet.  
  
#### <a name="single-instance-templates"></a>Einzelinstanzvorlagen  
 Eine Einzelinstanzvorlage zeigt alle Attribute der Zielentität sowie alle Standardaggregatattribute an, die für die verbundenen Entitäten angegeben sind, die zu der Zielentität in einer 1:n-Beziehung stehen. Eine Einzelinstanzvorlage könnte wie in der folgenden Abbildung aussehen.  
  
 ![Ein n:1-Bericht mit Durchklicken.](../media/manytooneclickthrough.gif "A many to 1 clickthrough report.")  
  
#### <a name="multiple-instance-templates"></a>Multiinstanzvorlagen  
 Eine Multiinstanzvorlage zeigt nur die Standarddetailattribute der Zielentität sowie alle Standardaggregatattribute an, die für die verbundenen Entitäten angegeben sind, die zu der Zielentität in einer 1:n-Beziehung stehen. Eine Multiinstanzvorlage könnte wie in der folgenden Abbildung aussehen.  
  
 ![Ein n:1-Bericht mit Durchklicken.](../media/onetomanyclickthrough.gif "A many to 1 clickthrough report.")  
  
## <a name="customizing-clickthrough-reports"></a>Anpassen von Berichten mit Durchklicken  
 Anstatt die vom Berichtsserver generierten Standardvorlagen zu verwenden, können Sie im Berichts-Generator einen Bericht erstellen und ihn als angepassten Bericht mit Durchklicken verwenden. Anschließend können Sie den Bericht mit dem Modell als Drillthroughbericht im Berichts-Manager verknüpfen.  
  
 Um einen im Berichts-Generator erstellten Bericht in einen Bericht mit Durchklicken umzuwandeln, müssen Sie im Dialogfeld **Eigenschaften** des Berichts-Generators die Option **Benutzern einen Drillthrough von anderen Berichten zu diesem Bericht ermöglichen** auswählen. Wenn diese Option ausgewählt ist, wird dem Bericht ein Drillthroughparameter hinzugefügt, und der Bericht kann nicht mehr direkt im Berichts-Generator ausgeführt werden. Der Drillthroughparameter wird automatisch vom Berichtsserver berechnet, wenn der Leser des Berichts in einem Berichts-Generator-Bericht auf ein Element klickt.  
  
> [!IMPORTANT]  
>  Bei der im Bericht verwendeten primären Entität bzw. Basisentität muss es sich um dieselbe Entität handeln, mit der Sie den Bericht verknüpfen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verknüpfen eines Berichts mit einem Modell als Bericht mit Durchklicken](../link-a-report-to-a-model-as-a-clickthrough-report.md)  
  
  
