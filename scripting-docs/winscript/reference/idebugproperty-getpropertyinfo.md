---
title: IDebugProperty::GetPropertyInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51cf7fae597d95b0d9098d6b2dc6950c2d06bfa0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979148"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Ruft den Wert des einem `IDebugProperty` , die eine Methode oder eine indizierte Eigenschaft beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 [in] Gibt an, die `DBGPROP_INFO_FLAGS` Konstanten, die bestimmen, die Felder in ausgefüllt werden, müssen die `DebugPropertyInfo` Struktur.  
  
 `nRadix`  
 [in] Die Basis bei der Formatierung von numerischen Informationen verwendet werden.  
  
 `pPropertyInfo`  
 [out] Gibt die `DebugPropertyInfo` Struktur, die die Eigenschaft beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo-Struktur](../../winscript/reference/debugpropertyinfo-structure.md)