---
title: Legacysprache Service Features1 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8fead42087699deb257b29093ee4349bbc8ef78
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333635"
---
# <a name="legacy-language-service-features"></a>Legacy-Dienst-Sprachfunktionen
Ein verwaltetes Paket Framework (MPF)-Sprachdienst unterstützen kann, einen oder mehrere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Features wie syntaxhervorhebung, IntelliSense und Validierung von Haltepunkt. Jede Funktion kann unabhängig von den anderen implementiert werden, aber alle erfordern, einen Parser und eine Überprüfung mit Ausnahme der syntaxhervorhebung, die nur eine Überprüfung erforderlich ist.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Beschreibt, was für die Unterstützung der Sprache paarvergleich, auch bekannt als Zuordnung von geschweiften Klammern erforderlich ist.

- [Kommentieren von Code in einem Legacysprachdienst](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Beschreibt, was zur Unterstützung von Kommentieren und Sie die ausgewählte Codezeilen auskommentieren erforderlich ist.

- [Benutzerdefinierte Dokumenteigenschaften in einem Legacysprachdienst](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Beschreibt, was ist erforderlich, um Dokumenteigenschaften zu unterstützen, die in einer Quelldatei eingebettet sind.

- [Gliederung in einem Legacysprachdienst](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Beschreibt, was zum unterstützen der Gliederung durch die Implementierung der ausgeblendeten Bereiche erforderlich ist.

- [Neuformatieren von Code in einem Legacysprachdienst](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Beschreibt, was für die Unterstützung der neuformatierung von Code erforderlich ist.

- [Unterstützen von Codeausschnitten in einem Legacysprachdienst](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Beschreibt, was ist erforderlich, um Codeausschnitte, unterstützen die Segmente des Codes sind, die eingefügt werden und können bearbeitet werden.

- [Parameterinformationen in einem Legacysprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Beschreibt, was ist zur Unterstützung des ParameterInfo IntelliSense-Vorgangs für die Signatur einer Methode anzeigen, wie die Methode eingegeben wurde.

- [QuickInfo in einem Legacysprachdienst](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Beschreibt, was zur Unterstützung des IntelliSense-QuickInfo-Vorgangs für die Anzeige von Informationen über einen Bezeichner erforderlich ist.

- [Membervervollständigung in einem Legacysprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Beschreibt, was erforderlich ist, zur Unterstützung des Membervervollständigung IntelliSense-Vorgangs für einen Member eines Namespaces aus einer Liste ausgewählt.

- [Wortvervollständigung in einem Legacysprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Beschreibt Funktionen erforderlich, um den vollständigen Wörtern durch IntelliSense-Vorgang zum Abschließen der teilweise eingegebene Wörter zu unterstützen.

- [Unterstützen des Auto-Fensters in einem Legacysprachdienst](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Beschreibt ein Sprachdienst Möglichkeiten zur Unterstützung der **"Auto"** Fenster während des Debuggens.

- [Unterstützen der Navigationsleiste in einem Legacysprachdienst](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Beschreibt, wie die **Navigationsleiste** am oberen Rand die Editor-Ansicht zu schnelle Navigation zu einem beliebigen Typ oder Member in der Datei, die in dieser Ansicht angezeigt...

- [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Beschreibt, was für die Unterstützung der syntaxhervorhebung des Quellcodes erforderlich ist.

- [Überprüfen von Haltepunkten in einem Legacysprachdienst](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Beschreibt, was ein Sprachdienst tun kann, um die Überprüfung Haltepunkte außerhalb eines Debuggers zu unterstützen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Beschreibt die Parser und Scanner, die erforderlich sind, um alle Features von einem Sprachdienst zu implementieren, die das managed Package Framework verwendet.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Beschreibt, was zu einen Sprachdienst zu implementieren, indem Sie mithilfe des verwalteten Paketframeworks erforderlich ist.

- [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Beschreibt die Schritte, die erforderlich sind, registrieren Sie eine MPF-basierten Sprachdienst mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Verwenden von IntelliSense](../../ide/using-intellisense.md)

 Erläutert, wie IntelliSense Sprachreferenzen einfach zugänglich macht.

- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Enthält Informationen dazu, wie Sie das managed Package Framework (MPF) verwenden, um einen Sprachdienst mit vollem Funktionsumfang in verwaltetem Code zu implementieren.