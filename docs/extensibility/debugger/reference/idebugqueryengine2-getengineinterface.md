---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c720ac348179ec979ba1ffbc1488244ca69246c4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339927"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Ruft einen benutzerdefinierten Debug-Engine (DE)-Schnittstelle ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parameter
`ppUnk`\
[out] Gibt eine `IUnknown` Objekt darstellt, die Debug-Engine (DE), und was für eine beliebige andere gültige Schnittstelle mit einer bereitgestellten Kompatibilitätsrichtlinie verknüpften abgefragt werden kann (z. B. [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oder [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die resultierende Schnittstelle sollte mit Vorsicht verwendet werden, da Aufrufen über Schnittstellen, die von dieser Methode abgerufen die sitzungsbasierter Debug-Manager-Verarbeitung umgeht und kann das SDM in einem fehlerhaften Zustand geraten, oder Generieren von Fehlern während des Debuggens zu.

## <a name="see-also"></a>Siehe auch
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)