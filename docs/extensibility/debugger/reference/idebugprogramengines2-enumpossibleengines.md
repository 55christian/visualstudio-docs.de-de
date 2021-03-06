---
title: IDebugProgramEngines2::EnumPossibleEngines | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
helpviewer_keywords:
- IDebugProgramEngines2::EnumPossibleEngines
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 532486c66b6feb5c397b9167e2b1cd6197513fa8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343397"
---
# <a name="idebugprogramengines2enumpossibleengines"></a>IDebugProgramEngines2::EnumPossibleEngines
Gibt zurück, die GUIDs für alle der möglichen Debug-Engines (DE), die das Programm debuggen können.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumPossibleEngines( 
   DWORD  celtBuffer,
   GUID*  rgguidEngines,
   DWORD* pceltEngines
);
```

```csharp
int EnumPossibleEngines( 
   uint      celtBuffer,
   GUID[]    rgguidEngines,
   ref DWORD pceltEngines
);
```

## <a name="parameters"></a>Parameter
`celtBuffer`\
[in] Die Anzahl der DE-GUIDs, die zurückgegeben werden soll. Hiermit wird die maximale Größe der auch die `rgguidEngines` Array.

`rgguidEngines`\
[in, out] Ein Array von DE-GUIDs gefüllt werden soll.

`pceltEngines`\
[out] Gibt die tatsächliche Anzahl von DE-GUIDs, die zurückgegeben werden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt [C++] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` oder [C#] 0x8007007A, wenn der Puffer nicht groß genug ist.

## <a name="remarks"></a>Hinweise
 Um zu bestimmen, wie viele Module vorhanden sind, rufen diese Methode einmal mit der `celtBuffer` -Parameter auf 0 festgelegt und die `rgguidEngines` -Parameter auf einen null-Wert festgelegt. Dies gibt `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` (0x8007007A für C#-Code), und die `pceltEngines` Parameter gibt die erforderliche Größe des Puffers zurück.

## <a name="see-also"></a>Siehe auch
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)