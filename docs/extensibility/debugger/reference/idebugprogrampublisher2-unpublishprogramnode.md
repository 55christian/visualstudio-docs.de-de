---
title: IDebugProgramPublisher2::UnpublishProgramNode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00c78b4390d519cb8b37d0af17e1e61a8127d080
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458923"
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
Entfernt einen angegebenes Programm Knoten aus Verfügbarkeit für die debug-Engines (DEs) und sitzungsbasierter Debug-Manager (SDM).

## <a name="syntax"></a>Syntax

```cpp
HRESULT UnpublishProgramNode(
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int UnpublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parameter
 `pProgramNode`\

 [in] Ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt, das diesem Programm Knoten darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Nachdem es entfernt wurde, ist der Programm-Knoten nicht mehr verfügbar, Programm Informationen abgefragt werden.

 Um ein Programm-Knoten verfügbar zu machen, rufen Sie die [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)