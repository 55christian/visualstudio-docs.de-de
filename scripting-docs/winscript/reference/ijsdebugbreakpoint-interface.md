---
title: IJsDebugBreakPoint-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14823baeb999ad24aabef9b2b55b59a7b5d08c71
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583105"
---
# <a name="ijsdebugbreakpoint-interface"></a>IJsDebugBreakPoint-Schnittstelle
Stellt einen Haltepunkt dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>Member  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[IJsDebugBreakPoint::Delete-Methode](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|Löscht den Haltepunkt.|  
|[IJsDebugBreakPoint::Disable-Methode](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|Deaktiviert den Haltepunkt.|  
|[IJsDebugBreakPoint::Enable-Methode](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|Aktiviert den Haltepunkt.|  
|[IJsDebugBreakPoint::GetDocumentPosition-Methode](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|Gibt die Position der Anweisung zurück, wo der Haltepunkt gebunden wurde.|  
|[IJsDebugBreakPoint::IsEnabled-Methode](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|Bestimmt, ob der Haltepunkt aktiviert ist.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)