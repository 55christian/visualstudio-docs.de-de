---
title: Debuggen mit Visual Studio für Mac
description: Das Debuggen ist ein üblicher und notwendiger Teil des Programmierens. Da Visual Studio für Mac eine ausgereifte IDE ist, enthält es eine Reihe von Features, die das Debuggen vereinfachen. Dieser Artikel erläutert vom sicheren Debuggen bis hin zur Datenvisualisierung, wie das volle Potenzial des Debuggens in Visual Studio für Mac genutzt werden kann.
author: therealjohn
ms.author: johmil
ms.date: 12/13/2019
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: 8a12880c25e980d668351ef4c24ced1e479577d4
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/25/2019
ms.locfileid: "75397936"
---
# <a name="debugging-with-visual-studio-for-mac"></a>Debuggen mit Visual Studio für Mac

Visual Studio für Mac verfügt über Debugger mit Unterstützung für .NET Core-, .NET Framework-, Unity- und Xamarin-Anwendungen.

Visual Studio für Mac verwendet den [*Soft-Debugger von Mono*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), der in die Mono-Laufzeit integriert wird und es Visual Studio für Mac ermöglicht, verwalteten Code für alle Plattformen zu debuggen.

## <a name="the-debugger"></a>Der Debugger

Visual Studio für Mac verwendet den Soft-Debugger von Mono, um verwalteten Code (C# oder F#) für alle Xamarin-Anwendungen zu debuggen. Der Soft-Debugger von Mono unterscheidet sich insofern von gewöhnlichen Debuggern, dass es sich um einen kooperativen und in die Mono-Laufzeit integrierten Debugger handelt. Der generierte Code und die Mono-Laufzeit kooperieren mit der IDE, um für ein benutzerfreundliches Debuggen zu sorgen. Die Mono-Laufzeit stellt die Debugfunktion über ein Versandprotokoll zur Verfügung. Weitere Informationen dazu finden Sie [in der Mono-Dokumentation](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Hard-Debugger, zum Beispiel [LLDB]( http://lldb.llvm.org/index.html) oder [GDB]( https://www.gnu.org/software/gdb/), steuern ein Programm ohne das Wissen oder die Kooperation des gedebuggten Programms. Diese können aber dennoch beim Debuggen von Xamarin-Anwendungen hilfreich sein, falls Sie nativen iOS- oder Android-Code debuggen müssen.

Für .NET Core und ASP.NET Core-Anwendungen verwendet Visual Studio für Mac den .NET Core-Debugger. Dieser Debugger ist ebenfalls ein kooperativer Debugger und arbeitet mit der .NET-Runtime.

## <a name="using-the-debugger"></a>Verwenden des Debuggers

Versichern Sie sich, dass die Konfiguration auf **Debug** (Debuggen) festlegt ist, um das Debuggen einer beliebigen Anwendung zu starten. Die Debugkonfiguration stellt eine Reihe hilfreicher Tools zur Unterstützung des Debuggens bereit, zum Beispiel Haltepunkte, das Verwenden von Daten-Schnellansichten und das Anzeigen der Aufrufliste:

![Debugkonfiguration](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Festlegen eines Haltepunkts

Klicken Sie zum Festlegen eines Haltepunkts in Ihrer IDE im Randbereich Ihres Editors an der Stelle neben die Zeilennummer des Codes, an der Sie unterbrechen möchten:

![Festlegen eines Haltepunkts am Rand](media/debugging-image0.png)

Sie können alle gesetzten Haltepunkte in Ihrem Code anzeigen lassen, indem Sie zum **Pad für Haltepunkte** navigieren:

![Liste der Haltepunkte](media/debugging-image0a.png)

## <a name="start-debugging"></a>Debugging starten

Wählen Sie zum Starten des Debuggens den Zielbrowser, das Gerät bzw. den Simulator/Emulator aus:

![Debugkonfiguration](media/debugging-image_0.png)
![Zielgerät auswählen](media/debugging-image1.png)

Stellen Sie Ihre Anwendung dann bereit, indem Sie auf die Schaltfläche **Wiedergabe** klicken oder **STRG + EINGABETASTE** drücken. Wenn Sie einen Haltepunkt erreichen, wird der Code gelb hervorgehoben:

![Hervorhebung zum Anzeigen, dass ein Haltepunkt erreicht wurde](media/debugging-image2.png)

Debugtools wie zum Beispiel das, was zur Überprüfung der Werte eines Objekts verwendet wurde, können an dieser Stelle verwendet werden, um weitere Informationen zu den Vorgängen in Ihrem Code zu erhalten:

![Debugvisualisierungen](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Bedingte Haltepunkte

Sie können auch Regeln festlegen, durch die die Umstände bestimmt werden, unter denen ein Haltepunkt auftreten soll. Dies wird als das Hinzufügen eines *bedingten Haltepunkts* bezeichnet. Greifen Sie auf das **Fenster für Haltepunkteigenschaften** zu, um einen bedingten Haltepunkt festzulegen. Dazu gibt es zwei Möglichkeiten:

* Um einen neuen bedingten Haltepunkt hinzuzufügen, klicken Sie mit der rechten Maustaste links der Zeilennummer des Codes, an der Sie einen Haltepunkt setzen möchten, auf den Rand des Editors, und wählen Sie „Neuer Haltepunkt“:

 ![Kontextmenü des Haltepunkts](media/debugging-image4.png)

* Klicken Sie mit der rechten Maustaste auf den Haltepunkt, und klicken Sie auf **Haltepunkteigenschaften**, um eine Bedingung zu einem bestehenden Haltepunkt hinzuzufügen. Sie können auch auf die unten dargestellte Schaltfläche „Haltepunkt bearbeiten“ im **Pad für Haltepunkte** klicken:

 ![Bearbeiten eines bestehenden Haltepunkts im Pad für Haltepunkte](media/debugging-image5.png)

Anschließend können Sie die Bedingung eingeben, unter der der Haltepunkt auftreten soll:

 ![Bearbeiten von Haltepunktbedingungen](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Einzelschrittausführung von Code

Wenn ein Haltepunkt erreicht wird, gewähren Ihnen die Debugtools die Kontrolle über die Ausführung des Programms. Visual Studio für Mac zeigt vier Schaltflächen an, die es Ihnen ermöglichen, den Code auszuführen oder schrittweise zu durchzugehen. In Visual Studio für Mac sehen diese wie folgt aus:

 ![Schaltflächen zum schrittweisen Durchgehen des Codes](media/debugging-image7.png)

Hier sind die vier Schaltflächen:

* **Wiedergabe**: Dadurch wird die Ausführung des Codes gestartet, bis der nächste Haltepunkt erreicht wird.
* **Prozedurschritt**: Dadurch wird die nächste Codezeile ausgeführt. Wenn die nächste Zeile ein Funktionsaufruf ist, wird der Prozedurschritt die Funktion ausführen und in der nächsten Codezeile *nach* der Funktion anhalten.
* **Einzelschritt**: Dadurch wird ebenfalls die nächste Codezeile ausgeführt. Wenn die nächste Zeile ein Funktionsaufruf ist, wird der Einzelschritt in der ersten Zeile der Funktion anhalten, wodurch Sie die Funktion dann Zeile für Zeile debuggen können. Wenn die nächste Zeile keine Funktion ist, funktioniert diese Schaltfläche genauso wie der Prozedurschritt.
* **Rücksprung**: Dadurch wird zu der Zeile zurückgekehrt, in der die aktuelle Funktion aufgerufen wurde.

## <a name="debugging-monos-class-libraries"></a>Debuggen der Mono-Klassenbibliotheken

Xamarin-Produkte enthalten den Quellcode für die Mono-Klassenbibliotheken, die Sie verwenden können, um in einem einzigen Schritt vom Debugger zu einer Überprüfung der Vorgänge im Hintergrund zu gelangen.

Da dieses Feature während des Debuggens mehr Arbeitsspeicher benötigt, ist es standardmäßig deaktiviert.

Navigieren Sie zu **Visual Studio for Mac > Preferences > Debugger** (Visual Studio für Mac > Einstellungen > Debugger), um dieses Feature zu aktivieren und versichern Sie sich, dass die Option **Step into external code** (Schritt in externen Code) **aktiviert** ist, wie unten dargestellt:

![Option „Step into External Code“ (In externen Code springen)](media/debugging-image8.png)

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio (unter Windows)](/visualstudio/debugger/)
