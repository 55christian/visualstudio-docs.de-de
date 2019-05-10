---
title: IActiveScriptSite::GetDocVersionString | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7327b71329c1f476eab9c27d5e0d5a047664abfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992746"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Ruft ab eine Host-definierte Zeichenfolge, die die aktuelle Dokumentversion eindeutig identifiziert. Wenn das zugehörige Dokument außerhalb des Bereichs der Windows-Skript (wie im Fall einer HTML-Seite, die bearbeitet wird, mit dem Editor) geändert hat, kann die Skript-Engine speichern diese zusammen mit den beibehaltenen Zustand, eine erzwungene Neukompilierung das nächste Mal, wenn das Skript geladen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pstrVersionString`  
 [out] Die Adresse der Versionszeichenfolge Host definiertes Dokument.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_NOTIMPL` Wenn diese Methode nicht unterstützt wird.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `E_NOTIMPL` zurückgegeben wird, wird die Skript-Engine sollten davon ausgehen, dass das Skript mit dem Dokument synchron ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)