---
title: 'Vorgehensweise: Anzeigen einer durch Trennzeichen getrennten Elementliste | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 677278d08e3223f759afc64692481311bfba3356
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596332"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Vorgehensweise: Anzeigen einer durch Trennzeichen getrennten Elementliste
Beim Arbeiten mit dem Elementlisten in [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) ist es manchmal hilfreich, den Inhalt dieser Elementlisten in einer leicht lesbaren Ansicht anzuzeigen. Oder Sie haben eine Aufgabe, die eine Liste von durch ein bestimmtes Trennzeichen getrennten Elementen akzeptiert. In beiden Fällen haben Sie die Möglichkeit, eine Trennzeichenabfolge für eine Elementliste anzugeben.

## <a name="separate-items-in-a-list-with-commas"></a>Trennen von Elementen in einer Liste mit Kommas
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verwendet standardmäßig Semikolons zum Trennen von Elementen in einer Liste. Sehen Sie sich beispielsweise das `Message`-Element mit dem folgenden Wert an:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Wenn die `@(TXTFile)`-Elementliste die Elemente *App1.txt*, *App2.txt* und *App3.txt* enthält, lautet die Meldung:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Wenn Sie das Standardverhalten ändern möchten, können Sie ein eigenes Trennzeichen angeben. Die Syntax eines Trennzeichens für Elementlisten ist:

`@(ItemListName, '<separator>')`

Das Trennzeichen kann ein einzelnes Zeichen oder eine Zeichenfolge sein und muss in einfache Anführungszeichen eingeschlossen werden.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>So fügen Sie ein Komma und ein Leerzeichen zwischen Elementen ein

- Verwenden Sie in etwa diese Elementnotation:

    `@(TXTFile, ', ')`

## <a name="example"></a>Beispiel
In diesem Beispiel führt die Aufgabe [Exec](../msbuild/exec-task.md) das Tool „findstr“ aus, um die angegebenen Textzeichenfolgen in der Datei *Phrases.txt* zu suchen. Im Befehl „findstr“ werden buchstabengetreue Suchzeichenfolgen mit dem Schalter **-c:** gekennzeichnet. Das Elementtrennzeichen `-c:` wird also zwischen Elementen in der `@(Phrase)`-Elementliste eingefügt.

In diesem Beispiel lautet die entsprechende Befehlszeile:

`findstr /i /c:hello /c:world /c:msbuild phrases.txt`

```xml
<Project DefaultTargets = "Find"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <Phrase Include="hello"/>
        <Phrase Include="world"/>
        <Phrase Include="msbuild"/>
    </ItemGroup>

    <Target Name = "Find">
        <!-- Find some strings in a file -->
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Siehe auch
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Elemente](../msbuild/msbuild-items.md)
