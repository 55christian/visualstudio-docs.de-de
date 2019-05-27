---
title: IDebugFunctionObject::CreateArrayObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f35c63310abe227dd50428d34122787ed0fb292
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212611"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Erstellt ein Arrayobjekt. Dieses Array kann entweder Primitive oder ein Objekt enthalten Werte von Gruppeninstanzen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`ot`\
[in] Gibt einen Wert aus der [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Enumeration, der angibt, des Typs, der das neue Arrayobjekt.

`pClassField`\
[in] Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, das die Klasse des Objekts, wenn ein Array von Objekt Werte von Gruppeninstanzen erstellen darstellt. Wenn ein Array primitiver Objekte erstellen, ist dieser Parameter ein null-Wert.

`dwRank`\
[in] Der Rang oder die Anzahl der Dimensionen des Arrays.

`dwDims`\
[in] Die Größen der einzelnen Dimensionen des Arrays.

`dwLowBounds`\
[in] Der Ursprung der einzelnen Dimensionen (in der Regel 0 oder 1).

`ppObject`\
[out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das das neu erstellte Array darstellt. Dies ist ein [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) Objekt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Rufen Sie diese Methode, um ein Objekt, das einen Arrayparameter an die Funktion darstellt, der durch dargestellt wird, erstellen die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)