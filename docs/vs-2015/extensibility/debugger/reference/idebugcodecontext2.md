---
title: IDebugCodeContext2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e06fd709b2d076b6fa8de7f104e907eb1b35a42
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959755"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt die Anfangsposition der Anweisung für einen Code an. Für die meisten Laufzeit-Architekturen kann heute ein Codekontext als Adresse für die Ausführung Stream eines Programms betrachtet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine implementiert diese Schnittstelle, um die Position des eine Code-Anweisung an eine Dokumentposition beziehen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Methoden für viele Schnittstellen zurückgeben dieser Schnittstelle, i. d. r. [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Darüber hinaus wird häufig mit der [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) Schnittstelle auch wie in der Lösung breakpointinformationen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Ruft ab, der Dokumentenkontext, der auf den aktiven Code-Kontext entspricht.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Ruft die Sprachinformationen für diesen Codekontext ab.|  
  
## <a name="remarks"></a>Hinweise  
 Der Hauptunterschied zwischen einer `IDebugCodeContext2` Schnittstelle und eine [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Schnittstelle ist, die eine `IDebugCodeContext2` ist immer Anweisung ausgerichtet. Dies bedeutet, dass ein `IDebugCodeContext2` ist immer an den Anfang einer Anweisung verweist, während ein `IDebugMemoryContext2` können eventuell Hinweise auf jedes beliebige Byte des Arbeitsspeichers in der Laufzeit-Architektur. `IDebugCodeContext2` wird von Anweisungen und nicht von der grundlegenden Speichergröße (in der Regel Byte) erhöht.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [Nächste Anweisung festlegen](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
