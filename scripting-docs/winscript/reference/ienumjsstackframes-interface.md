---
title: Ienumjsstackframes-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572030"
---
# <a name="ienumjsstackframes-interface"></a>IEnumJsStackFrames-Schnittstelle
Implementiert durch den Debugger, um zu "jscript9diag.dll" Stapelentladung für JavaScript bereitzustellen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Member  
  
### <a name="public-methods"></a>Öffentliche Methoden  
  
|-Name|Beschreibung|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next-Methode](../../winscript/reference/ienumjsstackframes-next-method.md)|Ruft die angegebene Anzahl an Frames ab.|  
|[IEnumJsStackFrames::Reset-Methode](../../winscript/reference/ienumjsstackframes-reset-method.md)|Setzt den Stapelrahmen auf die Position vor dem ersten Element zurück.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)