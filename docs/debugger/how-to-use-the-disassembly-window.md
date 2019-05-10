---
title: Anzeigen der Disassembly-Code im Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 10/30/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43214ee122b3aa5c3907b9176631f2dc22c9178e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846389"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Anzeigen der Disassembly-Code in Visual Studio-Debugger (C#, C++, Visual Basic F#)

Im Fenster **Disassemblierung** wird der Assemblycode angezeigt, der den vom Compiler erstellten Anweisungen entspricht. Wenn Sie verwalteten Code Debuggen, entsprechen diese Assemblyanweisungen durch den Just-in-Time (JIT)-Compiler, nicht die Microsoft intermediate Language (MSIL) erstellt, die von der Visual Studio-Compiler erstellten nativen Code.

> [!NOTE]
> Zum Nutzen der **Disassembly** Fenster verstehen oder die Grundlagen der [Programmieren](https://wikipedia.org/wiki/Assembly_language).

Dieses Feature ist nur verfügbar, wenn Debuggen auf Adressebene aktiviert ist. Es ist nicht für Skriptsprachen oder SQL-debugging verfügbar.

Neben den Assemblyanweisungen können folgende optionale Informationen im Fenster **Disassemblierung** angezeigt werden:

- Speicheradresse, an der sich die einzelnen Anweisungen befinden. Für native Anwendungen ist es die eigentliche Speicheradresse. Für Visual Basic oder C#, Offset vom Anfang der Funktion ist.

- Quellcode, aus dem der Assemblercode abgeleitet wird.

- Codebytes, d. h. die bytedarstellungen der tatsächlichen Computer- oder MSIL-Anweisungen.

- Symbolnamen für die Speicheradressen.

- Mit dem Quellcode übereinstimmende Zeilennummern.

Assemblysprachanweisungen bestehen aus *mnemonischen Code des*, Hierbei handelt es sich um Abkürzungen für Anweisungsnamen, und *Symbole* für Variablen, Register und Konstanten. Jede Anweisung in Computercode wird durch eine Assemblysprache Mnemonik, optional gefolgt von einer oder mehrerer Symbole dargestellt.

Assemblycode basiert stark auf Prozessor registriert, oder für verwalteten Code, der common Language Runtime registriert. Können Sie die **Disassembly** Fenster zusammen mit den **registriert** Fenster, in dem Sie dort den Registerinhalt untersuchen kann.

Um Computercode Anweisungen in ihre numerische Rohdaten und nicht als Assembly Sprache anzuzeigen, verwenden die **Arbeitsspeicher** Fenster, oder wählen **Codebytes** aus dem Kontextmenü in der **Disassembly**  Fenster.

## <a name="use-the-disassembly-window"></a>Verwenden des Disassembierungsfensters

So aktivieren Sie die **Disassembly** Fenster unter **Tools** > **Optionen** (oder **Tools**  >  **Optionen**) > **Debuggen**Option **Debuggen auf Adressebene aktivieren**.

Zum Öffnen der **Disassembly** Fenster während des Debuggens wählen **Windows** > **Disassembly** , oder drücken Sie **Alt** + **8**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

Um die optionalen Informationen zu aktivieren oder deaktivieren, mit der Maustaste in die **Disassembly** Fenster, und aktivieren bzw. deaktivieren Sie die gewünschten Optionen im Kontextmenü die Option.

Ein gelber Pfeil am linken Rand kennzeichnet den aktuellen Ausführungspunkt an. Für nativen Code entspricht der Ausführungspunkt Programmzähler der CPU. Diese Position zeigt die nächste Anweisung an, die im Programm ausgeführt wird.

## <a name="see-also"></a>Siehe auch

* [Paging up or down in memory (Vertikales Paging im Arbeitsspeicher)](../debugger/how-to-page-up-or-down-in-memory.md)
* [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
* [Vorgehensweise: Verwenden des Fensters „Register“](../debugger/how-to-use-the-registers-window.md)