---
title: IDebugApplicationThread110::IsThreadCallable | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90f0010a513adef67af1285ac15bc35d4573df57
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440509"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Bestimmt, ob dieser Thread in einem Zustand befindet, die Aufrufe, die über das PDM Threadwechsel Mechanismen, wie z. B. SynchronousCallInThread verarbeitet werden.  
  
> [!IMPORTANT]
> [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md) wird implementiert von PDM V11. 0 und höher. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pfIsCallable`  
 [out] `true` Wenn der Thread aufgerufen wird, andernfalls `false`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThread110-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md)