---
title: IDispError::QueryErrorInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.QueryErrorInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 828497eac8bb2751baeca8b1fe19b5aeb5aae6a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446807"
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
Ruft einen bestimmten Typ von Fehlerinformationen ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidErrorType`  
 [in] Beim Angeben der Fehlertyp ist ein GUID.  
  
 `ppde`  
 [out] Gibt das IDispError-Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die `QueryErrorInfo` Methode ruft eine bestimmte Art von Fehlerinformationen ab.  
  
> [!NOTE]
> Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)