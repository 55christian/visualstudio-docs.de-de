---
title: Haltepunktfehler | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a539894b0564d8c89461886558eb35c04c8af83c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890709"
---
# <a name="breakpoint-errors"></a>Haltepunktfehler
Die folgenden beschreibt den Prozess aus, wenn ein Haltepunkt zum Binden an Code versucht jedoch ein Fehler auftritt.

## <a name="troubleshoot-a-breakpoint-error"></a>Problembehandlung bei der ein haltepunktfehler

1. Die Debug-Engine (DE) sendet ein [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) für die Sitzung Debug-Manager (SDM).

2. Die SDM-Aufrufe [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) um den Haltepunkt Fehler zu erhalten.

3. Die SDM-Aufrufe [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) abzurufenden den ausstehenden Haltepunkt, von dem der Haltepunkt Fehler verursacht wurde.

4. Die SDM-Aufrufe [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) abzurufenden den Grund, warum der Haltepunkt Fehler beim Binden Fehler.

## <a name="see-also"></a>Siehe auch
- [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)