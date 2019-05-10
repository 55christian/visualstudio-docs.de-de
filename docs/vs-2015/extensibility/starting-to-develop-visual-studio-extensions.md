---
title: Starten, um Erweiterungen zu entwickeln | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6d8050ea7447a67f50f42157d57c17d3f1f8a329
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038631"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Starten Visual Studio-Erweiterungen entwickeln
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Visual Studio-Erweiterung vor nie geschrieben haben, verfügen Sie wahrscheinlich einige Fragen. Wir haben einige der am häufigsten verwendeten Tools hier aufgeführt. Wenn Sie die Informationen nicht wird Sie suchen angezeigt, verwenden Sie die Feedback-Schaltflächen (**war diese Seite hilfreich?** am unteren Rand des Bildschirms), bitten Sie den gewünschten.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Welche Software benötige ich zum Entwickeln von Visual Studio-Erweiterungen?
 Sie müssen das Visual Studio 2015 SDK zusätzlich zu Visual Studio 2015 zum Entwickeln von Visual Studio-Erweiterungen zu installieren.   Sie können die Visual Studio 2015 SDK installieren, als Teil der regulären Installation, oder Sie können sie später installieren. Weitere Informationen zum Installieren von Visual Studio SDK finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Welche Arten von Elementen kann ich mit Visual Studio-Erweiterungen?
 Vom Himmel zu holen ist die Grenze aus, wenn es darum geht, so vor anderen Visual Studio-Erweiterungen. Natürlich bei den meisten Erweiterungen haben etwas zu tun, Code zu schreiben, aber müssen, die nicht der Fall sein. Hier sind einige Beispiele für die Arten von Erweiterungen aus, die Sie erstellen können:

- Unterstützung für Sprachen, die nicht mit Farben für Syntax, IntelliSense und Unterstützung für Compiler und Debuggen in Visual Studio enthalten sind

- Produktivitätstools, die den Kern erweitern IDE-Erfahrung mit zusätzlichen Vorlagen, refactoring, neuer Code-Dialogfelder oder Toolfenster

- Domänenspezifische-Designern für Szenarien wie die Unterstützung der Entwurf oder in der cloud

  Beispiele für Erweiterungen, sehen Sie sich die [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Sie können außerdem sehen Sie sich [Visual Studio Open-Source-Erweiterungen](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).

## <a name="which-visual-studio-features-can-i-extend"></a>Welche Features von Visual Studio kann werden erweitert?
 Theoretisch können Sie fast jeden Teil von Visual Studio erweitern: Menüs, Symbolleisten, Befehle, Windows, Lösungen, Projekte, Editoren und So weiter.

 In der Praxis haben wir festgestellt, dass die Funktionen, die meisten Benutzer erweitern möchten Befehle, Menüs und Symbolleisten, Windows, IntelliSense und Projekte. Hier sind Links zu den relevanten Abschnitten:

- [Erweitern von Menüs und Befehlen](../extensibility/extending-menus-and-commands.md): Hinzufügen Ihrer eigenen Artikel zu Visual Studio-Menüs und Symbolleisten. Sie können Sie um neue Funktionen von Visual Studio oder Ihren eigenen externen Helper-Anwendungen zu starten. Sie können auch benutzerdefinierte Tastenkombinationen für den Menüelementen bereitstellen.

- [Erweitern und Anpassen von Tool Windows](../extensibility/extending-and-customizing-tool-windows.md): Erweitern Sie vorhandene Toolfenster oder erstellen Sie eigene Toolfenster. Sie könnten z. B. neue Eigenschaften zu Hinzufügen der **Eigenschaften**, oder erstellen Sie ein neues Toolfenster, um zusätzliche Features hinzuzufügen.

- [Editor und Sprachdiensterweiterungen](../extensibility/editor-and-language-service-extensions.md): Fügen Sie Ihre eigenen Anpassungen IntelliSense für Visual Studio-Sprachen bereitgestellt, oder erstellen Sie Unterstützung für neue Programmiersprachen. Sie können neue anweisungsvervollständigungen, Vorschläge und eine neue QuickInfos erstellen. Klicken Sie mit Glühbirnen können Sie die Umgestaltung Vorschläge hinzufügen, und codefehlerbehebungen um neue Programmiersprachen zu unterstützen.

- [Erweitern von Projekten](../extensibility/extending-projects.md)

- [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md)

- [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)

- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)

## <a name="BKMK_ProjectTemplate"></a> Welche Projektvorlagen werden von der VSSDK bereitgestellt?
 Die zwei wichtigsten Typen von Erweiterungen sind VSPackages und MEF-Erweiterungen. Im Allgemeinen werden die VSPackage-Erweiterungen für Erweiterungen verwendet, die verwenden oder Erweitern von Befehlen, Toolfenster und Projekte. MEF-Erweiterungen werden zum Erweitern oder Anpassen von Visual Studio-Editor.

 Für Erweiterungen für Visual c# und Visual Basic bietet das VS SDK eine leere VSIX-Projektvorlage, die Sie zusammen mit den neuen Vorlagen verwenden können, die Menübefehle, Toolfenster und Erweiterungen des Editors zu erstellen. Weitere Informationen finden Sie unter [Neuigkeiten in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). Sie können auch diese Vorlage, um die Paket-Projektvorlage, Codeausschnitte und andere Artefakte für die Verteilung an andere Benutzer verwenden.

 Für C++ bietet der VSPackage-Assistent den Code zum Hinzufügen von Menübefehle, Toolfenster und benutzerdefinierte Editoren.

 Die Isolated Shell-Vorlage wird verwendet, um eine Erweiterung in einer Version von Visual Studio Shell zu verpacken, die Sie kennzeichnen und Ihren eigenen verteilen. In den folgenden Themen wird gezeigt, wie erste Schritte mit jeder Art von Erweiterung wird:

- Befehle im Menü: [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

- Toolfenster: [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md)

- Editorerweiterungen: [Erstellen einer Erweiterung mit einer Editor-Elementvorlage](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Grundlegende VSPackages: [Erstellen einer Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- VSIX-Projektvorlage aus: [Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)

- Visual Studio isolated Shell: [Exemplarische Vorgehensweise: Erstellen einer grundlegenden Isolated Shell-Anwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Wie erhalte ich die my-Erweiterung zu Visual Studio aussehen?
 Erhalten Sie nützliche Tipps zum Entwerfen der Benutzeroberflächenautomatisierungs für die Erweiterung im [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Wo finde ich Beispiele für VSSDK Code?
 Jedem im vorherigen Abschnitt aufgeführten Links werden schrittweise beschriebenen exemplarischen Vorgehensweisen, in denen Sie die erläutert, um bestimmte Funktionen zu implementieren. Sie erhalten auch open-Source VSSDK-Beispiele auf GitHub unter [Visual Studio-Beispiele](https://aka.ms/vs2015sdksamples).

## <a name="how-can-i-distribute-my-extension"></a>Wie kann ich die my-Erweiterung verteilen?
 Sie können die Erweiterung auf einem anderen Computer installieren oder als eine VSIX-Datei, die Sie installieren, indem Sie darauf doppelklicken an Freunde senden. Finden Sie weitere Informationen zu VSIX-Pakete auf [Auslieferung von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).

 Sie können auch Ihre Erweiterung in der Visual Studio Gallery veröffentlichen für eine große Anzahl von Visual Studio-Kunden angezeigt werden. Ein Beispiel für das Verpacken einer Erweiterung für den Katalog, finden Sie unter [Exemplarische Vorgehensweise: Veröffentlichung von Visual Studio-Erweiterung](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Weitere Informationen, was Sie tun, um die im Katalog veröffentlichen müssen, finden Sie unter [Produkte und Erweiterungen für Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
