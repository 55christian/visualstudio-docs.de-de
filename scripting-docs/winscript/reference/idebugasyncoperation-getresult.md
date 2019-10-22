---
title: 'Idebugasyncoperation:: GetResult | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573282"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Stellt den Rückgabewert und den Rückgabe Objekt Parameter aus dem synchronen Debugvorgang bereit.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phrResult`  
 vorgenommen Wenn der Vorgang beendet ist, ist `phrResult` der Rückgabewert von `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 vorgenommen Wenn der Vorgang beendet ist, ist `ppunkResult` der vom Vorgang zurückgegebene Objekt Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang wurde nicht abgeschlossen.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Vorgang abgeschlossen wurde, gibt diese Methode den `HRESULT`-und den Object-Parameter von `IDebugSyncOperation::Execute` zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugasyncoperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)    
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)