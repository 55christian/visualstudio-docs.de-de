---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c643478da37b5a66c22b201ef8f8248df02e4ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992340"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informiert, dass der Host über einen Laufzeit-Skriptfehler beim Debuggen des Prozesses Manager einen Just-in-Time-Skriptdebugger nicht gefunden wird.  
  
 Um einen Debugger in Ihrem Host zu implementieren, sollten Sie behandeln [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Basierend auf eine Benutzeraktion, die Hosts kann entweder den Debugger Anfügen und zurück oder gibt zurück, das Starten des Debuggers in der OnScriptErrorDebug `pfEnterDebugger` Parameter. Sie sollten auch implementieren diese Schnittstelle, um die Benachrichtigung über den Laufzeit-Fehler zu erhalten, selbst wenn es keine externen Debugger, die von den prozessbasierten Debugmanager interpretiert werden können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pErrorDebug`  
 [in] Der Laufzeit-Fehler, der aufgetreten sind.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Angibt, ob die aufzurufende [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) , wenn der Benutzer entscheidet, ohne das Debuggen fortzusetzen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sie sollten diese Schnittstelle, um eine Benachrichtigung auch implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebugEx-Schnittstelle](../../winscript/reference/iactivescriptsitedebugex-interface.md)