---
title: IDebugBinder::Bind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00d7e63b8a521ee25d2c7d378aeb82d064358ec9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344495"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Diese Methode ruft den Arbeitsspeicher-Kontext oder das Objekt, das das Symbol für den aktuellen Wert enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`pContainer`\
[in] Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , enthält das untergeordnete Element verweist `pField`.

`pField`\
[in] Die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , das das Symbol darstellt.

`ppObject`\
[out] Gibt die `IDebugObject` , die die Instanz des Symbols darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)