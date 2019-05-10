---
title: Grafik-API und Speicherstatistiken | Microsoft-Dokumentation
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7810889d4af411477573c71aa694d797a90763f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896018"
---
# <a name="graphics-api-and-memory-statistics"></a>Grafik-API und Speicherstatistiken
<!-- VERSIONLESS -->
Visual Studio 2017 und höhere Versionen unterstützen die Grafik-API-Statistiken und Speicherstatistiken-Tools.  Diese beiden Tools können Sie verschiedene Teile der Informationen zur Verwendung der Direct3D-API als auch für GPU-Speicherverbrauch von verschiedenen Ressourcen anzeigen.

## <a name="graphics-api-statistics"></a>Grafik-API-Statistiken
Die Grafik-API-Statistiken in Visual Studio-Grafikdiagnose können Sie anzeigen, die alle der Direct3D-Aufrufe, die vorgenommen wurden, und die Anzahl der bei jedem Aufruf.  Wählen Sie zum Anzeigen des Fensters der **Ansicht > API-Statistiken** Menüelement.

![API-Statistiken](media/gfx_diag_api_statistics.png)

Dieses Tool kann erkennen, dass DirectX-aufrufen, dass Sie nicht wissen vornehmen, oder Aufrufe, die Sie oft machen nützlich sein.

Sie können im Fenster auf Kopieren alle Daten als CSV-Datei, mit der rechten Maustaste, die zur weiteren Analyse in etwa wie in Excel eingefügt werden können.

## <a name="memory-statistics"></a>Speicherstatistiken
Dieses Tool zeigt, wie viel Arbeitsspeicher der Grafiktreiber, für die Ressourcen zugewiesen wird in einem Frame erstellen.  Um dieses Fenster anzuzeigen, wählen die **Ansicht > Speicherstatistiken** Menüelement.

![Speicherstatistiken](media/gfx_diag_memory_statistics.png)

Die **GPU-Zuordnung** angezeigt, die Arbeitsspeichermenge, die verwendet werden, von dem Ereignis angezeigt, der **Ereignis** Spalte.  Sie können auch auswählen, das Symbol "überwachen" ![Symbol "überwachen"](media/gfx_watch.png) zum Anzeigen der [Ressourcenverlauf](graphics-event-list.md#resource-history) für das ausgewählte Ereignis.

Wie das Tool für API-Statistiken, können Sie im Fenster auf Kopieren alle Daten als CSV-Datei, mit der rechten Maustaste, die zur weiteren Analyse in etwa wie in Excel eingefügt werden können.

## <a name="see-also"></a>Siehe auch
- [Grafikdiagnose (Debuggen von DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)
- [Ressourcenverlauf](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->