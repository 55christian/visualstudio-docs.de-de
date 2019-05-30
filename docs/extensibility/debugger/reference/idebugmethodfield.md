---
title: IDebugMethodField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a4b8557226ad010968772562aa787472f159900
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324104"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Diese Schnittstelle wird eine Methode beschrieben.

## <a name="syntax"></a>Syntax

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein symbolanbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstelle. Diese Schnittstelle ist eine Spezialisierung, die eine Methode darstellt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwendung [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen der [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstelle, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) gibt `FIELD_TYPE_METHOD`. Darüber hinaus die Methoden [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), und [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), geben die `IDebugMethodField` Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden für die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) und [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstellen, die diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Erstellt einen Enumerator für die Parameter der Methode.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Ruft ab, der "this"-Zeiger des Objekts, die die Methode enthält.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Erstellt einen Enumerator für alle lokalen Variablen der Methode.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Erstellt einen Enumerator für die ausgewählten lokalen Variablen der Methode.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Erstellt einen Enumerator für statische lokale Variablen der Methode.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Ruft den globalen Container die Methode ab.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Erstellt einen Enumerator für den Typ jedes Arguments erforderlich, um die Methode aufrufen.|

## <a name="remarks"></a>Hinweise
 Eine Methode kann es sich um Parameter als auch für lokale Variablen enthalten.

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)