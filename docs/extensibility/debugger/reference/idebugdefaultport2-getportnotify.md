---
title: IDebugDefaultPort2::GetPortNotify | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9c59687e86d236bc22d563c94e2caaedae5decf
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205131"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Diese Methode ruft eine [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) Schnittstelle für diesen Port.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parameter
`ppPortNotify`\
[out] Ein [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 In der Regel die `QueryInterface` Methode wird aufgerufen, die Objekt-Implementierung der [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle zum Abrufen einer [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) Schnittstelle. Es gibt jedoch Situationen, in denen die gewünschte Schnittstelle auf einem anderen Objekt implementiert wird. Diese Methode blendet diese Umstände und gibt die `IDebugPortNotify2` Schnittstelle aus dem am besten geeigneten-Objekt.

## <a name="see-also"></a>Siehe auch
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)