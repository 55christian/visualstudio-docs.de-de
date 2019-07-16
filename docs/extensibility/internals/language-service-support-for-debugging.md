---
title: Sprachdienstunterstützung für das Debuggen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d4946c25aeac2d677b7a527a3d2bb338db3aa31
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333645"
---
# <a name="language-service-support-for-debugging"></a>Sprachdienstunterstützung für das Debuggen
Ein Sprachdienst bieten Funktionen, die einen Debugger über unterstützen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> Schnittstelle. Zu diesen Funktionen gehören, Überprüfen von Haltepunkten und die Angabe einer Liste mit Ausdrücken, die die **"Auto"** Fenster.

 Allerdings benötigen Sie eine ausdrucksauswertung, um Ihre Sprache zu debuggen. Die ausdrucksauswertung ist verantwortlich für das Auswerten von Ausdrücken, um Werte während des Debuggens zu erzeugen. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter:

- [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Beispiele für verwaltete Ausdrucksauswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Kompilierungsausgabe
 Der Typ der Compiler bestimmt, was Sie tun, um das Debuggen für Ihre Sprache zu implementieren. Wenn Ihre Compiler das Windows-Betriebssystem betrifft und eine PDB-Datei schreibt, können Sie Programme debuggen, mit dem systemeigenen Code Debuggen-Engine, die in Visual Studio integriert ist. Wenn Ihr Compiler Microsoft intermediate Language (MSIL) erzeugt, können Sie Programme debuggen, mit den verwalteten Code Debuggen-Engine, die auch in Visual Studio integriert ist. Wenn der Compiler ein proprietäres Operating System oder eine andere Runtime-Umgebung ausgerichtet ist, müssen Sie Ihre eigenen Debug-Engine zu schreiben.

 Weitere Informationen zum Implementieren von Debuggen, die für Ihre Sprache finden Sie unter [Einstieg](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging SDK.