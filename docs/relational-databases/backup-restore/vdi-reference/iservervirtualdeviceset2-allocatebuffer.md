---
title: IServerVirtualDeviceSet2::AllocateBuffer
titlesuffix: SQL Server VDI reference
description: In diesem Artikel erhalten Sie Referenzinformationen zum Befehl „IServerVirtualDeviceSet2::AllocateBuffer“.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7cf7461df60309f73158447d65fc63c50fc01b42
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892231"
---
# <a name="iservervirtualdeviceset2allocatebuffer-vdi"></a>IServerVirtualDeviceSet2::AllocateBuffer (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

Mit der Funktion **AllocateBuffer** wird ein freigegebener Speicherpuffer aus der Gruppe virtueller Geräte abgerufen.

## <a name="syntax"></a>Syntax

```c
HRESULT IServerVirtualDeviceSet2::AllocateBuffer (
   LPVOID*      ppBuffer,
   UINT32      dwSize,
   UINT32      dwAlignment
);
```

## <a name="parameters"></a>Parameter

*ppBuffer*: Gibt einen Zeiger auf den Anfang des Puffers zurück.

*dwSize*: Größe des Puffers in Bytes. Dies gilt nicht für Präfixzonen, die vom Client angefordert werden. Diese werden auf dem Server ausgeblendet, und vor dem Zurückgeben der Adresse des Puffers steht Speicherplatz zur Verfügung.

*dwAlignment*: Gibt die Ausrichtungsgrenze für den Puffer an. Der Wert 4096 würde z. B. sicherstellen, dass der Puffer an einer 4096-Byte-Grenze ausgerichtet wird. Dies bedeutet, dass für die zurückgegebene Adresse die niederwertigen 12 Bits auf NULL festgelegt sind. Dieser Parameter muss eine Potenz von 2 sein.

## <a name="return-value"></a>Rückgabewert

|Rückgabewert | Erklärung |
|---|---|
| NOERROR | Der Puffer wird zurückgegeben. |
| VD_E_MEMORY | Es ist nicht genügend Arbeitsspeicher verfügbar. |
| VD_E_INVALID | Ein Parameter war ungültig. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in der [Referenz zur Schnittstelle für virtuelle Geräte in SQL Server](reference-virtual-device-interface.md).