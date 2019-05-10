---
title: IDebugPendingBreakpoint2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 816fad53554675e7f29cef838d4ea24e154dca8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871933"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Diese Schnittstelle stellt einen Haltepunkt an, der an einen Speicherort gebunden werden kann.

## <a name="syntax"></a>Syntax

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte an.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) erstellt einen ausstehenden Haltepunkt von einem [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Schnittstelle. Ein Aufruf von [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) erstellt eine `IDebugBreakpoint2` -Schnittstelle, die einen gebundenen Haltepunkt in der Anwendung darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugPendingBreakpoint2`.

|Methode|Beschreibung|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob diese ausstehende Haltepunkt an einen Speicherort gebunden werden kann.|
|[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Wird dieser ausstehenden Haltepunkt an einem oder mehreren Code-Speicherorten gebunden.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Status der ausstehenden Haltepunkts ab.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft die Haltepunkt-Anforderung, die mit diesem ausstehenden Haltepunkt erstellt wurde.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Schaltet den virtualisierten Zustand dieser ausstehenden Haltepunkt.|
|[Enable](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Zustand der ausstehenden Haltepunkt an.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Legt fest oder ändert die Bedingung, die zugeordneten ausstehenden Haltepunkt.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Legt fest oder ändert die Anzahl der Durchläufe ausstehender Haltepunkt zugeordnet.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Listet alle Breakpoints, die von diesem ausstehender Haltepunkt gebunden.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Listet alle Fehler Haltepunkte, die bei diesem ausstehender Haltepunkt an.|
|[Löschen](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht diese ausstehenden Haltepunkt, und alle Breakpoints, die von ihm gebunden.|

## <a name="remarks"></a>Hinweise
 `IDebugPendingBreakpoint2` kann der betrachtet werden, als Anbieter alle notwendigen Informationen erforderlich, um einen Haltepunkt in Code zu binden, die auf eine oder mehrere Programme angewendet werden können.

 Ein ausstehender Haltepunkt kann möglicherweise mehr als einen gebundenen Haltepunkt erzeugen. Beispielsweise konnte ein Haltepunkt in einer C++-Stil-Vorlage einen gebundenen Haltepunkt für jede eindeutige Instanz dieser Vorlage erstellen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)