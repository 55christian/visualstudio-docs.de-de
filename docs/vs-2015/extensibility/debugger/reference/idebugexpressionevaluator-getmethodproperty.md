---
title: IDebugExpressionEvaluator::GetMethodProperty | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b84ac959241a8f68f4d9516879660b6414708731
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155362"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ruft ein Objekt, das die lokalen Variablen, Argumente und andere Eigenschaften einer Methode enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pSymbolProvider`  
 [in] Der symbolanbieter verwendet werden, ausgedrückt als eine [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) Objekt.  
  
 `pAddress`  
 [in] Die Adresse im Code als ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Funktion-Objekt, das zum nächsten mit aufgelöst werden sollen.  
  
 `pBinder`  
 [in] Der Binder verwendet werden, ausgedrückt als eine [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) Objekt.  
  
 `fIncludeHiddenLocals`  
 [in] Ungleich Null (`TRUE`) bedeutet, dass enthalten ausgeblendete "lokal"; 0 (null) (`FALSE`) bedeutet, dass ausgeblendete "lokal" auslassen  
  
 `ppProperty`  
 [out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das die Methode darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ausgeblendete "lokal" werden in der Regel Variablen, die vom Compiler generiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
