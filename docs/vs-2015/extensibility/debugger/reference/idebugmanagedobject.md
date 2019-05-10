---
title: IDebugManagedObject | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be39e42de029b597d46fc775ef7df63c5d31c0c1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439058"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle ermöglicht die ausdrucksauswertung (EE) aufrufen, Eigenschaften oder Methoden auf Klasseninstanzen Wert (z. B. `System.Decimal`) und ihren Wert ohne festlegen [auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) auf die Anwendung gedebuggt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine ausdrucksauswertung implementiert diese Schnittstelle, um ein verwalteter Code-Objekt, z. B. eine Variable darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie zum Abrufen dieser Schnittstelle [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) auf eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , die eine Instanz einer Wertklasse darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Gibt eine Schnittstelle, die das Objekt von verwaltetem Code darstellt und aus der entsprechenden verwalteter Code Schnittstelle abgerufen werden kann.|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Legt den Wert dieses Objekts auf den Wert eines Objekts des angegebenen verwalteten Code fest.|  
  
## <a name="remarks"></a>Hinweise  
 Eine ausdrucksauswertung verwendet diese Schnittstelle, um ein Objekt von verwaltetem Code in eine Analysestruktur zu speichern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
