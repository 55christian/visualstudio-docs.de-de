---
title: IDebugApplicationNode::Attach | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c41d06c116c7c15ad308ce2ace837ea01d90ab1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990483"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Der angegebene Projektstruktur wird dieser Anwendungsknoten hinzugefügt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdanParent`  
 [in] Die Projektstruktur, in dem dieser Anwendungsknoten ist, hinzugefügt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode fügt dieser Anwendungsknoten auf das Projekt-Struktur, mit der `pdanParent` als übergeordnetes Element. Wenn `pdanParent` ist `NULL`, diesen Anwendungsknoten werden die Knoten der obersten Ebene.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode-Schnittstelle](../../winscript/reference/idebugapplicationnode-interface.md)