---
title: IDebugAddress | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b9aba2be92516bab86f39eee55a3df4586eb09c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677963"
---
# <a name="idebugaddress"></a>IDebugAddress
Diese Schnittstelle stellt die Adresse eines Elements dar. Es wird von der Symbol-Handler zurückgegeben.

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein symbolanbieter implementiert diese Schnittstelle, um eine Adresse eines Objekts darstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Viele Methoden für viele Schnittstellen zurückgeben dieser Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Ruft eine [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur, die beschreibt ein Objekt und seine Position.|

## <a name="remarks"></a>Hinweise
 Der symbolanbieter gibt diese Schnittstelle, um ein Objekt und seine Position innerhalb eines bestimmten Bereichs (z. B. Funktion, Methode oder Klasse) darstellen. Diese Schnittstelle wird von zurückgegeben und, die an verschiedene Methoden für die symbolanbieter und Expression Evaluator. Der symbolanbieter ist in der Regel die einzige Entität, die zum Interpretieren des Inhalts dieser Schnittstelle benötigt.

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)