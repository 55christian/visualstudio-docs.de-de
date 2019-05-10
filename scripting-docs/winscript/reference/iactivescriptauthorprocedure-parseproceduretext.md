---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c513b105a483d0f80510dff9c91fa2c3f09e0523
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955158"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Eine Prozedur Code analysiert und fügt den Code der Prozedur Text an das Skript-Engine-Erstellung erstellt eine `IScriptEntry` Objekt, das die Code-Prozedur entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszCode`  
 [in] Der Skripttext analysiert werden soll.  
  
 `pszFormalParams`  
 [in] Die Adresse der formale Parameternamen für die Prozedur. Die Parameternamen müssen durch die entsprechenden Trennzeichen für das Skript-Engine-authoring getrennt werden. Die Namen sollten nicht in Klammern eingeschlossen werden.  
  
 `pszProcedureName`  
 [in] Die Adresse der den Namen der Prozedur, die analysiert werden.  
  
 `pszItemName`  
 [in] Die Pufferadresse, die den Namen des Elements enthält zugeordneten der `IScriptEntry` Objekt.  
  
 `pszDelimiter`  
 [in] Die Adresse des Trennzeichens Ende-des-Skript-Block. Wenn `pszCode` wird analysiert, die aus einem Stream des Texts, verwendet der Host in der Regel ein Trennzeichen (z. B. zwei einfache Anführungszeichen), um das Ende des Skriptblocks zu erkennen. Legen Sie diesen Parameter auf NULL, wenn kein Trennzeichen zum Kennzeichnen des Skriptblocks vorhanden ist.  
  
 `dwCookie`  
 [in] Einer der Anwendung definierter Wert, der mit dem neuen verknüpft ist `IScriptEntry` Objekt.  
  
 `dwFlags`  
 [in] Nicht verwendet.  
  
 `pdispFor`  
 [in] Nicht verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Die aktuelle [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Engine diese Methode nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptAuthorProcedure-Schnittstelle](../../winscript/reference/iactivescriptauthorprocedure-interface.md)