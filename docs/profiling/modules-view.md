---
title: Modulansicht | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89b3e7492e0f5155dd1c36f0140f6a1ad11db027
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829969"
---
# <a name="modules-view"></a>Modulansicht
In der Modulansicht werden die Module der Profilerstellungsdaten aufgelistet. Jedes Modul ist der Stammknoten einer hierarchischen Struktur. Die Profilfunktionen des Moduls, für die ein Sampling ausgeführt wurde, werden unter dem Modulknoten aufgeführt. Wenn die Profilerstellungsdaten mithilfe der Samplingmethode gesammelt wurden, werden Zeileninformationen unter dem Funktionsknoten aufgelistet, und Anweisungszeigerdaten werden unter dem Zeilenknoten aufgelistet.

 Erweitern oder reduzieren Sie den Modulnamen, um die Ansicht der Modulleistungsdaten anzuzeigen oder zu schließen.

 Klicken Sie zum Hinzufügen oder Entfernen von Spalten mit der rechten Maustaste in das Berichtsfenster, und wählen Sie anschließend **Spalten hinzufügen/entfernen** aus. Sie können die Daten durch Klicken auf einen Spaltennamen sortieren. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md).

 Welche Spalten in der Modulansicht verfügbar sind, ist abhängig von der Profilerstellungsmethode (Sampling oder Instrumentierung), die zum Sammeln der Daten verwendet wurde, und davon, ob in der Profilerstellungsausführung .NET-Arbeitsspeicherdaten gesammelt wurden.

## <a name="see-also"></a>Siehe auch
- [Modulansicht](../profiling/modules-view-sampling-data.md)
- [Modulansicht](../profiling/modules-view-instrumentation-data.md)
- [Modulansicht: .NET-Speicherinstrumentierungsdaten](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modulansicht: Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modulansicht](../profiling/modules-view-contention-data.md)