---
title: 'Idebugapplication:: SetName | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SetName
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a3e5115d4adc3fc3dfa93f10c90cb0d2b36f0e4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571106"
---
# <a name="idebugapplicationsetname"></a>IDebugApplication::SetName
Legt den Namen der Anwendung fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrName`  
 in Der Name der Anwendung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Der für diese Methode angegebene Name wird in nachfolgenden Aufrufen der `IRemoteDebugApplication::GetName`-Methode zurückgegeben.  
  
 Diese Methode sollte aufgerufen werden, bevor die `IProcessDebugManager::AddApplication`-Methode aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)