---
title: IActiveScriptStringCompare::StrComp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStringCompare.StrComp
apilocation:
- scrobj.dll
helpviewer_keywords:
- StrComp method, IActiveScriptStringCompare interface
ms.assetid: 124d1281-8037-4766-a2a1-61244ac1f114
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66cccb4281e19aebb25b3b4cde06705b500f53a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991432"
---
# <a name="iactivescriptstringcomparestrcomp"></a>IActiveScriptStringCompare::StrComp
Definiert die Methode zum Zeichenfolgenvergleich für die Skript-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT StrComp(  
// The first string:  
    [in] BSTR bszStr1,    
// The second string:   
    [in] BSTR bszStr2,    
// The result of the comparison:  
    [out, retval] LONG* iRet   
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bszStr1`  
 Die erste Zeichenfolge.  
  
 `bszStr2`  
 Die zweite Zeichenfolge.  
  
 `iRet`  
 Das Ergebnis des Vergleichs. 0, wenn `bszStr1` und `bszStr2`identisch sind; 1, wenn `bszStr1`  <  `bszStr2`; 1, wenn `bszStr1`  >  `bszStr2`.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument ist ungültig.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert).|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird jedes Mal aufgerufen, die ein Zeichenfolgenvergleich ausgeführt wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie die Funktion zum Zeichenfolgenvergleich überladen wird. Überladen ist zulässig, bei der Verwendung [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) SCRIPTPROP_STRINGCOMPAREINSTANCE festlegen.  
  
```cpp#  
cpp_quote("// {58562769-ED52-42f7-8403-4963514E1F11}")  
cpp_quote("DEFINE_GUID(IID_IActiveScriptStringCompare, 0x58562769,   
    0xED52, 0x42f7, 0x84, 0x03, 0x49, 0x63, 0x51, 0x4E, 0x1F, 0x11);")  
cpp_quote("")  
  
cpp_quote("#define SCRIPTPROP_INTEGERMODE              0x00003000")  
cpp_quote("#define SCRIPTPROP_STRINGCOMPAREINSTANCE    0x00003001")  
cpp_quote("")  
interface IActiveScriptStringCompare;  
[  
         object,  
         uuid(58562769-ED52-42f7-8403-4963514E1F11),  
         pointer_default(unique)  
]  
interface IActiveScriptStringCompare : IUnknown  
{  
        // StrComp  
        //     bszStr1: first string  
        //     bszStr2: second string  
        //     iRet: 0 if identical, -1 if bszStr1 < bszStr2, 1 if   
        //         bszStr1 > bszStr2  
        //            
        //     Return values:  
        //         S_OK: Success  
        //         E_NOTIMPL: Not implemented  
        //  
        HRESULT StrComp(  
                [in] BSTR bszStr1,  
                [in] BSTR bszStr2,  
                [out, retval] LONG* iRet  
        );  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptStringCompare-Schnittstelle](../../winscript/reference/iactivescriptstringcompare-interface.md)