---
title: PROVIDER_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f6fb974bd5affc89eeacbfccace5c1e89218db5
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457926"
---
# <a name="providerflags"></a>PROVIDER_FLAGS
Gibt die gewünschte Eigenschaften von einem Programm-Anbieter abgerufen werden sollen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
typedef DWORD PROVIDER_FLAGS;
```

```csharp
public enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
```

## <a name="fields"></a>Felder
 `PFLAG_NONE`\
 Keine Flags angegeben.

 `PFLAG_REMOTE_PORT`\
 Eine Liste der Programme auf einem anderen Computer als "Aufrufer" [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 `PFLAG_DEBUGGEE`\
 Der Prozess wird von dieser Instanz der gerade gedebuggten [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 `PFLAG_ATTACH_TODEBUGGEE`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] das derzeit debuggte Programm angefügt ist, jedoch wurde nicht gestartet.

 `PFLAG_REASON_WATCH`\
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] wird für Ereignisse überwachen.

 `PFLAG_GET_PROGRAM_NODES`\
 Aufrufer möchte, dass die `ProgramNodes` Feld der [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Struktur.

 `PFLAG_GET_IS_DEBUGGER_PRESENT`\
 Aufrufer möchte, dass die `fIsTheDebuggerPresent` Feld der `PROVIDER_PROCESS_DATA` Struktur.

## <a name="remarks"></a>Hinweise
 Diese Flags werden an die folgenden Methoden übergeben:

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  Diese Werte können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)