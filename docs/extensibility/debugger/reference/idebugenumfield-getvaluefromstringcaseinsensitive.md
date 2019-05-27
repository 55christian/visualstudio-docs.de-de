---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 163e675d0ef4b47e0a0bf82d730adcc081eddec3
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200095"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Diese Methode verwendet einen Groß-und Kleinschreibung gesucht, um den Wert mit dem Namen einer Enumerationskonstante zurückzugeben.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parameter
`pszValue`\
[in] Eine Zeichenfolge, die den Namen für die zum Abrufen des Werts angeben. Beachten Sie, dass für C++, dies ist eine Breitzeichen-Zeichenfolge.

`pValue`\
[out] Gibt den zugeordneten numerischen Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE`, wenn der Name nicht Teil der Enumeration oder ein Fehlercode.

## <a name="remarks"></a>Hinweise
 Diese Methode ist die Groß-/Kleinschreibung. Wenn die Groß-/ Kleinschreibung (z. B. in einer Sprache wie C++, in denen Groß-und Kleinschreibung) erforderlich ist, verwenden Sie [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Siehe auch
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)