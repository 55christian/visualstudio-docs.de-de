---
title: IDebugMemoryBytes2::GetSize | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbed7e4421b01e1a779c5c976001a5dd5b4ba2d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918887"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Ruft die Größe in Bytes, des Arbeitsspeichers dargestellt durch diese [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) Objekt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSize( 
   UINT64* pqwSize
);
```

```csharp
int GetSize(
   out ulong pqwSize
);
```

#### <a name="parameters"></a>Parameter
 `pqwSize`

 [out] Gibt die Größe, der den Speicherplatz in Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)