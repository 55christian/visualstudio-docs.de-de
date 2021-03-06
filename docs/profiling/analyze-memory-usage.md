---
title: Analysieren der Speicherauslastung
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 124b792e134b31a5964c8f202c7870a58bc0878b
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128250"
---
# <a name="analyze-memory-usage"></a>Analysieren der Speicherauslastung
Verwenden Sie das Diagnosetool für die **Speicherauslastung** mit integriertem Debugger, um Arbeitsspeicherverluste und nicht effiziente Speicherauslastung zu ermitteln. Mit dem Speicherauslastungstool können Sie einen oder mehrere *Momentaufnahmen* des verwalteten und systemeigenen Momentaufnahme-Heaps machen. Sie können Momentaufnahmen von .NET-Apps, ASP.NET-Apps, nativen Apps und Apps im gemischten Modus (.NET und nativ) erfassen.

- Sie können eine einzelne Momentaufnahme analysieren, um die relativen Auswirkungen der Objekttypen auf die Arbeitsspeichernutzung zu verstehen und Code in der App zu suchen, die Arbeitsspeicher auf ineffiziente Weise verwendet.

- Sie können auch einen Vergleich zweier Momentaufnahmen einer App vornehmen, um Bereiche im Code aufzuspüren, die dazu führen, dass die Arbeitsspeichernutzung im Zeitverlauf zunimmt.

Weitere Informationen finden Sie im Tutorial [Analysieren der Speicherauslastung](../profiling/memory-usage.md).  Um den Speicherverbrauch für eine.NET Core-Anwendung zu messen, müssen Sie derzeit das Tool mit dem angefügten Debugger verwenden. Für andere verwaltete und native Apps können Sie das Tool entweder mit oder ohne angefügten Debugger verwenden.

Unter Windows 7 und höher können Sie die Profilerstellungstools ohne den Debugger verwenden. Windows 8 und höher ist erforderlich, um die Profilerstellungstools mit dem Debugger auszuführen (Fenster **Diagnosetools**).

## <a name="blogs-and-videos"></a>Blogs und Videos

[Analyze CPU and Memory While Debugging (Analysieren der CPU und des Arbeitsspeichers beim Debuggen)](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Team Blog: Memory Profiling in Visual C++ 2015 (Visual C++-Teamblog: Speicherprofilerstellung in Visual C++ 2015)](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Siehe auch

- [Profilerstellung in Visual Studio](../profiling/index.yml)
- [Einführung in Profilerstellungstools](../profiling/profiling-feature-tour.md)