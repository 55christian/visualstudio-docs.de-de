---
title: 'Vorgehensweise: Ereignisse auszulösen, wenn der Editor den Fokus verliert. | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57cc24847e0a7635c27a78e983b2bf46ed4326c5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340848"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Vorgehensweise: Lösen Sie Ereignisse aus, wenn der Editor den Fokus verliert.
Manchmal ist es notwendig zu wissen, wenn Sie ein Editor den Fokus auf den Fensterrahmen verliert. Beispielsweise müssen Sie Code aus einem Codefenster zu extrahieren, nachdem der Editor nicht mehr darauf ausgerichtet ist. Das folgende Verfahren enthält die Schritte zum Empfangen von Benachrichtigungen über den Editor den Fokus.

## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Zum Auslösen eines Ereignisses als Reaktion auf einen Editor den Fokus

1. Auswahlereignisse überwachen, durch Abrufen einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> -Sitzungsobjekts <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.

2. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> und Bereitstellen Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> Objekt.

3. Der Aufruf <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, suchen Sie nach `elementid==SEID_WindowFrame`.

4. Testen der `varValueNew` Parameter für zwei Dinge:

    1. Der Fensterrahmen, die, den Sie suchen.

    2. Der Punkt, an dem das Programm die Auswahl auf, das diesem Fensterrahmen verliert.