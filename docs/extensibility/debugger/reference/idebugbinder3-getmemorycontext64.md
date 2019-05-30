---
title: IDebugBinder3::GetMemoryContext64 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetMemoryContext64
- IDebugBinder3::GetMemoryContext64
ms.assetid: f021fd16-9fc7-4c41-86af-e54e6224cfbb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92c589951e9b65536be5474f56eb6b959232b738
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327070"
---
# <a name="idebugbinder3getmemorycontext64"></a>IDebugBinder3::GetMemoryContext64
Konvertiert entweder auf ein Objektspeicherort oder auf einer 64-Bit-Speicheradresse in einen Kontext an Arbeitsspeicher an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryContext64 (
    IDebugField*           pField,
    UINT64                 uConstant,
    IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext64 (
    IDebugField              pField,
    ulong                    uConstant,
    out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parameter
`pField`\
[in] Ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , beschreibt das zu suchende Objekt. Wenn `NULL`, verwenden Sie dann `dwConstant` stattdessen.

`uConstant`\
[in] Eine 64-Bit-Speicheradresse, z. B. 0x50000000.

`ppMemCxt`\
[out] Gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Schnittstelle, die die Adresse des Objekts oder die Adresse im Speicher darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
In den folgenden Beispielen wird ein Objekt, implementiert die [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md) Schnittstelle, und verwendet diese Methode zum Abrufen des Kontexts Arbeitsspeicher.

```cpp
HRESULT CValueProperty::GetMemoryContext ( IDebugMemoryContext2** out_ppMemoryContext )
{
    // precondition
    REQUIRE( NULL != out_ppMemoryContext );

    if (NULL == out_ppMemoryContext)
        return E_POINTER;

    *out_ppMemoryContext = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    if (VT_EMPTY == this->m_VarValue.vt)
    {
        return E_FAIL;
    }

    // function body
    if (NULL != this->m_pBinder)
    {
        UINT64 dwOffset = 0;

        DEBUG_PROPERTY_INFO dpInfo;
        HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_VALUE,
                                           10, // RADIX
                                           DEFAULT_TIMEOUT,
                                           NULL,
                                           0,
                                           &dpInfo);
        if (ENSURE( S_OK == HR ))
        {
            REQUIRE( NULL != dpInfo.bstrValue );
            REQUIRE( NULL == dpInfo.bstrName );
            REQUIRE( NULL == dpInfo.bstrFullName );
            REQUIRE( NULL == dpInfo.bstrType );
            REQUIRE( NULL == dpInfo.pProperty );

            wchar_t * end;
            dwOffset = _wcstoui64(dpInfo.bstrValue, &end, 0); // base 0 to allow 0x if it's ever output
            ::SysFreeString(dpInfo.bstrValue);
        }

        if (CComQIPtr<IDebugBinder3> binder3 = this->m_pBinder)
            HR = binder3->GetMemoryContext64(NULL, dwOffset, out_ppMemoryContext);
        else
            HR = this->m_pBinder->GetMemoryContext(NULL, (DWORD)(__int32)dwOffset, out_ppMemoryContext);

        if (ENSURE( S_OK == HR ))
        {
            REQUIRE( NULL != *out_ppMemoryContext );
        }
    }

    // postcondition
    INVARIANT( this );

    HRESULT HR = E_FAIL;

    if (NULL != *out_ppMemoryContext)
    {
        HR = S_OK;
    }

    return HR;
}
```

## <a name="see-also"></a>Siehe auch
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
