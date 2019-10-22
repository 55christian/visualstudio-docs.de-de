---
title: 'Ijsdebugdatatarget:: Read Memory-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572431"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory-Methode
Liest den Arbeitsspeicher des Zielprozesses.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `address`  
 [in] Die Basisadresse, aus der der Arbeitsspeicher des Zielprozesses zu lesen ist.  
  
 `flags`  
 [in] Flags, die das Verhalten von ReadMemory steuern.  
  
 `pBuffer`  
 [out] Ein Puffer, der den Inhalt vom Adressbereich des Zielprozesses empfängt. Beim Fehlschlagen wird der Inhalt dieses Puffers nicht angegeben.  
  
 `size`  
 [in] Die Anzahl an Bytes, die aus dem Prozess gelesen werden sollen.  
  
 `pBytesRead`  
 [out] Gibt die Anzahl der Bytes an, die aus dem Zielprozess gelesen wurden. Wenn "JsDebugAllowPartialRead" nicht aktiviert ist, wird bei Erfolg dieser Wert immer genau der Eingabegröße entsprechen. Wenn "JsDebugAllowPartialRead" angegeben ist, wird bei Erfolg dieser Wert größer als null sein.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Gibt bei Erfolg S_OK zurück, und Fehlercodes werden für jeden Fehler verwendet. Gibt E_JsDEBUG_INVALID_MEMORY_ADDRESS zurück, wenn die Adresse ungültig ist. Weitere Informationen finden Sie unter "JsDebugAllowPartialRead".  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)