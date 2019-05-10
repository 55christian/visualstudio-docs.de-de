---
title: IDebugModule3::GetSymbolInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5fedebe6a8e411e09b527841bd0ded3854749ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918852"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Ruft eine Liste der Pfade, die für Symbole als auch die Ergebnisse der Suche von jedem Pfad durchsucht werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

#### <a name="parameters"></a>Parameter
`dwFields`

 [in] Eine Kombination von Flags aus der [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) Enumeration angeben welche Felder der `pInfo` in ausgefüllt werden.

`pInfo`

 [out] Ein [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) -Struktur, deren Mitglieder sind, sich mit den angegebenen Informationen gefüllt werden soll. Wenn dies ein null-Wert ist, gibt diese Methode `E_INVALIDARG`.

## <a name="return-value"></a>Rückgabewert
Wenn die Methode erfolgreich ist, gibt es `S_OK`ist, andernfalls einen Fehlercode zurückgegeben.

> [!NOTE]
> Die zurückgegebene Zeichenfolge (in der `MODULE_SYMBOL_SEARCH_INFO` Struktur) kann leer sein. auch wenn `S_OK` zurückgegeben wird. In diesem Fall gab es keine Suchinformationen zurückgegeben.

## <a name="remarks"></a>Hinweise
Wenn die `bstrVerboseSearchInfo` Feld der `MODULE_SYMBOL_SEARCH_INFO` Struktur ist nicht leer, und es enthält eine Liste von Pfaden, die durchsucht und die Ergebnisse dieser Suche. Die Liste wird mit einem Pfad, gefolgt von einer mit den Auslassungspunkten ("…"), gefolgt von das Ergebnis formatiert. Wenn mehr als ein Paar der Path-Ergebnis vorhanden ist, wird jedes Paar von ein Paar aus "\r\n" (Wagenrücklauf/Zeilenvorschub) getrennt. Das Muster sieht folgendermaßen aus:

\<Pfad >... \<Ergebnis > \r\n\<Pfad >... \<Ergebnis > \r\n\<Pfad >... \<Ergebnis >

Beachten Sie, dass der letzte Eintrag nicht mit eine Sequenz \r\n verfügt.

## <a name="example"></a>Beispiel
In diesem Beispiel gibt diese Methode drei Pfade mit drei unterschiedliche Ergebnisse zurück. Jede Zeile wird mit einem Paar aus Wagenrücklauf/Zeilenvorschub beendet. Die Beispielausgabe gibt nur die Ergebnisse der Suche als einzelne Zeichenfolge.

> [!NOTE]
> Einem statusergebnis ist alles, was unmittelbar nach dem "..." bis zum Ende der Zeile.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\symbols\user32.pdb... Die Datei wurde nicht gefunden. ** 
 **c:\winnt\symbols\user32.pdb... Version stimmt nicht überein. ** 
 ** \\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbole geladen.**

## <a name="see-also"></a>Siehe auch

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
