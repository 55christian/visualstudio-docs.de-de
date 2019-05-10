---
title: IScriptEntry::SetText | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- ISetEntry::SetText
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17e716a7ad52cc5aeca18d02122edb9c457b14e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787631"
---
# <a name="iscriptentrysettext"></a>IScriptEntry::SetText
Legt den Text, der entspricht einer `IScriptEntry` Skriptblock oder der Quellcode, der in enthalten ist ein `IScriptScriptlet` -Ereignishandler.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `psz`  
 [in] Der Text des der `IScriptEntry` Skriptblock oder den Quellcode der `IScriptScriptlet` -Ereignishandler.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)