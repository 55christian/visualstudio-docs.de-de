---
title: IDebugFunctionObject::CreateObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc0632f429a547d4b17fe57bec4582fea623ee24
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320945"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Erstellt ein Objekt, das über einen Konstruktor.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>Parameter
`pConstructor`\
[in] Ein [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Objekt, das den Konstruktor des zu erstellenden-Objekts darstellt.

`dwArgs`\
[in] Die Anzahl von Parametern in der `pArg` Array. Gibt die Anzahl von Parametern, die an den Konstruktor übergeben.

`pArg`\
[in] Ein Array von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte, die Parameter darstellen, die an den Konstruktor übergeben wird.

`ppObject`\
[out] Gibt eine `IDebugObject` , das das neu erstellte Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Rufen Sie diese Methode, um ein Objekt zu erstellen, die eine Instanz einer Klasse (oder anderen komplexen Typs, der einen Konstruktor ist erforderlich) darstellt, einen Parameter an die Funktion die entspricht der [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.

 Wenn Sie einen Konstruktor mit der Objektparameter nicht erforderlich ist, rufen Sie die [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)