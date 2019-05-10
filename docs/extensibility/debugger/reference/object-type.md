---
title: OBJECT_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08d50e3d3ddda55a7ff0f3fea333c5408b02878a
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461034"
---
# <a name="objecttype"></a>OBJECT_TYPE
Gibt den Typ eines Objekts von der ausdrucksauswertung.

## <a name="syntax"></a>Syntax

```cpp
enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
typedef DWORD OBJECT_TYPE;
```

```csharp
public enum enum_OBJECT_TYPE { 
   OBJECT_TYPE_BOOLEAN = 0x0,
   OBJECT_TYPE_CHAR    = 0x1,
   OBJECT_TYPE_I1      = 0x2,
   OBJECT_TYPE_U1      = 0x3,
   OBJECT_TYPE_I2      = 0x4,
   OBJECT_TYPE_U2      = 0x5,
   OBJECT_TYPE_I4      = 0x6,
   OBJECT_TYPE_U4      = 0x7,
   OBJECT_TYPE_I8      = 0x8,
   OBJECT_TYPE_U8      = 0x9,
   OBJECT_TYPE_R4      = 0xa,
   OBJECT_TYPE_R8      = 0xb,
   OBJECT_TYPE_OBJECT  = 0xc,
   OBJECT_TYPE_NULL    = 0xd,
   OBJECT_TYPE_CLASS   = 0xe
};
```

## <a name="fields"></a>Felder
 `OBJECT_TYPE_BOOLEAN`\
 Gibt an, dass das Objekt ein boolescher Wert.

 `OBJECT_TYPE_CHAR`\
 Gibt an, dass das Objekt ein Zeichen ist.

 `OBJECT_TYPE_I1`\
 Gibt an, dass das Objekt eine ein-Byte-Ganzzahl mit Vorzeichen ist.

 `OBJECT_TYPE_U1`\
 Gibt an, dass das Objekt eine ein-Byte-Ganzzahl ohne Vorzeichen ist.

 `OBJECT_TYPE_I2`\
 Gibt an, dass das Objekt eine 2-Byte-Ganzzahl mit Vorzeichen ist.

 `OBJECT_TYPE_U2`\
 Gibt an, dass das Objekt eine 2-Byte-Ganzzahl ohne Vorzeichen ist.

 `OBJECT_TYPE_I4`\
 Gibt an, dass das Objekt eine vier-Byte-Ganzzahl mit Vorzeichen ist.

 `OBJECT_TYPE_U4`\
 Gibt an, dass das Objekt eine vier-Byte-Ganzzahl ohne Vorzeichen ist.

 `OBJECT_TYPE_I8`\
 Gibt an, dass das Objekt eine 8-Byte-Ganzzahl mit Vorzeichen ist.

 `OBJECT_TYPE_U8`\
 Gibt an, dass das Objekt eine 8-Byte-Ganzzahl ohne Vorzeichen ist.

 `OBJECT_TYPE_R4`\
 Gibt an, dass das Objekt eine vier-Byte-Gleitkommazahl.

 `OBJECT_TYPE_R8`\
 Gibt an, dass das Objekt eine 8-Byte-Gleitkommazahl.

 `OBJECT_TYPE_OBJECT`\
 Gibt an, dass das Objekt ein Objekt.

 `OBJECT_TYPE_NULL`\
 Gibt an, dass das Objekt NULL ist.

 `OBJECT_TYPE_CLASS`\
 Gibt an, dass das Objekt einer Klasse ist.

## <a name="remarks"></a>Hinweise
 Übergeben als Argument an die [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) und [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) Methoden.

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)
- [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)