---
title: Optionen, Text-Editor, JavaScript, Projekt
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09ed64d6bffaa4453c3294229ee48fd0a065eb74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778172"
---
# <a name="options-text-editor-javascript-project"></a>Optionen, Text-Editor, JavaScript, Projekt

Verwenden Sie die Seite **Projekt** des Dialogfelds **Optionen**, um JavaScript-Projektoptionen im Code-Editor anzugeben. Öffnen Sie diese Seite, indem Sie auf der Menüleiste auf **Tools** > **Optionen** klicken und anschließend **Text-Editor** >  **JavaScript** > **Projekt** erweitern.

## <a name="project-analysis-options"></a>Projektanalyseoptionen

Diese Optionen bestimmen, wie der Editor Projekte, Berichte und Diagnosen analysiert und Verbesserungen vorschlägt. Aktivieren oder deaktivieren Sie die Optionen, um festzulegen, wie der Editor mit diesen Situationen umgeht.

### <a name="uielement-list"></a>UIElement-Liste

- **Nur Projekte analysieren, die Dateien enthalten, die im Editor geöffnet wurden**
- **Nur Diagnosen für Dateien melden, die im Editor geöffnet wurden**
- **Verbesserungsmöglichkeiten vorschlagen (keine Korrekturen)**

## <a name="virtual-projects-in-solution-explorer"></a>Virtuelle Projekte im Projektmappen-Explorer

Mit diesen Optionen können Sie wählen, ob virtuelle Projekte angezeigt werden sollen, wenn eine Lösung entweder geladen oder nicht geladen ist.

## <a name="compile-on-save"></a>Beim Speichern kompilieren

Diese Optionen bestimmen, ob TypeScript-Dateien, die nicht Teil des Projekts sind, automatisch kompiliert werden. Aktivieren Sie das Kontrollkästchen und wählen Sie dann die Art der Codegenerierung, die verwendet werden soll.

### <a name="uielement-list"></a>UIElement-Liste

- **AMD-Codegenerierung für Module verwenden, die nicht Teil eines Projekts sind**
- **CommonJS-Codegenerierung für Module verwenden, die nicht Teil eines Projekts sind**
- **UMD-Codegenerierung für Module verwenden, die nicht Teil eines Projekts sind**
- **Systemcodegenerierung für Module verwenden, die nicht Teil eines Projekts sind**
- **ES2015-Codegenerierung für Module verwenden, die nicht Teil eines Projekts sind**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>ECMAScript-Version für Dateien verwenden, die nicht Teil eines Projekts sind

Mit diesen Optionen können Sie die ECMAScript-Version für Dateien auswählen, die nicht Teil eines Projekts sind. Sie können zwischen **ECMAScript 3**, **ECMAScript 5** oder **ECMAScript 6** auswählen.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>JSX-Ausgabe für TSX-Dateien, die nicht Teil eines Projekts sind

Diese Optionen bestimmen, wie der Editor TypeScript-Dateien behandelt, die nicht Teil eines Projekts sind.

### <a name="uielement-list"></a>UIElement-Liste

|Option|Beschreibung|
|------------|-----------------|
|**React-Framework**|Wenn diese Option aktiviert ist, gibt der Code-Editor eine *JS*-Dateierweiterung aus.|
|**Preserve**|Wenn diese Option ausgewählt ist, behält der Code-Editor das JSX als Teil der Ausgabe bei und sendet eine *JSX*-Dateierweiterung.|

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)