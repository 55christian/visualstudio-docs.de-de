---
title: IDebugComPlusSymbolProvider2::GetTypeFromToken | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::GetTypeFromToken
- GetTypeFromToken
ms.assetid: 4452bc5d-0225-40e0-a467-c472a5c7c4ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5212fe733e3590a7b15b5ade55d2bfd2aa4048dc
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "66326152"
---
# <a name="idebugcomplussymbolprovider2gettypefromtoken"></a>IDebugComPlusSymbolProvider2::GetTypeFromToken
Ruft einen Typ, dessen Token erhält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypeFromToken(
    ULONG32       appDomain,
    GUID          guidModule,
    DWORD         tdToken,
    IDebugField** ppField
);
```

```csharp
int GetTypeFromToken(
    uint            appDomain,
    Guid            guidModule,
    uint            tdToken,
    out IDebugField ppField
);
```

## <a name="parameters"></a>Parameter
`appDomain`\
[in] Der Bezeichner der Anwendungsdomäne.

`guidModule`\
[in] Eindeutiger Bezeichner des Moduls.

`tdToken`\
[in] Token des Typs abgerufen werden sollen.

`ppField`\
[out] Gibt den Typ zurück, die durch dargestellt ist die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) Schnittstelle.

```cpp
HRESULT CDebugSymbolProvider::GetTypeFromToken(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    DWORD tdToken,
    IDebugField **ppField)
{
    HRESULT hr = E_FAIL;

    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetTypeFromToken );

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidWritePtr(ppField, IDebugField*));

    Module_ID idModule(ulAppDomainID, guidModule);

    IfFailGo( this->CreateClassType(idModule, tdToken, ppField) );

Error:

    METHOD_EXIT( CDebugDynamicFieldSymbol::GetTypeFromToken, hr );

    return hr;
}
```

## <a name="see-also"></a>Siehe auch
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
