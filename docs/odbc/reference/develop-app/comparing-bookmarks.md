---
title: Vergleich von Lesezeichen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c28392c0d48984b4aaf8a8df442b6a4054a7eced
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307475"
---
# <a name="comparing-bookmarks"></a>Vergleichen von Textmarken
Da Lesezeichen bytevergleichbar sind, können sie auf Gleichheit oder Ungleichheit verglichen werden. Zu diesem Tun behandelt eine Anwendung jede Textmarke als Array von Bytes und vergleicht zwei Lesezeichen byte-byte. Da Lesezeichen garantiert nur innerhalb eines Resultsets unterschieden werden, macht es keinen Sinn, Lesezeichen zu vergleichen, die aus verschiedenen Resultsets erhalten wurden.
