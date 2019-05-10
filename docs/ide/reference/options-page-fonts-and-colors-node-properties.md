---
title: Optionsseite, Eigenschaften des Knotens "Schriftarten und Farben"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5363d71082128c13146c445fe312424be7e4340
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945593"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Optionsseite, Eigenschaften des Knotens "Schriftarten und Farben"
Dieses Dokument beschreibt die Eigenschaften der Schriftarten und Farben für ein Toolfenster, das unter **Schriftarten und Farben** in der Kategorie **Umgebung** des Dialogfelds **Optionen** registriert ist. Dadurch wird die Dynamik von Gruppen von einfärbbaren Elementen unterstützt, die sich ändern kann, wenn VSPackages installiert oder deinstalliert werden.

 Im folgenden Bereich wird ein Beispiel für einen registrierten Fenstertyp und die für jedes Fenster verfügbaren Eigenschaften besprochen.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Text-Editor oder Drucker oder Dialogfelder oder Toolfenster
 `DTE.Properties("FontsAndColors", "TextEditor")`

 -oder- 

 `DTE.Properties("FontsAndColors", "Printer")`

 - oder - 

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Eigenschaftenelementname|Wert|Beschreibung|
| - |-----------|-----------------|
|FontFamily|Get/Set (Zeichenfolge)|Der zu verwendende Name einer Schriftart, z.B. „Courier New.“|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Ein <xref:EnvDTE.vsFontCharSet>-Wert, der den Typ des zu verwendenden Zeichensatzes angibt, z.B. Hebräisch oder Russisch.|
|FontSize|Get/Set (kurzer Name)|Die zu verwendende Schriftgröße in Punkten. Beispielsweise 10 oder 12.|

## <a name="see-also"></a>Siehe auch

- [Steuern der Einstellungen im Dialogfeld „Optionen“](https://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Bestimmen der Namen von Eigenschaftenelementen auf Optionsseiten](https://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Seite „Optionen“, Eigenschaften des Knotens „Umgebung“](../../ide/reference/options-page-environment-node-properties.md)
- [Optionsseite, Eigenschaften des Knotens „Text-Editor“](../../ide/reference/options-page-text-editor-node-properties.md)