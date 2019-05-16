---
title: Visual Studio-Debugger-Erweiterbarkeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e337e87d162ac59cc6bb45676c1411692dd1a3bb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675267"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio Debugger-Erweiterbarkeit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio enthält einen vollständig interaktive Source Code-Debugger, ein leistungsfähiges und einfach zu verwendendes Tool für das Aufspüren von Fehlern in Ihrem Programm bereitstellen. Der Debugger hat die vollständige Unterstützung von Visual Basic, c#, C/C++- und JavaScript. Allerdings können mit der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], d. h. verfügbar der [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), anderen Programmiersprachen können in den Debugger mit den gleichen umfassenden Features unterstützt werden.  
  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger ist es die debugging-Komponenten, die, für die Sprache, die gedebuggt wird wiederum sind, das allgemeine Front-End (d. h. der Benutzeroberfläche). Für neue Sprachen, unterstützen alles, was erforderlich ist, indem die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger ist es die erforderlichen Back-End-Komponenten, z. B. einer Debug-Engine (DE) zu erstellen. Dieser befinden sich die [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] ins Spiel.  
  
 Die [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] enthält eine vollständige Referenz zu allen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Elemente, die zum Erstellen einer neuen DE erforderlich sind. Darüber hinaus stehen Beispiele und Lernprogramme, die Ihnen beim Einstieg helfen.  
  
 Ein End-to-End-Beispiel eines Sprache-Projektsystems mit debugging-Unterstützung finden Sie unter den [IronPython-Beispiel](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 In den folgenden Abschnitten wird beschrieben, wie den Debugger mit Erweitern der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Erfahren Sie, was [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen bietet und wie Sie das SDK zu installieren.  
  
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Dokumentiert die benutzerdefinierten DE-Prozess, von der Vorbereitung von Ihrem Programms für ein DE zum Trennen der DE.  
  
 [Schreiben einer CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Erläutert, ob Sie eine ausdrucksauswertung schreiben müssen.  
  
 [Auswählen einer Implementierungsstrategie für die Debug-Engine](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Erläutert, wie Ihre DE zu implementieren.  
  
 [Verweis](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Dokumente der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debug-API.  
  
 [Beispiele](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Enthält Links zu einem ausdrucksauswertung (Beispiel) common Language Runtime und ein Beispiel für die Debug-Engine.
