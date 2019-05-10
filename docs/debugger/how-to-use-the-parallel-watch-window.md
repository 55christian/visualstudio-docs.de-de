---
title: Festlegen eines Überwachungselements für Variablen in parallelen Threads | Microsoft-Dokumentation
ms.date: 04/25/2017
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6026ab6d0d59fb3a8f945e554fda26f10d98f952
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388474"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Festlegen eines Überwachungselements für Variablen in parallelen Threads in Visual Studio (C#, Visual Basic C++)
Im parallelen Überwachungsfenster können Sie gleichzeitig die Werte anzeigen, die ein Ausdruck auf mehreren Threads enthält. Jede Zeile stellt einen Thread in einer Anwendung ausgeführten dar. Allerdings wird ein Thread möglicherweise in mehreren Zeilen angezeigt werden. Genauer gesagt stellt jede Zeile einen Funktionsaufruf dar, dessen Funktionssignatur der Funktion auf dem aktuellen Stapelrahmen entspricht. Sie können die Elemente in den Spalten sortieren, neu anordnen, entfernen und gruppieren. Sie können Threads kennzeichnen bzw. die Kennzeichnung aufheben, ihn einfrieren (anhalten) und reaktivieren (fortsetzen). Die folgenden Spalten werden im Fenster **Parallele Überwachung** angezeigt:

- Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.

- Der aktuelle Thread-Spalte, in der ein gelber Pfeil den aktuellen Thread gibt (ein grüner Pfeil in Form einer Welle gibt an, dass eine nicht-aktuellen Threads den aktuellen Debuggerkontext hat).

- Eine konfigurierbare Spalte, in der der Computer, der Prozess, die Kachel, die Aufgabe und der Thread angezeigt werden können.

  > [!TIP]
  > Zum Anzeigen von Aufgabeninformationen in den **parallele Überwachung** Fenster müssen Sie zuerst öffnen die **Aufgabe** Fenster.

- Die leere *Überwachung hinzufügen* Spalten, in dem Sie Ausdrücke zur Überwachung eingeben können.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>So zeigen Sie das parallele Überwachungsfenster an

1. Legen Sie einen Haltepunkt im Code fest.

2. Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debuggen starten**. Warten Sie, bis die Anwendung den Haltepunkt erreicht hat.

3. Klicken Sie in der Menüleiste auf **Debuggen**, **Fenster**, **Parallele Überwachung**, und wählen Sie dann ein Überwachungsfenster aus. Sie können bis zu vier Fenster öffnen.

### <a name="to-add-a-watch-expression"></a>So fügen Sie einen Überwachungsausdruck hinzu

- Wählen Sie eine vom leer *Überwachung hinzufügen* Spalten und geben Sie einen Überwachungsausdruck.

### <a name="to-flag-or-unflag-a-thread"></a>So Kennzeichnen Sie einen Thread bzw. haben die Kennzeichnung auf

- Wählen Sie die Spalte zur Kennzeichnung für die Zeile (erste Spalte), oder öffnen Sie das Kontextmenü für den Thread, und wählen Sie **Flag** oder **Flag**.

### <a name="to-display-only-flagged-threads"></a>So zeigen Sie nur gekennzeichnete Threads an

- Wählen Sie die **nur gekennzeichnete Elemente anzeigen** -Schaltfläche in der oberen linken Ecke des der **parallele Überwachung** Fenster.

### <a name="to-switch-to-another-thread"></a>So wechseln Sie zu einem anderen thread

- Doppelklicken Sie auf die Spalte mit dem aktuellen Thread (zweite Spalte). (Tastatur: Wählen Sie die Zeile, und drücken Sie die EINGABETASTE.)

### <a name="to-sort-a-column"></a>So sortieren Sie eine Spalte

- Wählen Sie Spaltenüberschrift aus.

### <a name="to-group-threads"></a>So gruppieren Sie Threads

- Öffnen Sie das Kontextmenü für das parallele Überwachungsfenster, wählen Sie die Option **Gruppieren nach** aus, und wählen Sie dann das entsprechende Untermenüelement aus.

### <a name="to-freeze-or-thaw-threads"></a>So frieren Sie Threads ein oder reaktivieren sie

- Öffnen Sie das Kontextmenü für die Zeile, und wählen Sie dann **Einfrieren** oder **Reaktivieren** aus.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>So exportieren Sie Daten in das parallele Überwachungsfenster

- Wählen Sie die Schaltfläche **In Excel öffnen** aus, und wählen Sie dann **Exportieren nach CSV** oder **In Excel öffnen** aus.

### <a name="to-filter-by-a-boolean-expression"></a>So filtern Sie nach einem booleschen Ausdruck

- Geben Sie im Feld **Nach booleschem Ausdruck filtern** einen booleschen Ausdruck ein. Vom Debugger wird der Ausdruck für jeden Threadkontext ausgewertet. Nur Zeilen mit einem Wert von `true` werden angezeigt.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Vorgehensweise: Verwenden des Fensters „GPU-Threads“](../debugger/how-to-use-the-gpu-threads-window.md)
- [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)