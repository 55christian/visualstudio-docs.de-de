---
title: IDebugPointerField | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d92b1b4d6efda1b8f05c594368a05bd833c9f34
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705829"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Zeiger dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die symbolanbieter implementiert diese Schnittstelle, um einen Zeiger darstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) dieser Schnittstelle vom Abrufen der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) gibt `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die `IDebugField` und `IDebugContainerField` Schnittstellen, die diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , beschreibt das Ziel des Zeigers.|  
  
## <a name="remarks"></a>Hinweise  
 In C/C++ kann ein Zeiger auf einen Container sein, wenn sie mit der Arraynotation verwendet wird. Angenommen, `char *pString`, `pString` verfügt über einen Typ eines Zeigers auf den `char`. `pString[3]` weist den Typ des einem Container ist ein Zeiger auf `char` , die auf das vierte Element der diesem Container verweist.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
