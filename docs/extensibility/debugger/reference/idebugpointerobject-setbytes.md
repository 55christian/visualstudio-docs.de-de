---
title: IDebugPointerObject::SetBytes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b574e28ac0b42f065bfbf056188c655797e542b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209343"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Legt den Wert aus einer Reihe von aufeinander folgenden Bytes gezeigt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parameter
`dwStart`\
[in] Ein Offset in Bytes vom Beginn des Objekts auf den verwiesen wird.

`dwCount`\
[in] Die Anzahl der Bytes, die festgelegt werden soll.

`pBytes`\
[in] Ein Array von Bytes, die den neuen Wert darstellt. Dieser Wert wird in das Objekt, beginnend am angegebenen Offset gespeichert.

`pdwBytes`\
[out] Gibt zurück, der die Anzahl der Bytes tatsächlich festgelegt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird verwendet, wenn der Zeiger, dargestellt durch diese [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) verweist auf einen primitiven Typ oder einem einfachen Array primitiver Typen (d. h. ein Array, das durch eine einfache Folge von Bytes dargestellt werden können). Dies `IDebugPointerObject` Objekt handelt es sich nicht um einen null-Verweis (es muss auf eine Adresse im Speicher).

## <a name="see-also"></a>Siehe auch
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)