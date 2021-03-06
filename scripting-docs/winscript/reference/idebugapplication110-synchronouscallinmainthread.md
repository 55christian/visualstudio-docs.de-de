---
title: 'IDebugApplication110:: synchronouscallinmainthread | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db2b94d51cc5c9a65355aae7405fb162f564e0cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573650"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Führt einen synchronen-Rückruf für den Haupt Thread aus.  
  
> [!IMPORTANT]
> Die [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pptc`  
 Das aufzurufende [idebugthreadcallcenter-Schnittstellen](../../winscript/reference/idebugthreadcall-interface.md) Objekt.  
  
 `dwParam1`  
 Der erste Parameter des Aufrufes.  
  
 `dwParam1`  
 Der erste Parameter des Aufrufes.  
  
 `dwParam2`  
 Der zweite Parameter des Aufrufes.  
  
 `dwParam3`  
 Der dritte Parameter des Aufrufes.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication110-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md)