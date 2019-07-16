---
title: CODE_PATH | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 516122ee8aaaa0ed18537369eeeffb05be3ebf1c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327223"
---
# <a name="codepath"></a>CODE_PATH
Beschreibt eine Methode oder einen Funktionsaufruf an.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagCODE_PATH { 
    BSTR                bstrName;
    IDebugCodeContext2* pCode;
} CODE_PATH;
```

```csharp
public struct CODE_PATH {
    public string            bstrName;
    public IDebugCodeContext pCode;
}
```

## <a name="members"></a>Member
`bstrName`\
Der Name des Codepfads.

`pCode`\
Die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, an welcher Stelle in den Code einer Funktion in Einzelschritten identifiziert.

## <a name="remarks"></a>Hinweise
Diese Struktur wird verwendet, um Einzelschritt in eine Funktion zu implementieren. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) gibt alle Aufrufe von der aktuellen Position in die Anwendung gedebuggt wird. Diese Struktur stellt ein solcher Aufruf dar.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)
