---
title: IDebugPendingBreakpoint2::GetBreakpointRequest | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest
helpviewer_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest method
- GetBreakpointRequest method
ms.assetid: cb1e36aa-4302-455c-98fb-6638a1ef5c46
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50f4c2f2e0358819683fff281898278c7096327b
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "58959228"
---
# <a name="idebugpendingbreakpoint2getbreakpointrequest"></a>IDebugPendingBreakpoint2::GetBreakpointRequest
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Haltepunkt-Anforderung, die mit diesem ausstehenden Haltepunkt erstellt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetBreakpointRequest(   
   IDebugBreakpointRequest2** ppBPRequest  
);  
```  
  
```csharp  
int GetBreakpointRequest(   
   out IDebugBreakpointRequest2 ppBPRequest  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppBPRequest`  
 [out] Gibt eine [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Objekt, das die Haltepunkt-Anforderung, die verwendet wurde, zum Erstellen dieser ausstehenden Haltepunkt darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Haltepunkt gelöscht wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
