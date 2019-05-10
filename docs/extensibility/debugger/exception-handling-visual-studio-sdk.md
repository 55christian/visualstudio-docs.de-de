---
title: Ausnahmebehandlung (Visual Studio SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f48724ac57e23fc569bd244afdb3a205ed9c4ef7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889878"
---
# <a name="exception-handling-visual-studio-sdk"></a>Ausnahmebehandlung (Visual Studio SDK)
Im folgenden wird beschrieben, den Prozess, der auftritt, wenn Ausnahmen ausgelöst werden.

## <a name="exception-handling-process"></a>Ausnahme Behandlungsvorgangs

1. Zuerst wird eine Ausnahme ausgelöst, aber bevor sie vom Ausnahmehandler in der Anwendung im Debugmodus befindlichen behandelt wird, die Debug-Engine (DE sendet) eine [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) für die Sitzung-Debug-Manager (SDM) als eine Beenden-Ereignis. Die `IDebugExceptionEvent2` wird gesendet, wenn nur die Einstellungen für die Ausnahme (angegeben in das Dialogfeld "Ausnahmen" in das debugpaket) angeben, dass der Benutzer auf Benachrichtigungen über Ausnahmefehler der ersten Chance beenden möchte.

2. Die SDM-Aufrufe [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) -Eigenschaft der Ausnahme abgerufen.

3. Ruft die Debug-Paket [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) um zu bestimmen, welche Optionen Sie dem Benutzer.

4. Das debugpaket fordert den Benutzer, wie Sie die Ausnahme zu behandeln, durch Öffnen eines Dialogfelds Ausnahmefehler der ersten Chance.

5. Wenn der Benutzer auswählt, um den Vorgang fortzusetzen, das SDM ruft [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Wenn die Methode S_OK zurückgibt, ruft [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         - oder - 

         Wenn die Methode gibt S_FALSE zurück, das Programm zurück, im Debugmodus befindlichen erhält eine zweite Chance, die die Ausnahme zu behandeln.

6. Verfügt das derzeit debuggte Programm kein Handler für eine zweite Chance-Ausnahme, die DE sendet eine `IDebugExceptionEvent2` , das SDM als **EVENT_SYNC_STOP**.

7. Das debugpaket fordert den Benutzer, wie Sie die Ausnahme zu behandeln, durch Öffnen eines Dialogfelds Ausnahmefehler der ersten Chance.

8. Ruft die Debug-Paket [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) um zu bestimmen, welche Optionen Sie dem Benutzer.

9. Das debugpaket fordert den Benutzer, wie Sie die Ausnahme zu behandeln, indem Sie eine zweite Chance Ausnahme-Dialogfeld zu öffnen.

10. Wenn die Methode S_OK zurückgibt, ruft `IDebugExceptionEvent2::PassToDebuggee`.

## <a name="see-also"></a>Siehe auch
- [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)