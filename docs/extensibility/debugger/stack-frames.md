---
title: Stapelrahmen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 125acbbca2723a9fbd9f41932782a62e966bcdd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864313"
---
# <a name="stack-frames"></a>Stapelrahmen
Architektur der Debugger eine *Stapelrahmen*:

- Ist eine Abstraktion eines Stapels, der den Ausführungskontext eines Threads bereitstellt. Ein Thread wird immer innerhalb einer Funktion ausgeführt. Ein Stapelrahmen werden die lokalen Variablen der Funktion und die Argumente, enthält. Um mit Visual Studio zu debuggen, muss die Sprache oder Umgebung, die im Debugmodus befindlichen Stapelrahmen unterstützen.

- Kann sowohl zu identifizieren und selbst beschreiben und können den zugeordneten Thread zurück. Ein Stapelrahmen kann der Codekontext, der den aktuellen Anweisungszeiger und die zugehörige Dokumentation darstellt und ausdruckskontexten-Auswertung zurückgegeben werden.

- Verfügt über Eigenschaften, die den Namen, Typ und Wert der lokalen Variablen und Argumente, die beschreiben, und die in verschiedene IDE-Debug-Fenster angezeigt werden.

- Wird durch dargestellt eine [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle, die in der Regel von einem Debug-Engine (DE) oder den virtuellen Computer als Folge eines Threads erstellt.

## <a name="see-also"></a>Siehe auch
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [Debug-engine](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)