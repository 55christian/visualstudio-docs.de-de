---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce1b5635685971b3a9390533589975ff0f323021
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203790"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Fügt an die zugeordnete Anwendung oder den anfügungsprozess, verzögert die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.

## <a name="syntax"></a>Syntax

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Parameter
`guidProgramId`\
[in] `GUID` an das zugeordnete Programm zuweisen.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode nicht aufgerufen werden soll. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird während des Prozesses anfügen aufgerufen, bevor die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methode wird aufgerufen. Die `OnAttach` -Methode kann den anfügungsprozess zu sich selbst ausführen (in diesem Fall ist diese Methode gibt `S_FALSE`) oder zurückgestellt werden, den anfügungsprozess, die `IDebugEngine2::Attach` Methode (die `OnAttach` Methodenrückgabe `S_OK`). In jedem Fall die `OnAttach` Methode kann festlegen, die `GUID` der die zu debuggende Programm wird auf der angegebenen `GUID`.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)