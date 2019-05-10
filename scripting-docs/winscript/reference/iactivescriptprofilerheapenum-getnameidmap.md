---
title: IActiveScriptProfilerHeapEnum::GetNameIdMap | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3284557bf71a038d884c1f8786755b7761770e21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992863"
---
# <a name="iactivescriptprofilerheapenumgetnameidmap"></a>IActiveScriptProfilerHeapEnum::GetNameIdMap
Gibt die Zeichenfolgennamen für [PROFILER_HEAP_OBJECT_NAME_ID-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md) Werte.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetNameIdMap (    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],     [out] UINT *pcelt);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pNameList`  
 [out] Ein Array von Namen zugeordnete [PROFILER_HEAP_OBJECT_NAME_ID-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md) Werte.  
  
 `pcelt`  
 [out] Die Anzahl der Namen im Array.  
  
## <a name="return-value"></a>Rückgabewert  
 Das HRESULT.