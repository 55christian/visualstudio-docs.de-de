---
title: DEBUG_ADDRESS_UNION | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fddd1fdc0aef74f637c058cd440f6e8309fe3432
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615297"
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
Beschreibt die verschiedene Arten von Adressen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Member
`dwKind`\
Ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Enumeration, der die Union zu interpretieren.

`addr.addrNative`\
[C++ nur] Enthält die [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Struktur, wenn `dwKind` ADDRESS_KIND_NATIVE =.

`addr.addrThisRel`\
[C++ nur] Enthält die[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Struktur, wenn `dwKind` ADDRESS_KIND_UNMANAGED_THIS_RELATIVE =.

`addr.addUPhysical`\
[C++ nur] Enthält die[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Struktur, wenn `dwKind` ADDRESS_KIND_UNMANAGED_PHYSICAL =.

`addr.addrMethod`\
[C++ nur] Enthält die[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Struktur, wenn `dwKind` ADDRESS_KIND_METHOD =.

`addr.addrField`\
[C++ nur] Enthält die[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Struktur, wenn `dwKind` ADDRESS_KIND_FIELD =.

`addr.addrLocal`\
[C++ nur] Enthält die[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Struktur, wenn `dwKind` ADDRESS_KIND_LOCAL =.

`addr.addrParam`\
[C++ nur] Enthält die[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Struktur, wenn `dwKind` ADDRESS_KIND_PARAM =.

`addr.addrArrayElem`\
[C++ nur] Enthält die[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Struktur, wenn `dwKind` ADDRESS_KIND_ARRAYELEM =.

`addr.addrRetVal`\
[C++ nur] Enthält die[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Struktur, wenn `dwKind` ADDRESS_KIND_RETVAL =.

`addr.unused`\
[C++ nur] auffüllen.

`addr`\
[C++ nur] Der Name der Union.

`unionmember`\
[C# nur] Dieser Wert muss auf den entsprechenden Strukturtyp basierend auf gemarshallt werden `dwKind`. Finden Sie unter "Hinweise" für die Zuordnung zwischen `dwKind` und Interpretation der Union.

## <a name="remarks"></a>Hinweise
Diese Struktur ist Teil der [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) strukturieren und stellt eine Anzahl verschiedener Arten von Adressen (der `DEBUG_ADDRESS` Struktur wird ausgefüllt, durch einen Aufruf der [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) Methode).

 [C# nur] Die folgende Tabelle zeigt die Interpretation der `unionmember` Member für jede Art von Adresse. Im Beispiel wird gezeigt, wie dies für eine bestimmte Art von Adresse erfolgt.

|`dwKind`|`unionmember` interpretiert als|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie eine Art Adresse interpretiert (`METADATA_ADDRESS_ARRAYELEM`) von der `DEBUG_ADDRESS_UNION` Struktur in C# geschrieben. Die übrigen Elemente können auf genau die gleiche Weise interpretiert werden.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Anforderungen
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
