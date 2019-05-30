---
title: EXCEPTION_STATE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8f05596b12151b3a40b87c6fc2f15659a38e3431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337691"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Gibt den Ausnahmezustand.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Felder
`EXCEPTION_NONE`\
Beenden Sie nicht an der Ausnahme.

`EXCEPTION_STOP_FIRST_CHANCE`\
Beenden Sie am ersten Auslösen der Ausnahme. Wenn Sie einem Ausnahmeereignis zu beschreiben, gibt dieses Flag an, dass die Ausnahmeereignis ein Ereignis für die Ausnahme der ersten Chance ist.

`EXCEPTION_STOP_SECOND_CHANCE`\
Beenden Sie am zweiten Auslösung der Ausnahme. Wenn Sie einem Ausnahmeereignis beschreiben zu können, gibt an, dass das Ausnahmeereignis eine zweite Chance Ausnahmeereignisses.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Beenden Sie am ersten Auslösen einer Ausnahme des User-Modus. Wenn Sie einem Ausnahmeereignis beschreiben zu können, gibt an, dass das Ausnahmeereignis ein Ereignis für nicht abgefangene Ausnahme.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Beendet, wenn eine Benutzer-Modus-Ausnahme nicht abgefangen wird. Wenn Sie einem Ausnahmeereignis beschreiben zu können, gibt an, dass das Ausnahmeereignis eine nicht abgefangene Benutzerereignis Modus Ausnahme.

`EXCEPTION_STOP_ALL`\
Bei jeder Ausnahme beendet. Nicht verwendet, wenn Sie ein Ausnahmeereignis beschreiben.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Wenn Sie einem Ausnahmeereignis zu beschreiben, gibt Sie an, dass über die Ausnahme fortgesetzt werden kann nicht.

`EXCEPTION_CODE_SUPPORTED`\
Gibt an, dass die Ausnahme unterstützen Code verfügt. Bei der Anzeige einer Ausnahme verwendet

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Gibt an, dass der Ausnahmecode im Hexadezimalformat angezeigt werden soll. Bei der Anzeige einer Ausnahme verwendet.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Gibt an, dass der Ausnahmecode JustMyCode unterstützt. Bei der Anzeige einer Ausnahme verwendet.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Gibt an, dass der Debugger für verwalteten Code Ausnahmen verarbeiten soll. Wenn dies nicht festgelegt ist, der Standarddebugger behandelt die Ausnahmen. Diese wird zum Übergeben der [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) Methode und nicht in verwendet die [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
VERALTET, VERWENDEN SIE NICHT.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
VERALTET, VERWENDEN SIE NICHT.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
VERALTET, VERWENDEN SIE NICHT.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
VERALTET, VERWENDEN SIE NICHT.

## <a name="remarks"></a>Hinweise
Verwendet als die `dwState` Mitglied der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur geben den Zustand der Ausnahme und wozu dazu verwendet werden können.

Diese Werte werden auch zum Übergeben der [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) Methode zum Festlegen des Status für alle Ausnahmen.

Diese Flags können mit einem bitweisen OR kombiniert werden.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
