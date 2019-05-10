---
title: IDebugProgram2::Step | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f841960eec9274139307f5fcc1bcaea9bb9fb8e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412858"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Führt einen Schritt aus.

> [!NOTE]
> Diese Methode ist veraltet. Verwenden der [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md) Methode stattdessen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

#### <a name="parameters"></a>Parameter
 `pThread`

 [in] Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread wird abgestuften darstellt.

 `sk`

 [in] Ein Wert aus der [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) -Enumeration, der den Typ des Schritts angibt.

 `step`

 [in] Ein Wert aus der [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) Enumeration, die die Einheit des Schritts (beispielsweise von einer Anweisung oder der Anweisung) angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Für den Fall, dass alle Threadsynchronisierung oder die Kommunikation zwischen Threads vorhanden ist, sollten andere Threads im Programm ausführen, wird ein Prozedurschritt ein bestimmter Thread ausgeführt.

> [!WARNING]
> Senden Sie eine Beenden-Ereignis oder ein sofort (synchron) Ereignis [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) bei der Verarbeitung dieser Aufruf ist; andernfalls der Debugger wird, reagiert.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)