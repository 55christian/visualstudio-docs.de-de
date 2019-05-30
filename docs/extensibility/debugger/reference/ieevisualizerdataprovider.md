---
title: IEEVisualizerDataProvider | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 269f154083f3589e989a6ca2f9ce0835b249181a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350179"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle bietet die Möglichkeit, den Wert eines Objekts über eine typschnellansicht zu ändern.

## <a name="syntax"></a>Syntax

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die ausdrucksauswertung implementiert diese Schnittstelle, um die Änderung von Daten auf ein Objekt über eine typschnellansicht unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird verwendet, bei der Erstellung der [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Objekt durch einen Aufruf von [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) Weitere Details.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge

|Methode|Beschreibung|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Bestimmt, ob es möglich ist, aktualisieren Sie das Objekt (und anschließend den Wert), die diese Schnellansicht ist, darstellt.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Erzwingt eine erneute Auswertung der das Objekt für diese Schnellansicht.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ruft ein vorhandenes Objekt für diese Schnellansicht (keine Auswertung erfolgt) ab.|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualisiert das Objekt für diese Schnellansicht, ändern und somit auch den Wert, den die Schnellansicht zeigt.|

## <a name="remarks"></a>Hinweise
 Die schnellansichtsdienst (dargestellt durch die [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Schnittstelle und zurückgegeben, indem [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) behält einen Verweis auf das Objekt implementiert die `IEEVisualizerDataProvider` Schnittstelle . Daher die `IEEVisualizerDataProvider` Schnittstelle sollte nicht implementiert werden, für das gleiche Objekt, das implementiert die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Wenn dieses Objekt einen Verweis auf verwaltet die `IEEVisualizerService` Objekt: ein Zirkelverweis Ergebnisse und ein Deadlock tritt auf, wenn die Objekte zerstört werden. Wird empfohlen, implementieren `IEEVisualizerDataProvider` auf ein separates Objekt, das `IDebugProperty2` Objekt Delegaten ohne `IUnknown::AddRef` darauf.

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)