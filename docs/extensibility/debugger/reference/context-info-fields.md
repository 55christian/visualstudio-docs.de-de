---
title: CONTEXT_INFO_FIELDS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ed50d43061ee714f8f892e03bb164f16e2e33d9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346385"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Gibt an, welche Informationen Sie über eine Speicherkontext abzurufen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Felder
`CIF_MODULEURL`\
Initialisieren und Verwenden der `bstrModuleUrl` Feld der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur.

`CIF_FUNCTION`\
Initialisieren und Verwenden der `bstrFunction` Feld der `CONTEXT_INFO` Struktur.

`CIF_FUNCTIONOFFSET`\
Initialisieren und Verwenden der `posFunctionOffset` Feld der `CONTEXT_INFO` Struktur.

`CIF_ADDRESS`\
Initialisieren und Verwenden der `bstrAddress` Feld der `CONTEXT_INFO` Struktur.

`CIF_ADDRESSOFFSET`\
Initialisieren und Verwenden der `bstrAddressOffset` Feld der `CONTEXT_INFO` Struktur.

`CIF_ALLFIELDS`\
Alle Felder initialisiert und Verwenden der `CONTEXT_INFO` Struktur.

## <a name="remarks"></a>Hinweise
Diese Werte werden übergeben einen Parameter für die [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) Methode, um die Felder anzugeben der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) sind, dass die Struktur initialisiert werden.

Diese Flags werden auch verwendet, welche Felder der an die `CONTEXT_INFO` -Struktur sind gültig und verwendet, wenn die Struktur zurückgegeben wird.

Diese Werte können mit einem bitweisen OR kombiniert werden.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
