---
title: PROCESS_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a3418aaa9c2e14454d71d26c0e364ae04244127
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457973"
---
# <a name="processinfo"></a>PROCESS_INFO
Enthält Informationen zu einem Prozess an.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Member
 `Fields`\
 Eine Kombination von Flags aus der [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) -Enumeration, die angeben, welche Felder ausgefüllt sind.

 `bstrFileName`\
 Der vollständige Name des Prozesses. Entspricht dem Aufrufen der [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) Methode mit dem Parameter `GN_FILENAME`.

 `bstrBaseName`\
 Der Dateiname und Erweiterung des Prozesses. Entspricht dem Aufrufen der `IDebugProcess2::Getname` Methode mit dem Parameter `GN_BASENAME`.

 `bstrTitle`\
 Der Titel des Prozesses aus, falls vorhanden. Entspricht dem Aufrufen der `IDebugProcess2::Getname` Methode mit dem Parameter `GN_TITLE`.

 `ProcessId`\
 Die [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die den Prozess bezeichnet. Entspricht dem Aufrufen der [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md) Methode.

 `dwSessionId`\
 Der Bezeichner der Debugsitzung, die diesen Prozess ausgeführt wird.

 `bstrAttachedSessionName`\
 Der Sitzungsname des angefügten. Entspricht dem Aufrufen der [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) Methode.

 `CreationTime`\
 Der Zeitpunkt, an der Prozess erstellt wurde.

 `Flags`\
 Eine Kombination von Flags aus der [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) -Enumeration, die Eigenschaften des Prozesses angeben.

## <a name="remarks"></a>Hinweise
 Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) Methode, in denen es ausgefüllt wird.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)