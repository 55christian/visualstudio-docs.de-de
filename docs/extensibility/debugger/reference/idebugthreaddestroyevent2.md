---
title: IDebugThreadDestroyEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7d0d2990c5286a277164d58e74ec2d96fa176e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319994"
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
Diese Schnittstelle wird von der Debug-Engine (DE) für die Sitzung Debug-Manager (SDM) gesendet, wenn ein Thread bis zum Abschluss ausgeführt wurde.

## <a name="syntax"></a>Syntax

```
IDebugThreadDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle für den Bericht, der ein Thread beendet wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die DE erstellt und sendet dieses Ereignisobjekt an den Bericht, der ein Thread beendet wurde. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn es um das derzeit debuggte Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugThreadDestroyEvent2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|Ruft Exitcode des Threads ab.|

## <a name="remarks"></a>Hinweise
 Visual Studio verwendet dieses Ereignis zum Aktualisieren der **Threads** Fenster.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)