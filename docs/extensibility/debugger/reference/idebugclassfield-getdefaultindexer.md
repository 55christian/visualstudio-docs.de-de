---
title: IDebugClassField::GetDefaultIndexer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 95387f65382c970ec2e9847e95ff49e139cf69b8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350751"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Ruft den Namen der Standardindexer ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>Parameter
`pbstrIndexer` [out] Gibt eine Zeichenfolge, die mit dem Namen des der Standardindexer zurück.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, oder gibt S_FALSE zurück, wenn kein Standardindexer vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Standardindexer einer Klasse ist die Eigenschaft mit der Kennzeichnung der `Default` -Eigenschaft für Arrays zugreift. Dies bezieht sich auf [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]. Hier ist ein Beispiel für einen Standardindexer deklariert [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] und wie diese verwendet werden.

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>Siehe auch
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)