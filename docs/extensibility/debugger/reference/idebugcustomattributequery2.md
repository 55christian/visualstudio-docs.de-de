---
title: IDebugCustomAttributeQuery2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00220574ac9c16bdab9abd64adde1877ee0fd9f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335808"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Bestimmt, ob ein benutzerdefiniertes Attribut für dieses Feld vorhanden ist und, sofern vorhanden, gibt die Attributinformationen.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein symbolanbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) um benutzerdefinierte Attribute zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwendung [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der **IDebugCustomAttributeQuery** Schnittstelle.

|Methode|Beschreibung|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Bestimmt, ob ein benutzerdefiniertes Attribut nach Namen vorhanden ist.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ruft die Attributinformationen für den angegebenen benutzerdefinierten Attributs ab.|

 Zusätzlich zu den **IDebugCustomAttributeQuery** Methoden `IDebugCustomAttributeQuery2` implementiert die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ruft einen Enumerator für alle benutzerdefinierten Attribute, die an dieses Feld angefügt.|

## <a name="remarks"></a>Hinweise
 Die [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) Methode kann einen Enumerator für alle benutzerdefinierten Attribute für dieses Feld definierten zurückgeben.

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)