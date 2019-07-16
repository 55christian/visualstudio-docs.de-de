---
title: IDebugEngineCreateEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 088de1540a07e85bfb474308987302d8a7c613ba
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352459"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
Die Debug-Engine (DE) sendet diese Schnittstelle für die Sitzung Debug-Manager (SDM), wenn eine Instanz des DE erstellt wird.

## <a name="syntax"></a>Syntax

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle als Teil der normalen Vorgänge. Der [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden (das SDM verwendet die `QueryInterface` Methode, um Zugriff auf die `IDebugEvent2` Schnittstelle).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, bei der DE instanziiert wurde. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn diese an die zu debuggende Programm wird angefügt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugEngineCreateEvent2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Ruft das Objekt, das das neu erstellte Debugmodul (DE) darstellt.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)