---
title: IDebugComPlusSymbolProvider::GetTypeFromAddress | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetTypeFromAddress
- GetTypeFromAddress
ms.assetid: 01f21ff9-e8a5-4e5f-9f7b-1b6de8b1432f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9670dd1c6c56e2e6b983dffc054aa23fddae6e09
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206273"
---
# <a name="idebugcomplussymbolprovidergettypefromaddress"></a>IDebugComPlusSymbolProvider::GetTypeFromAddress
Ruft ab, um ein Symboltyp, wenn die debugadresse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypeFromAddress(
    IDebugAddress* pAddress,
    IDebugField**  ppField
);
```

```csharp
int GetTypeFromAddress(
    IDebugAddress   pAddress,
    out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
[in] Die debugadresse, die durch dargestellt wird ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.

`ppField`\
[out] Gibt den Arraytyp zurück, dargestellt durch ein [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Schnittstelle.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.

```cpp
HRESULT CDebugSymbolProvider::GetTypeFromAddress(
    IDebugAddress *pAddress,
    IDebugField **ppField)
{
    HRESULT hr = E_FAIL;
    CDEBUG_ADDRESS da;
    CDebugGenericParamScope* pGenScope = NULL;

    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromPrimitive );

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppField, IDebugField*));

    IfFailGo( pAddress->GetAddress(&da) );

    switch ( da.addr.dwKind )
    {
        case ADDRESS_KIND_METADATA_LOCAL:
        case ADDRESS_KIND_METADATA_PARAM:
        case ADDRESS_KIND_METADATA_FIELD:
        case ADDRESS_KIND_METADATA_ARRAYELEM:
        case ADDRESS_KIND_METADATA_METHOD:
            {
                IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );
                break;
            }

        case ADDRESS_KIND_METADATA_RETVAL:
            {
                if ( da.addr.addr.addrRetVal.dwCorType )
                {

                    IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );
                    IfFailGo( this->CreateType((const COR_SIGNATURE*)(&da.addr.addr.addrRetVal.rgSig),
                                               da.addr.addr.addrRetVal.dwSigSize,
                                               da.GetModule(),
                                               mdMethodDefNil,
                                               pGenScope,
                                               ppField) );
                }
                else
                {
                    IfFailGo( this->CreateClassType(da.GetModule(), da.tokClass, ppField) );
                }

                break;
            }

        default:
            {
                ASSERT(!"Address type not supported.");
            }
    }

Error:

    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromPrimitive, hr );

    RELEASE( pGenScope );

    return hr;
}
```

## <a name="see-also"></a>Siehe auch
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
