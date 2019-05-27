---
title: IDebugClassField::EnumNestedEnums | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01465a0b921d61a07c4d31c8d4d4ba4b70e5bafd
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206860"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Erstellt einen Enumerator für die geschachtelte Enumeratoren dieser Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumNestedEnums(
    IEnumDebugFields** ppEnum
);
```

```csharp
int EnumNestedEnums(
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Objekt, das die Liste der geschachtelte Enumerationen darstellt. Gibt einen null-Wert zurück, wenn keine geschachtelten Enumerationen vorhanden sind.

## <a name="return-value"></a>Rückgabewert
Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn keine geschachtelten Enumeratoren vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
Jedes Element der Enumeration ist ein [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) Objekt, das eine geschachtelten Enumeration beschreibt.

Eine Enumeration, die innerhalb einer Klasse deklariert wird mit eine geschachtelten Enumeration betrachtet. Angenommen, dies liegt vor:

```
class RootClass {
    enum NestedEnum { EnumValue = 0 }
};
```

Die `EnumNestedEnums` Methode zurückgeben würde eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) -Objekt, das eine enthält [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) Objekt, das darstellt der `NestedEnum` Enumeration.

## <a name="see-also"></a>Siehe auch
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
