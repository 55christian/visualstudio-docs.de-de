---
title: IDebugProcess3::GetDebugReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetDebugReason
helpviewer_keywords:
- IDebugProcess3::GetDebugReason
ms.assetid: f23fbabc-8b18-4278-bebf-4cdc7091513c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55f49d94ec95af8c7c74205335fe69b1ec3ecd41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917688"
---
# <a name="idebugprocess3getdebugreason"></a>IDebugProcess3::GetDebugReason
Diese Methode gibt den Grund, dass der Prozess zum Debuggen gestartet wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDebugReason(
   DEBUG_REASON* pReason
);
```

```csharp
int GetDebugReason(
   out enum_DEBUG_REASON pReason
);
```

#### <a name="parameters"></a>Parameter
 `pReason`

 [out] Gibt einen Wert aus der [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) Enumeration.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)