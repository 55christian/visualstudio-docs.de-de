---
title: Erstellen eines Quellcodeverwaltungs-Plug-in | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8489e991a54df5b905289a64fccb0df65c3cec8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341926"
---
# <a name="create-a-source-control-plug-in"></a>Erstellen eines Quellcodeverwaltungs-Plug-in
Visual Studio SDK enthält Ressourcen, die Ihnen ermöglichen, Quelle Steuerungsfunktionen zum Hinzufügen der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE). Sie können anhand eine Plug-in-DLL, die erfüllt mit der Source-Plug-in-API in dieser Dokumentation beschrieben.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Erste Schritte](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 Beschreibt, wie Sie ein Quellcodeverwaltungs-Plug-in zu installieren, und hebt die derzeit verfügbaren Source Control-Plug-in-API-Versionen.

- [Architektur](../../extensibility/internals/source-control-plug-in-architecture.md)

 Verwendet ein Architekturdiagramm zur Erläuterung der Integration von eines Quellcodeverwaltungs-Plug-in mit der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Test-Handbuch](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 Enthält Anleitungen dazu, wie Sie die Installation und Ausführung von eines Quellcodeverwaltungs-Plug-in zu testen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Erläutert, wie ein Quellcodeverwaltungs-VSPackage zu erstellen, die nicht nur ein Knoten ersetzt jedoch stellt Quellcodeverwaltungsfunktionen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Datenquellen-Steuerelement-Benutzeroberfläche.

- [Quellcodeverwaltungs-Plug-ins](../../extensibility/source-control-plug-ins.md)

 Enthält eine vollständige Liste aller Elemente in der Quelle-Plug-in-API.

- [Datenquellen-Steuerelement](../../extensibility/internals/source-control.md)

 Erläutert die Optionen zum Implementieren von Datenquellen-Steuerelement als eine integrierte Funktion von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
