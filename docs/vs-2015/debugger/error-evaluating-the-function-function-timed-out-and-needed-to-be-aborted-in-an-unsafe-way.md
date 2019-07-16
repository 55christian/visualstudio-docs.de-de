---
title: 'Fehler: Auswerten der Funktion &#39;Funktion&#39; Timeout und musste auf unsichere Weise abgebrochen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d5a992751e31f21a7875091b4c8b1be9bd0bd0a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197061"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Fehler: Auswerten der Funktion &#39;Funktion&#39; Timeout und musste auf unsichere Weise abgebrochen werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vollständige Nachrichtentext: Auswerten der Funktion 'Funktion' Timeout und musste auf unsichere Weise abgebrochen werden. Dies kann den Zielprozess beschädigt. 

Zum Überprüfen des Status von Objekten für .NET zu vereinfachen, wird der Debugger automatisch den gedebuggten Prozess zum Ausführen von zusätzlichen Codes (in der Regel die Eigenschaft Getter-Methoden und Funktionen mit ToString) erzwungen. In den meisten Szenarien alle diese Funktionen schnell ausführen und Debuggen deutlich vereinfacht. Der Debugger nicht jedoch die Anwendung in einer Sandbox ausgeführt wird. Daher kann eine Abruf- oder die ToString-Methode, die eine native Funktion aufruft, das hängt zu lange Timeouts führen, die nicht wiederhergestellt werden kann. Wenn Sie diese Fehlermeldung auftritt, ist dies aufgetreten.
 
Ein häufiger Grund für dieses Problem ist, dass wenn der Debugger eine Eigenschaft ausgewertet wird, nur den Thread wird überprüft, um Sie ausführen können. Also wird ob die Eigenschaft in der debuggten Anwendung Ausführung anderer Threads warten ist und wenn es auf eine Weise, die die .NET Runtime unterbrechen, können nicht im Wartezustand befindet, dieses Problem auftreten.
 
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler
 
Es gibt drei mögliche Lösungen für dieses Problem.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>#1-Lösung: Verhindern Sie, dass des Debuggers beim Aufrufen der Getter-Eigenschaft oder die ToString-Methode
 
Die Fehlermeldung informiert Sie den Namen der Funktion, die der Debugger versucht hat, aufgerufen. Wenn Sie diese Funktion ändern können, können Sie verhindern, dass den Debugger die Getter für eine Eigenschaft oder die ToString-Methode aufrufen. Versuchen Sie Folgendes:
 
* Ändern Sie die Methode in eine andere Art von Code als einen Eigenschaften-Getter oder ToString-Methode und das Problem werden verschwinden.
    -oder-
* (Für ToString) Einem DebuggerDisplay-Attribut für den Typ definieren und Sie können den Debugger, einen anderen Wert als ToString ausgewertet.
    -oder-
* (Für einen Eigenschaften-Getter) Platzieren der `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` Attribut für die Eigenschaft. Dies ist hilfreich, wenn Sie eine Methode verwenden, die eine Eigenschaft aus Gründen der Kompatibilität von API-bleiben muss, aber es sollte eigentlich eine Methode sein.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Lösung #2: Haben Sie den Code des ereignisdateiziels, bitten Sie den Debugger an die Auswertung Abbrechen
 
Die Fehlermeldung informiert Sie den Namen der Funktion, die der Debugger versucht hat, aufgerufen. Wenn der Eigenschaftengetter oder eine ToString-Methode in einigen Fällen nicht ordnungsgemäß ausgeführt werden, insbesondere in Situationen, in denen das Problem, das Code einem anderen Thread zum Ausführen von Code benötigt, und die implementierungsfunktion aufrufen kann `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` , bitten Sie den Debugger an die Funktion abgebrochen nützlich. Mit dieser Lösung ist es weiterhin möglich, diese Funktionen bewerten, aber das Standardverhalten ist, dass die Ausführung hält bei der NotifyOfCrossThreadDependency des Anrufs gewählt.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>#3-Lösung: Deaktivieren Sie alle implizite Auswertung
 
Wenn die vorherigen Lösungen das Problem nicht beheben, wechseln Sie zu *Tools* / *Optionen*, und deaktivieren Sie die Einstellung *Debuggen*  /   *Allgemeine* / *eigenschaftenauswertung und andere implizite Funktionsaufrufe*. Dadurch werden die meisten Evaluierungsversionen von impliziten Funktionen deaktiviert und sollte das Problem zu beheben.
