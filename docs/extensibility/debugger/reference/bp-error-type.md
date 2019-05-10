---
title: BP_ERROR_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2964c833abfa25b57678680f8b821f992cb31de8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689186"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Gibt den Fehlertyp eines Haltepunkts an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="members"></a>Member
BPET_NONE gibt kein haltepunktfehler an.

BPET_TYPE_WARNING gibt eine Warnung-Stil haltepunktfehler an.

BPET_TYPE_ERROR gibt Fehler Haltepunkt Error-Format an.

BPET_SEV_HIGH gibt einen mit hohem Schweregrad haltepunktfehler an.

BPET_SEV_GENERAL gibt einen mit mittleren Schweregrad haltepunktfehler an.

BPET_SEV_LOW gibt einen haltepunktfehler mit niedriger Schweregrad an.

BPET_TYPE_MASK gibt ein Maske-Stil haltepunktfehler an.

BPET_SEV_MASK gibt einen haltepunktfehler für Schweregrad-Maske-Style.

BPET_GENERAL_WARNING gibt einen haltepunktfehler für die allgemeine-Warnung-Style.

BPET_GENERAL_ERROR gibt eine allgemeine-Error-Format haltepunktfehler an.

BPET_ALL gibt alle Haltepunkttypen Fehler an.

## <a name="remarks"></a>Hinweise
Diese Werte können kombiniert werden, mit einer bitweisen `OR` und wird verwendet, für die `dwType` Mitglied der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur. Übergeben als Parameter an die [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) Methode.

Eine Haltepunkt-Fehlertyp besteht aus einem Typ und einen Schweregrad aus. Dies bedeutet, dass ein Fehler Haltepunkt niemals nur ein Typ ist (z. B. `BPET_TYPE_ERROR`,) oder einen Schweregrad (z. B. `BPET_SEV_GENERAL`) selbst. `BPET_GENERAL_WARNING` und `BPET_GENERAL_ERROR` Geben Sie vordefinierte Werte für allgemeine Warnungs- und Haltepunkte.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
