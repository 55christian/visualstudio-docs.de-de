---
title: 'Ijsdebugframe:: Evaluate-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b328d6071ae9dc96b8e7f62bad6d4417aa1730f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558189"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate-Methode
Werten Sie einen Ausdruck im Kontext dieses Stapelrahmens aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pExpressionText`  
 [in] Der auszuwertende Ausdruck.  
  
 `ppDebugProperty`  
 [out] Objekt, das den Eigenschaftenbrowser darstellt.  
  
 `pError`  
 [out] Die Fehlermeldung, wenn ein Fehler auftritt.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Gibt Folgendes zurück: S_OK: Auswertung folgt, * PpDebugProperty enthält Auswertungsergebnis. S_FALSE: Auswertung löst einen Fehler (oder der Auswertungsvorgang wird nicht unterstützt), \*pError enthält die Fehlermeldung angezeigt.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugFrame-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)