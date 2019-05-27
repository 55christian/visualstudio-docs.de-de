---
title: IDebugProcess2::EnumThreads | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce6a4061992fd0b5c1328f2bd6c7dd1c688dfd80
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202672"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Ruft eine Liste aller Threads im Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) -Objekt, das eine Liste aller Threads in allen Programmen im Prozess enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode listet die Threads, die in jedem Programm ausgeführt wird und Sie dann in eine Prozessansicht der Threads. Ein einzelner Thread kann in mehrere Programme ausgeführt; Diese Methode listet dieser Thread nur einmal auf.

 Diese Methode stellt eine Liste der Threads des Prozesses, ohne Duplikate. Verwenden Sie zum Auflisten von Threads in einem bestimmten Programm ausgeführt wird, andernfalls die [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)