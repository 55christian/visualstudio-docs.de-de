---
title: REFERENCE_COMPARE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_COMPARE
helpviewer_keywords:
- REFERENCE_COMPARE enumeration
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d166917ec9770e3f8d1f41f3774676278b894724
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322344"
---
# <a name="referencecompare"></a>REFERENCE_COMPARE
Gibt den Typ von Vergleich für Verweise.

## <a name="syntax"></a>Syntax

```cpp
enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
typedef DWORD REFERENCE_COMPARE;
```

```csharp
public enum enum_REFERENCE_COMPARE { 
   REF_COMPARE_EQUAL        = 0x0001,
   REF_COMPARE_LESS_THAN    = 0x0002,
   REF_COMPARE_GREATER_THAN = 0x0003
};
```

## <a name="fields"></a>Felder
 `REF_COMPARE_EQUAL`\
 Gibt einen-gleich-Vergleich an.

 `REF_COMPARE_LESS_THAN`\
 Gibt an, eine kleiner-als-Vergleich.

 `REF_COMPARE_GREATER_THAN`\
 Gibt an, ein größer-als-Vergleich.

## <a name="remarks"></a>Hinweise
 Übergeben als Argument an die [vergleichen](../../../extensibility/debugger/reference/idebugreference2-compare.md) Methode.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugreference2-compare.md)