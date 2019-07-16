---
title: IDebugPortEvents2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e0f6455e6df8db88b1aae1a7b7f6965c0ee524b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188528"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle informiert einen Listener Prozess und das Programm Erstellung und Zerstörung auf einem bestimmten Port (in der Regel die sitzungsbasierter Debug-Manager [SDM] oder einer Debug-Engine). Diese Informationen kann verwendet werden, um eine Echtzeitansicht der Prozesse und Programme, die an den Port zu präsentieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio wird in der Regel implementiert diese Schnittstelle zum Empfangen von Benachrichtigungen über die Erstellung und Zerstörung. Ein Debugmodul kann auch diese Schnittstelle zum Überwachen von Ereignissen Port implementieren.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Alle [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstellen abgefragt werden können, für eine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> -Methode für `IDebugPortEvents2` wird aufgerufen, der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> -Schnittstelle zum Abrufen einer <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle. Zum Schluss die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> -Methode in der die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle wird aufgerufen, um die Ereignisse durch Senden der [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md) Methode.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methode der `IDebugPortEvents2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Sendet Ereignisse, die die Erstellung und Zerstörung von Prozessen und Programme auf dem Port zu beschreiben.|  
  
## <a name="remarks"></a>Hinweise  
 `IDebugPortEvents2` durch die SDM dient auch zum Debuggen von Programmen, die in einem Prozess ausgeführt werden, die bereits im Debugmodus befindet.  
  
 Portereignisse werden an das SDM von dieser Schnittstelle übergeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
