---
title: Erstellen benutzerdefinierte Ansichten von Daten im Debugger | Microsoft-Dokumentation
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32b3fddd13bd16ac2c846f02f54596ec846374b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929993"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Erstellen benutzerdefinierte Ansichten von Daten in Visual Studio-Debugger (C#, Visual Basic C++)

Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Debugger bietet viele Tools zum Überprüfen und ändern den Zustand des Programms. Die meisten dieser Tools funktionieren nur im Unterbrechungsmodus.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Erstellen Sie benutzerdefinierter Ansichten von Daten im Variablenfenster und DataTips

 Viele der [Debuggerfenster](../debugger/debugger-windows.md), z. B. die **"Auto"** und **Überwachen** Windows ermöglichen es Ihnen, Variablen untersuchen. Sie können anpassen, wie C++ Typen, verwaltete Objekte und Ihre eigenen Typen werden angezeigt, in den Variablenfenstern des Debuggers und im [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Weitere Informationen finden Sie unter [Erstellen benutzerdefinierter Ansichten von C++ Objekte](../debugger/create-custom-views-of-native-objects.md) und [erstellen benutzerdefinierte Ansichten von Objekten](../debugger/create-custom-views-of-dot-managed-objects.md).

## <a name="create-custom-visualizers"></a>Erstellen benutzerdefinierter Schnellansichten

 Schnellansichten können Sie den Inhalt eines Objekts oder der Variable auf sinnvolle Weise anzeigen. In der Visual Studio-Debugger von eine Schnellansicht, bezieht sich auf die anderen Fenster, die Sie öffnen können, verwenden das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol") Symbol. Beispielsweise zeigt der HTML-Schnellansicht, wie eine HTML-Zeichenfolge interpretiert und in einem Browser angezeigt werden sollen. Sie können Schnellansichten sind über DataTips, die **Watch** Fenster der **"Auto"** Fenster und die **"lokal"** Fenster. Die **Schnellüberwachung** Dialogfeld enthält außerdem eine Schnellansicht. Weitere Informationen finden Sie unter [Create Custom Visualizers (Erstellen benutzerdefinierter Schnellansichten)](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Siehe auch

- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Befehlsfenster](../ide/reference/command-window.md)
- [Debuggersicherheit](../debugger/debugger-security.md)