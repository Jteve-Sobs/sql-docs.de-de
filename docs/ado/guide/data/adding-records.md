---
title: Hinzufügen von Datensätzen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 87d8358344d75cd6995d43d081abbec7aeaabe1c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701061"
---
# <a name="adding-records-to-a-recordset"></a>Hinzufügen von Datensätzen zu einem Recordset
Verwenden der **AddNew** Methode zum Erstellen und initialisieren einen neuen Datensatz in einer vorhandenen **Recordset**. Können Sie die **unterstützt** -Methode mit einer **CursorOptionEnum** Wert **AdAddNew** zu überprüfen, ob Sie Datensätze, mit dem aktuellen hinzufügen können **Recordset** Objekt.

 Nach dem Aufrufen der **AddNew** Methode, der neue Datensatz wird zum aktuellen Datensatz und bleibt der aktuelle aufzurufen, nachdem Sie die **Update** Methode. Wenn die **Recordset** Objekt unterstützt keine Lesezeichen. Sie können nicht auf den neuen Datensatz zugreifen, nachdem Sie zu einem anderen Datensatz wechseln. Daher abhängig vom Cursortyp, möglicherweise müssen Sie zum Aufrufen der **Requery** Methode, um den neuen Datensatz zugänglich zu machen.

 Aufrufen **AddNew** beim Bearbeiten des aktuellen Datensatzes oder beim Hinzufügen eines neuen Datensatzes, ADO Ruft die **Update** Methode, um alle speichern Änderungen und erstellt dann den neuen Datensatz.

 Dieser Abschnitt enthält die folgenden Themen.

-   [Hinzufügen von Datensätzen mit der AddNew-Methode](../../../ado/guide/data/adding-records-using-addnew.md)

-   [Hinzufügen von mehreren Feldern](../../../ado/guide/data/adding-multiple-fields.md)

-   [Bestimmen des Bearbeitungsmodus](../../../ado/guide/data/determining-edit-mode.md)

-   [Using AddNew in Immediate and Batch Modes (Verwenden von AddNew in Immediate- und Batch-Modi)](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
