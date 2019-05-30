---
title: Mitwirken am Automatisierungsmodell | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47e6686c82dcb0272fa9b3b3c4d3b7c73afe4475
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335445"
---
# <a name="contribute-to-the-automation-model"></a>Mitwirken Sie am Automatisierungsmodell
Visual Studio bietet eine Reihe von Automatisierungsschnittstellen für die Umgebung anzupassen. Das Automatisierungsmodell ist das Objektmodell, das Benutzer zum Erstellen von Visual Studio-add-ins und-Erweiterungen ermöglicht.

 Darüber hinaus ist es für Sie geeignet als VSPackage-Entwickler zum Automatisierungsmodell beitragen. auf diese Weise können Sie Endbenutzer, die von einem VSPackage-add-ins erstellen und Bereitstellen in der Regel eine konsistente benutzererfahrung Modell aus, wenn sie Ihr VSPackage in verwenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Um die endbenutzererfahrung konsistent zu machen, können Sie eine Reihe von Richtlinien befolgen, wie Sie das VSPackage so entwerfen, dass das Automatisierungsmodell für das VSPackage die Ideen folgt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>In diesem Abschnitt
- [Übersicht über das Automatisierungsmodell](../../extensibility/internals/automation-model-overview.md)

 Definiert das Automatisierungsmodell eine miteinander verbundene Gruppen von Objekten, die wesentliche Merkmale der gemeinsamen Umgebung zu steuern. Dieser Satz von Objekten ist in einem Diagramm des Automatisierungsmodells abgebildet.

- [Bereitstellen von Automatisierung für VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Beschreibt die zwei Hauptmethoden zum Bereitstellen von Automatisierung für Ihr VSPackage.

- [Bereitstellen von Projektobjekten](../../extensibility/internals/exposing-project-objects.md)

 Bietet schrittweise Anleitungen zum Erstellen von VSPackage-Objekten.

- [Projektmodellierung](../../extensibility/internals/project-modeling.md)

 Erläutert die standard-Projekt-Objekte, die zum Erstellen von Automation für den neuen Projekttyp erforderlich sind, und zeigt den Pfad für den Projekt-Automatisierung entspricht. Dieses Thema enthält auch Auflistungen von Deklarationen und Implementierung für Klassen.

- [Ereignisse verfügbar machen](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Bietet schrittweise Anleitungen zum Erstellen von Ereignissen für Ihr Automatisierungsmodell.

- [Unterstützung der Automatisierung für Optionsseiten](../../extensibility/internals/automation-support-for-options-pages.md)

 Beschreibt, wie Sie ein Automatisierungsobjekt zurück, für die Eigenschaften von einem VSPackage unterstützt benutzerdefinierte ist **Optionen** Dialogfeld auf die **Tool** Menü durch die Erweiterung der `DTE.Properties` Objekt.

- [Bereitstellen von Automatisierung für code](../../extensibility/internals/providing-automation-for-code.md)

 Erklärt, dass die Erstellung eines Automatisierungsmodells für Ihren Code nicht erforderlich ist. Allerdings wird ein Link in diesem Thema bereitgestellt, die aussagekräftige Informationen in Codemodelle enthält.

- [Vorgehensweise: Bereitstellen von Automatisierung für Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Erklärt, dass das Bereitstellen von Automatisierung ist eine gute Idee, wann immer Sie-Automatisierungsobjekte in einem Fenster zur Verfügung stellen möchten, und die Umgebung eine vorgefertigte Automatisierungsobjekt keine bereits bietet. Erläutert die Automatisierung für Toolfenster und Dokumentfenster.

- [Verwenden Sie das Automatisierungsmodell](../../extensibility/internals/using-the-automation-model.md)

 Enthält zwei Codebeispiele, die zeigen, wie ein automatisierungsbenutzer das ursprüngliche Projekt Automatisierungsobjekte erhält.

- [Automatisierung für Konfigurations- und SelectedItem-Objekte](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Enthält Informationen zur Automatisierung für Konfigurations- und SelectedItems-Objekte.

## <a name="reference"></a>Referenz
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Enthält ein Codebeispiel, das zeigt, wie eine VSPackage das DTE-Automatisierungsobjektmodell teilnimmt. Listen-Parameter, Rückgabewerte und ausgewählte "Hinweise".
