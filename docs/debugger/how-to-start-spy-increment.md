---
title: 'Vorgehensweise: Starten von Spy++ | Microsoft-Dokumentation'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc247a6391df0357905e2cbdb895bec4e469a248
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387531"
---
# <a name="how-to-start-spy"></a>Vorgehensweise: Starten von Spy++

Sie können Spy++ aus Visual Studio oder an einer Eingabeaufforderung starten.

 Wenn Sie Starten von Spy++, wenn eine Nachricht angezeigt wird, um zu Fragen, berechtigt, Änderungen auf dem Computer, auf **Ja**.

> [!NOTE]
> Sie können nur eine Instanz von Spy++ ausführen. Wenn Sie versuchen, eine zweite Instanz gestartet, wird nur die aktuell ausgeführte Instanz aus, um den Fokus erhalten.

## <a name="prerequisites"></a>Vorraussetzungen

Spy++-müssen die folgenden Komponenten ein. Sie können diese Komponenten aus Visual Studio-Installer auswählen, durch Auswählen der **Einzelkomponenten** Registerkarte, und wählen Sie dann die folgenden Komponenten.

* Wählen Sie unter Debuggen und Testen von  **C++ Profilerstellungstools**
* Wählen Sie unter Entwicklungsaktivitäten, **Visual Studio C++ Kernfeatures**

Wenn Sie keine Änderungen vorgenommen haben, führen Sie die Anweisungen zum Installieren dieser Komponenten.

## <a name="start-spy-from-visual-studio"></a>Starten von Spy++ aus Visual Studio

Auf der **Tools** , wählen Sie im Menü **Spy++**.

Da Spy++ unabhängig voneinander ausgeführt wird, nachdem Sie ihn starten, können Sie Visual Studio schließen.

> [!NOTE]
> Wenn Sie Nachrichten mit Spy++, führt dies möglicherweise langsamer ausgeführt, das Betriebssystem.

## <a name="start-spy-at-a-command-prompt"></a>Starten von Spy++ an einer Eingabeaufforderung

1. Ein Eingabeaufforderungsfenster wechseln Sie zu dem Ordner, der spyxx.exe enthält. In der Regel ist der Pfad zu diesem Ordner... \\ *Visual Studio-Installationsordner*\Common7\Tools\\.

2. Geben Sie **spyxx.exe** ein.

## <a name="see-also"></a>Siehe auch
- [Verwenden von Spy++](../debugger/using-spy-increment.md)
- [Spy++-Ansichten](../debugger/spy-increment-views.md)
- [Spy++-Referenz](../debugger/spy-increment-reference.md)