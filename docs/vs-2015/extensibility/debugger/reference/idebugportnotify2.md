---
title: IDebugPortNotify2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 72e420a0601f4b78198723a2173e542d93a9206e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957586"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle registriert oder hebt die Registrierung für ein Programm, das den Port zum Debuggen verwendet werden kann, die es ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um das Hinzufügen und Entfernen von Programmen vom Port unterstützt. Sie wird in der Regel implementiert, für das gleiche Objekt, das implementiert die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf die `IDebugPort2` Schnittstelle zurückgibt, diese Schnittstelle. Darüber hinaus einen Aufruf von [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) dieser Schnittstelle zurück. Ein Debugmodul sehen diese Schnittstelle als Parameter an [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPortNotify2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registriert ein Programm, das Debuggen kann mit dem Port, den es ausgeführt wird.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Hebt die Registrierung für ein Programm, das vom Port debuggt werden kann, die es ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Es sei denn, ein Debugport erkennen, wenn Programme geladen oder entladen werden, muss ein benutzerdefinierten Port Lieferanten über diese Schnittstelle implementieren. Alle Programme, die geladen werden, für das Debuggen über einen bestimmten Port werden nachverfolgt mithilfe dieser Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
