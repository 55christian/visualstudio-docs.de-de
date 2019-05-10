---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8f1b5aac6df8d8659fa323f3f1efcb7721d97f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955057"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Gibt den Textattribute des Scriptlet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCode`  
 [in, Size_is (`cch`)] Scriptlet-Texts. Diese Zeichenfolge muss keine null-terminiert.  
  
 `cch`  
 [in] Die Größe des für die `pszCode` und `pattr` Parameter.  
  
 `pszDelimiter`  
 [in] Die Adresse des End-of-Scriptlet-Trennzeichens. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Scriptlets zu erkennen. Legen Sie diesen Parameter auf NULL, wenn kein Trennzeichen verwendet wird, um das Ende des Scriptlets zu identifizieren.  
  
 `dwFlags`  
 [in] Die Flags, die Textattributen des Scriptlets zugeordnet sind. Eine Kombination der folgenden Werte kann sein.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifizieren von Bezeichnern, die das SOURCETEXT_ATTR_IDENTIFIER-Attribut aufweisen, und geben Sie Punktoperatoren, die das SOURCETEXT_ATTR_MEMBERLOOKUP-Attribut aufweisen.|  
|GETATTRFLAG_THIS|0x0100|Identifizieren Sie das aktuelle Objekt, das das SOURCETEXT_ATTR_THIS-Attribut aufweist.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifizieren Sie die Zeichenfolge Inhalt, und kommentieren Text, der das SOURCETEXT_ATTR_HUMANTEXT-Attribut aufweist.|  
  
 `pattr`  
 [in, out, Size_is (`cch`)] die Farbinformationen für den Scriptlet-Code.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthor-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)