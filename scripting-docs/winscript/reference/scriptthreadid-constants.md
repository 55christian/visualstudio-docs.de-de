---
title: SCRIPTTHREADID-Konstanten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfbb39d10d552141a68d40a7be3f1715a80f8f57
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840200"
---
# <a name="scriptthreadid-constants"></a>SCRIPTTHREADID-Konstanten
Dient zum Angeben des Typs des Threads.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Konstanten  
  
|Konstante|Wert|Bedeutung|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Der aktuell ausgeführten Thread.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Die Basis-Thread. instanziiert wurde, also die in dem der Skript-Engine-Threads.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Alle Threads.|  
  
## <a name="remarks"></a>Hinweise  
 Die `SCRIPTTHREADID` Typ wird verwendet, indem `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, und `IActiveScript::InterruptScriptThread`, aber die Konstanten können nur verwendet werden, indem `IActiveScript::GetScriptThreadState` und `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)