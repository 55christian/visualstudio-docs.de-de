---
title: IDebugBinder3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a08ee3f637b954d2df7e48fb8f6aebbdd0948c19
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414074"
---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle bietet Zugriff auf Typen, Aliase und benutzerdefinierte Schnellansicht-Dienste.

## <a name="syntax"></a>Syntax

```
IDebugBinder3 : IDebugBinder
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul implementiert diese Schnittstelle, um die Aliase, benutzerdefinierte Schnellansicht-Dienste und den Zugriff auf Objekttypen zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle ruft diese Schnittstelle mit [QueryInterface](/cpp/atl/queryinterface).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die bereitgestellt werden, indem die [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle, diese Schnittstelle implementiert, die folgenden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Ruft ein Speicherobjekt, das den Speicher an dem dieses Objekt gebunden ist darstellt.|
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Ruft ab, der die Ausnahme, die diesem Objekt (falls vorhanden) zugeordnet,|
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Ruft einen Alias mit dem angegebenen Namen ab,|
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Ruft ein Array aller Aliase für dieses Objekt ab,|
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Ruft die Anzahl von Argumenttypen, die diesem Objekt zugeordnet,|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Ruft eine Liste der Argumenttypen, die diesem Objekt zugeordnet,|
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Ruft eine Schnittstelle für einen schnellansichtsdienst,|
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Konvertiert entweder auf ein Objektspeicherort oder auf einer 64-Bit-Speicheradresse in einen Kontext an Arbeitsspeicher an.|

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)