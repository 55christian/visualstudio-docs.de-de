---
title: Ijsdebugprocess-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9200515b2c975fb1fa5b2acda7c261cb684d85b4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577345"
---
# <a name="ijsdebugprocess-interface"></a>IJsDebugProcess-Schnittstelle
Stellt Routinen zum Überprüfen und Steuern des Zielprozesses bereit.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Member  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|-Name|Beschreibung|  
|----------|-----------------|  
|[IJsDebugProcess::CreateBreakPoint-Methode](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Legt den Haltepunkt an der angegebenen Dokumentposition fest.|  
|[IJsDebugProcess::CreateStackWalker-Methode](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Factorymethode für Stapeldurchlauf.|  
|[IJsDebugProcess::PerformAsyncBreak-Methode](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Setzt die Skript-Engine in den Unterbrechungsmodus, der bei der nächsten Skriptanweisung eine Unterbrechung veranlasst.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)