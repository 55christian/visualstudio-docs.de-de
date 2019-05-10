---
title: IDispError::GetHelpInfo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa831ff511ea507e03ca858b93383ff38ead9039
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446913"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Gibt den Pfad der Hilfedatei und des Themas, das den Fehler, wenn möglich wird erläutert, die Kontext-ID zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrFileName`  
 [out] Eine Zeichenfolge, die den vollqualifizierten Pfad der Hilfedatei enthält. Wenn keine Hilfe-Datei vorhanden ist, oder ein Fehler auftritt, ist der Rückgabewert NULL.  
  
 `pdwContext`  
 [out] Die Hilfekontext-ID für den Fehler. Wenn keine Hilfe-Datei vorhanden ist (Wenn `pbstrFileName` NULL ist), dieser Parameter hat keine Bedeutung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Ein anbieterspezifischer Fehler ist aufgetreten.|  
|`E_INVALIDARG`|`pbstrFileName` oder `pdwContext` war NULL.|  
|`E_OUTOFMEMORY`|Der Anbieter konnte nicht genügend Speicher in den Pfad der Hilfe zurückgegeben.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt den Pfad der Hilfedatei und des Themas, das den Fehler, wenn möglich wird erläutert, die Kontext-ID zurück.  
  
> [!NOTE]
> Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)