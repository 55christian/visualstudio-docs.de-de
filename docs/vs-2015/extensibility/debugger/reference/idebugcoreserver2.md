---
title: IDebugCoreServer2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192913"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird verwendet, um darzustellen, und beziehen Sie Informationen von einem Server auf einem Computer im Netzwerk.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um einen Server darstellen. Jede Instanz von Visual Studio erstellt eine Instanz dieser Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein benutzerdefinierten Port Lieferanten empfängt diese Schnittstelle in einem Aufruf von [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Ein Debugmodul erhalten diese Schnittstelle indirekt durch einen Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (gibt [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), eine Schnittstelle, die abgeleitet wird `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugCoreServer2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ruft den Namen und die Attribute eines Computers.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ruft den Namen eines Computers.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ruft eines portanbieters vorhanden ist, die auf einem Computer ab.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ruft ab einen Port, der auf einem Computer bereits vorhanden ist.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Erstellt einen Enumerator für alle Ports auf einem Computer an.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Erstellt einen Enumerator für alle Lieferanten für den Port auf einem Computer an.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ruft die Hilfsprogramme für die Computer für einen Computer ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird auch von Visual Studio verwendet, um Prozesse, die auf Computern im Netzwerk zu suchen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
