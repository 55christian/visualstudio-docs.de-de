---
title: IDebugAlias | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6c05b6987804681176abdde0e8c94a7463a9163c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442306"
---
# <a name="idebugalias"></a>IDebugAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt einen numerischen Alias für eine Variable dar. Ein Alias ist einfach einen anderen Namen für eine Variable.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung (EE) implementiert diese Schnittstelle, um numerische Aliase für Variablen zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) erstellt einen Alias für ein bestimmtes Objekt. Verwenden Sie zum Suchen nach Aliase [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) oder [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgenden Methoden definiert werden, der `IDebugAlias` Schnittstelle.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Ruft das Objekt, das auf dem dieser Alias verweist.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Ruft den Aliasnamen ab.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Ruft eine `ICorDebugValue` Schnittstelle für den Zugriff auf verwalteten Codeinformationen zu diesem Objekt (nur verwalteter Code).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Kennzeichnet dieses alias als nicht mehr verwendet wird.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Alias ist eine Dezimalzahl in Form einer Zeichenfolge gefolgt von dem #-Zeichen ein, z. B. 1001#.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
