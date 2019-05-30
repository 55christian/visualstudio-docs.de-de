---
title: DEBUG_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0502ab10398d37bcafee5316ba7e7566dbab4e01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346165"
---
# <a name="debugreason"></a>DEBUG_REASON
Gibt an, warum der Prozess zum Debuggen gestartet wurde.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Felder
`DEBUG_REASON_ERROR`\
Ein nicht-spezifischer Fehler aufgetreten ist (Dies wird verwendet, als eine standardbedingung Wenn keine der anderen Lösung Gründe).

`DEBUG_REASON_USER_LAUNCHED`\
Der Prozess wurde auf Anforderung des Benutzers gestartet.

`DEBUG_REASON_USER_ATTACHED`\
Der bereits ausgeführten Prozess wurde vom Benutzer zugeordnet.

`DEBUG_REASON_AUTO_ATTACHED`\
Der Prozess wurde mit automatisch verbunden, wenn sie gestartet wurde.

`DEBUG_REASON_CAUSALITY`\
Der Prozess wurde gestartet, aufgrund einer *Just-In-Time-* Debuggen (JIT)-Ereignis.

## <a name="remarks"></a>Hinweise
Zurückgegeben von der [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
