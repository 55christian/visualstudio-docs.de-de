---
title: EXCEPTION_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c5863c9ebb790ebcbc267f62cc2a0a1fd14603c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686261"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Beschreibt eine Ausnahme oder ein Laufzeitfehler ausgegeben, die von der zu debuggende Programm wird ausgelöst.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Member
pProgram der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm darstellt, in dem die Ausnahme aufgetreten ist.

BstrProgramName den Namen des Programms in der die Ausnahme aufgetreten ist.

BstrExceptionName den Namen der Ausnahme.

DwCode den ID-Code für die Ausnahme oder ein Laufzeit-Fehler.

dwState-Datenmember ein Wert aus der [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Enumeration, die den Zustand der Ausnahme definiert.

Die GUID-Sprachbezeichner GuidType, entweder `guidLang` oder `guidEng`.

## <a name="remarks"></a>Hinweise
Diese Struktur wird als Parameter an übergeben die [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) und [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) Methoden. Diese Struktur wird ebenfalls übergeben, um die [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) Methode gefüllt werden soll.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
