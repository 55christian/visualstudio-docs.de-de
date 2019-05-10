---
title: 'Ijsdebugdatatarget:: FreeVirtualMemory-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf450c03d996a47f9dcd00899ddee46b75d6df32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583040"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory-Methode
Führt Freigabe und/oder Aufhebung der Zusage eines Arbeitsspeicherbereich innerhalb des virtuellen Adressraums des Zielprozesses aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `address`  
 [in] Adresse innerhalb des Zielprozesses, in dem der Arbeitsspeicher freigegeben werden soll.  
  
 `size`  
 [in] Anzahl der aufzuhebenden Bytes. Um einen Bereich des Arbeitsspeichers freizugeben, muss dieser Wert null sein.  
  
 `freeType`  
 [in] Gibt den Typ des auszuführenden freigegebenen Vorgangs an. Dies ist in der Regel MEM_RELEASE (0x8000), was den angegebenen Bereich von Seiten freigibt. Nach dem Vorgang sind die Seiten freigegeben. "MEM_DECOMMIT (0x4000)" kann stattdessen verwendet werden, um die Zusage der Seiten aufzuheben, ohne sie freizugeben.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen finden Sie in der VirtualFree-Win32-API.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)