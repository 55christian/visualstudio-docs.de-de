---
title: IDebugProgramNode2::GetHostPid | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostPid
helpviewer_keywords:
- IDebugProgramNode2::GetHostPid
ms.assetid: e65b4b15-46d8-4ca7-9456-2b4c078f7cf9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03ac1d4f979c6b6ce504160216d42f055820d69c
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457809"
---
# <a name="idebugprogramnode2gethostpid"></a>IDebugProgramNode2::GetHostPid
Ruft die System-Prozess-ID für den Prozess, der die Anwendung hosten.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostPid ( 
   AD_PROCESS_ID * pdwHostPid
);
```

```csharp
int GetHostPid ( 
   out AD_PROCESS_ID pdwHostPid
);
```

## <a name="parameters"></a>Parameter
 `pdwHostPid`\

 [out] Gibt zurück, die System-Prozess-ID für den Hostprozess.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CProgram` Objekt, das implementiert die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle.

```cpp
HRESULT CProgram::GetHostPid(AD_PROCESS_ID* pdwHostPid) {
   // Check for valid argument.
   if (pdwHostPid == NULL)
     return E_INVALIDARG;

   // Get the process identifier of the calling process.
   pdwHostPid->ProcessIdType = AD_PROCESS_ID_SYSTEM;
   pdwHostPid->ProcessId.dwProcessId = GetCurrentProcessId();
   return S_OK;
}
```

## <a name="see-also"></a>Siehe auch
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
