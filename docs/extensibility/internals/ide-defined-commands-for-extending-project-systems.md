---
title: IDE-definierte Befehle zum Erweitern von Projektsystemen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26f5ee29a52546e7f2111189f54d64c160a94cea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860345"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>IDE-definierte Befehle zum Erweitern von Projektsystemen
Beim Erweitern von Projektsystemen werden sollen, können Sie Befehle verwenden und Gruppen, die von bereitgestellte Befehl die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Befehls-Elemente, die besonders nützlich zum Erweitern von Projektsystemen sind Sie in den folgenden Abschnitten.

## <a name="command-menus"></a>Befehlsmenüs
 Die folgende Tabelle zeigt die Befehlsmenüs, die sind hilfreich für Sie Befehlen auf höherer Ebene zu platzieren, die einen Extender Projekt aufrufen.

|Menü "Command"|Beschreibung|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Die **Projekt** Menü der obersten Ebene.|
|IDM_VS_TOOL_PROJWIN|Die **Projektmappen-Explorer** Symbolleiste.|

## <a name="shortcut-menus"></a>Kontextmenüs
 Die folgende Tabelle zeigt die Kontextmenüs, die gelten, wenn in ein einzelnen Knoten ausgewählt wird die **Projektmappen-Explorer**, oder es gibt mehrere homogene Auswahl in der **Projektmappen-Explorer**, der ist, wenn alle ausgewählte Knoten werden vom gleichen Typ sind.

|Kontextmenü|Beschreibung|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Gilt, wenn Sie der Knoten des Projekts ausgewählt ist.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Gilt, wenn eine Datei ausgewählt ist.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Gilt, wenn ein Ordner ausgewählt ist.|
|IDM_VS_CTXT_WEBREFFOLDER|Gilt, wenn der Webverweis-Ordner ausgewählt ist.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Gilt, wenn die Verweise Stammknoten namens "Referenzen" ausgewählt ist.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Gilt, wenn Knoten ausgewählt sind. Dazu gehören die Assembly, COM und nur die Projektverweise. Umfasst keine Webverweise.|

 Die folgende Tabelle zeigt die Kontextmenüs, die beim Anwenden der Auswahl in der **Projektmappen-Explorer** erstreckt sich über mehrere Hierarchien.

|Kontextmenü|Beschreibung|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Gilt, wenn die aktuelle Auswahl der Knoten "Projektmappe" und die Stammknoten-Projekt enthält.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Gilt, wenn die aktuelle Auswahl Projektmappenelemente Knoten und das Projekt enthält.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Gilt, wenn mehrere Projekt Stammknoten nur die aktuelle Auswahl besteht.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Gilt, wenn die aktuelle Auswahl um eine Mischung aus Projekt Stammknoten und Projektelemente enthält. Darüber hinaus kann die Auswahl der Knoten "Projektmappe" enthalten.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Gilt, wenn die aktuelle Auswahl Projektelemente aus mehreren Projekten in der Projektmappe enthält oder wenn Elemente verschiedener Typen im selben Projekt ausgewählt sind.|

## <a name="command-groups"></a>Befehlsgruppen
 Die folgende Tabelle zeigt die Befehlsgruppen, die Sie verwenden können, wenn Sie die Projekte erweitern, und die Sie zugreifen können, über die <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> im Kontextmenü.

|Befehlsgruppe|Beschreibung|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Befehle zum Erstellen, Neuerstellen und beim Bereitstellen des Projekts.|
|IDG_VS_CTXT_COMPILELINK|Befehle zum Kompilieren und verknüpfen das Projekt.|
|IDG_VS_CTXT_PROJECT_CONFIG|Befehle, die Konfiguration des Projekts festgelegt und Buildreihenfolge.|
|IDG_VS_CTXT_PROJECT_ADD|Befehle, die dem Projekt Elemente hinzu.|
|IDG_VS_CTXT_PROJECT_START|Befehle, die das zugeordnete der F5-Taste Startprojekt festzulegen.|
|IDG_VS_CTXT_PROJECT_SAVE|Befehle für das Speichern von Projektelementen.|
|IDG_VS_CTXT_PROJECT_DEBUG|Befehle zum Debuggen.|
|IDG_VS_CTXT_PROJECT_SCC|Befehle für die quellcodeverwaltung.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Befehle zum Ausschneiden, kopieren und einfügen.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Befehle, die Zugriff auf ermöglichen die **Projekteigenschaften** Dialogfeld.|

## <a name="see-also"></a>Siehe auch
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [MenuCommands im Vergleich zu OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Erstellen von wiederverwendbaren Gruppen von Schaltflächen](../../extensibility/creating-reusable-groups-of-buttons.md)