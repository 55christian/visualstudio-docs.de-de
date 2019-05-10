---
title: Erste Schritte mit dem Debugger-Erweiterbarkeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f3fe14cff05f37ef7ee6f10026fd727696a223f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925705"
---
# <a name="get-started-with-debugger-extensibility"></a>Erste Schritte mit dem Debugger-Erweiterbarkeit
Die [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] enthält die Informationen, die Sie zum Erstellen und Anpassen von Debugger-Komponenten verwendet benötigen, um das Debuggen von Programmen innerhalb der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen von Verbesserungen, die die umfassende benutzerfreundlichkeit, die auf vorherigen durchgeführten Tests abgeleitet wurden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger. Sie können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugging für Schritt durch eine Anwendung mehrsprachig, oder Sie können auf dynamische Bearbeitung von Variablen beim Debuggen von Anwendungen und Lösungen mit mehreren Sprachen implementieren.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ist ausgeführten Out-of-Process mit dem Programm im Debugmodus befindlichen und daher weniger intrusiv im Prozessbereich der Anwendung. Daher ist es einfacher, Komponenten, die Interaktion mit dem Debugger zu schreiben, ohne Auswirkungen auf das Programm debuggen.

 Die optimale Verwendung der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], Sie sollten mit den folgenden Artikeln vertraut sein:

- Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE)

- Die Programmiersprache C++

- ATL COM

## <a name="in-this-section"></a>In diesem Abschnitt
 [Roadmap für die Erweiterung des Debuggers](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) beschreibt den Prozess der Implementierung in Ihrem Produkt, je nach dem Compiler und seine Ausgabe Debuggen.

 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md) bietet eine Übersicht über die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugging-Komponenten, die die Debug-Engine (DE), die ausdrucksauswertung (EE) und die Symbol-Handler (SH) enthalten.

 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Konzepte für das Debuggen Architektur.

 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) wird erläutert, wie die Debug-Engine (DE) gleichzeitig innerhalb von Code, Dokumentationen und Ausdruck Auswertung Kontexten ausgeführt wird. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Auswertung, die für sie relevant.

 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md) enthält Links zu verschiedenen Debuggingaufgaben ausführen, z. B. Starten eines Programms und Auswerten von Ausdrücken.