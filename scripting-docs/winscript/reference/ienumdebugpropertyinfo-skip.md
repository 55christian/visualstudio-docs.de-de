---
title: IEnumDebugPropertyInfo::Skip | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7544b8ea54fabc53e6c8476648e339c53da94d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963389"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Überspringt eine angegebene Anzahl von `DebugPropertyInfo` Strukturen in einer Enumerationsfolge.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der `DebugPropertyInfo` Strukturen in der Enumerationsfolge übersprungen.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`. Gibt `S_FALSE` und Elementzeiger für den aktuellen am Ende der Enumeration festgelegt wird, wenn `celt` ist größer als die Anzahl der Elemente nach links im Enumerator.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugPropertyInfo-Schnittstelle](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)