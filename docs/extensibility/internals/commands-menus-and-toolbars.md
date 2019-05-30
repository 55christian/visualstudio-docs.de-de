---
title: Befehle, Menüs und Symbolleisten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed5a91a819658fb141abb4301b9b9499ed602c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311159"
---
# <a name="commands-menus-and-toolbars"></a>Befehle, Menüs und Symbolleisten
Menüs und Symbolleisten sind, dass sich Benutzer Befehle im VSPackage zugreifen. Befehle sind Funktionen, mit denen Aufgaben wie das Drucken eines Dokuments, das Aktualisieren einer Ansicht oder das Erstellen einer neuen Datei ausgeführt werden können. Menüs und Symbolleisten stellen eine praktische Methode für die grafische Darstellung von Befehlen für Benutzer dar. In der Regel sind verwandte Befehle zusammen im gleichen Menü oder auf derselben Symbolleiste gruppiert.

- Menüs werden in der Regel als aus einem Wort bestehende Zeichenfolgen in einer Zeile im oberen Bereich der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) oder oben in einem Toolfenster gruppiert angezeigt. Menüs können auch durch Klicken mit der rechten Maustaste angezeigt werden. In diesem Kontext werden sie als Kontextmenüs bezeichnet. Beim Klicken auf ein Menü wird das Menü erweitert, sodass mindestens ein Befehl angezeigt wird. Wenn Sie auf Befehle klicken, können Aufgaben ausgeführt oder Untermenüs, die zusätzliche Befehle enthaltenen, geöffnet werden. Einige bekannte Menünamen sind **Datei**, **bearbeiten**, **Ansicht**, und **Fenster**. Weitere Informationen finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

- Symbolleisten sind in der Regel Zeilen, in denen Schaltflächen und andere Steuerelemente wie Kombinationsfelder, Listenfelder, Textfelder und Menüsteuerelemente angezeigt werden. Allen Symbolleisten-Steuerelementen sind Befehle zugeordnet. Wenn Sie auf eine Symbolleistenschaltfläche klicken, wird der zugeordnete Befehl aktiviert. Symbolleistenschaltflächen weisen normalerweise Symbole auf, die die zugrunde liegenden Befehle veranschaulichen. Ein Beispiel hierfür ist ein Drucker für den Befehl "Drucken". Bei Dropdownlisten-Steuerelementen ist jedes Element in der Liste einem anderen Befehl zugeordnet. Ein Menüsteuerelement ist eine Mischform, bei der eine Seite des Steuerelements eine Symbolleistenschaltfläche und die andere Seite ein Dropdownpfeil ist. Wenn Sie auf den Dropdownpfeil klicken, werden zusätzliche Befehle angezeigt. Weitere Informationen finden Sie unter [einer Symbolleiste ein Menücontroller hinzugefügt](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Wenn Sie einen Befehl erstellen, müssen Sie auch einen Ereignishandler für diesen Befehl erstellen. Der Ereignishandler bestimmt, wann der Befehl angezeigt oder aktiviert wird, ermöglicht Ihnen, den zugehörigen Text zu ändern, und stellt sicher, dass der Befehl entsprechend "reagiert", wenn er aktiviert wird. In den meisten Fällen verarbeitet die IDE Befehle mit der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>-Schnittstelle. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden Befehle hierarchisch weitergeleitet, beginnend mit dem innersten Befehlskontext, basierend auf der lokalen Auswahl, bis zum äußersten Kontext, basierend auf der globalen Auswahl. Befehle, die dem Hauptmenü hinzugefügt werden, sind sofort für die Skripterstellung verfügbar. Weitere Informationen finden Sie unter [MenuCommands im Vergleich. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) und [auswahlkontextobjekte](../../extensibility/internals/selection-context-objects.md).

  Um neue Menüs und Symbolleisten definieren möchten, müssen Sie sie in einer Visual Studio-Befehlstabelle beschreiben (*VSCT*) Datei. Die Visual Studio-Paketvorlage erstellt diese Datei für die Sie zusammen mit den erforderlichen Elementen zur Unterstützung, beliebige Befehle, Symbolleisten und Editoren, die Sie in der Vorlage ausgewählt. Alternativ Sie können eigene schreiben *VSCT* Datei, verwenden hier das XML-Schema beschrieben: [VSCT XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md).

  Weitere Informationen zum Arbeiten mit *VSCT* finden Sie unter [Visual Studio-Befehlstabellen (VSCT) Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  Die Themen in diesem Abschnitt wird erläutert, wie Befehle, Menüs und Symbolleisten in VSPackages zu arbeiten.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Eine ausführliche Beschreibung der Formatspezifikation Befehl Tabelle.

- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Beschreibt eine XML-basierter Syntax und die Compiler für Befehlstabellen.

- [Standardplatzierung-Befehl, Gruppe und Symbolleiste](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Beschreibt, vordefinierten Befehlen, Gruppen, Menüs und Symbolleisten.

- [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Gibt an, die vordefinierte Menüs, Befehle und Befehlsgruppen verfügbar, für die Verwendung durch die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Befehlsentwurf](../../extensibility/internals/command-design.md)

 Erläutert, wie Befehle zu entwerfen.

- [Optimieren von Menü-und Symbolleistenbefehle](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Bietet Richtlinien für Befehle.

- [Befehle zur Verfügung stellen](../../extensibility/internals/making-commands-available.md)

 Es wird erläutert, wie Befehle in Visual Studio verfügbar zu machen.

- [Befehle und Menüs, die interop-Assemblys verwenden.](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Erläutert, wie Sie Befehle zu implementieren, die interop-Assemblys verwenden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Erläutert das Befehlsrouting in VSPackages.