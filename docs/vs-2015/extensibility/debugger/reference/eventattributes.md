---
title: EVENTATTRIBUTES | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3026845be9aa6623d6c5cd42406385e8c5c2a11e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149376"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Attribute des Ereignisses.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>Member  
 EVENT_ASYNCHRONOUS  
 Gibt an, dass das Ereignis asynchron ist und keine Antwort auf das Ereignis ist erforderlich.  
  
 EVENT_SYNCHRONOUS  
 Gibt an, dass das Ereignis synchron ist. Antworten von [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT_STOPPING  
 Gibt an, dass es sich um eine Beenden-Ereignis handelt. Muss zusammen mit entweder `EVENT_ASYNCHRONOUS` oder `EVENT_SYNCHRONOUS`.  
  
 EVENT_ASYNC_STOP  
 Gibt eine asynchrone Stopping-Ereignis an. Es gibt derzeit kein entsprechendes Ereignis. Dieses Flag ist nur ein Platzhalter.  
  
 EVENT_SYNC_STOP  
 Gibt eine synchrone Stopping-Ereignis (eine Kombination von `EVENT_SYNCHRONOUS` und `EVENT_STOPPING`). Dieser Wert wird verwendet, durch eine DebugEngine (DE), wenn er eine Beenden-Ereignis sendet. Die Antwort erfolgt durch einen Aufruf von [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md), oder [Weiter](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT_IMMEDIATE  
 Gibt an, ein Ereignis, das für die IDE sofort und synchron gesendet wird. Dieses Flag wird zusammen mit anderen Flags wie `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, oder `EVENT_SYNC_STOP` , geben Sie den Typ des Ereignisses und die Tatsache, dass die Antwort-Mechanismus (sofern vorhanden) bekannt ist.  
  
 EVENT_EXPRESSION_EVALUATION  
 Das Ereignis ist das Ergebnis der Auswertung des Ausdrucks.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden übergeben, der `dwAttrib` Parameter, der die [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Methode.  
  
 Diese Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
