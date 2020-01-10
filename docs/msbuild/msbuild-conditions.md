---
title: MSBuild-Bedingungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9576bdf06593ae3cde3bc29e2585a7ab475671a3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566617"
---
# <a name="msbuild-conditions"></a>MSBuild-Bedingungen
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] unterstützt bestimmte Bedingungen, die angewendet werden können, wenn ein `Condition`-Attribut zulässig ist. Diese Bedingungen sind in der folgenden Tabelle angegeben.

|Bedingung|Beschreibung|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|Ergibt `true`, wenn `stringA` gleich `stringB`.<br /><br /> Zum Beispiel:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|
|'`stringA`' != '`stringB`'|Ergibt `true`, wenn `stringA` ungleich `stringB`.<br /><br /> Zum Beispiel:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|
|\<, >, \<=, >=|Wertet die numerischen Werte der Operanden aus. Gibt `true` aus, wenn die relationale Auswertung TRUE ist. Die Auswertung von Operanden muss eine dezimale oder hexadezimale Zahl ergeben. Hexadezimale Zahlen müssen mit „0x“ beginnen. **Hinweis**:  Im XML müssen die Zeichen `<` und `>` mit Escapezeichen versehen werden. Das Symbol `<` wird als `&lt;` dargestellt. Das Symbol `>` wird als `&gt;` dargestellt.|
|Exists('`stringA`')|Ergibt `true`, wenn eine Datei oder ein Ordner mit dem Namen `stringA` vorhanden ist.<br /><br /> Zum Beispiel:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|
|HasTrailingSlash('`stringA`')|Ergibt `true`, wenn die angegebene Zeichenfolge entweder einen nachgestellten umgekehrten Schrägstrich (\\) oder einen Schrägstrich (/) enthält.<br /><br /> Zum Beispiel:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Für einfache alphanumerische Zeichenfolgen und boolesche Werte sind keine einfachen Anführungszeichen erforderlich. Allerdings sind einfache Anführungszeichen für leere Werte erforderlich.|
|!|Ergibt `true`, wenn die Auswertung des Operanden `false` ergibt.|
|Und|Ergibt `true`, wenn die Auswertung beider Operanden `true` ergibt.|
|Oder|Ergibt `true`, wenn die Auswertung von mindestens einem Operanden `true` ergibt.|
|()|Gruppierungsmechanismus, dessen Auswertung `true` ergibt, wenn die Auswertung der darin enthaltenen Ausdrücke `true` ergibt.|
|$if$ ( %expression% ), $else$, $endif$|Überprüft, ob das angegebene `%expression%` dem Zeichenfolgenwert des übergebenen benutzerdefinierten Vorlagenparameters entspricht. Wenn die Auswertung der `$if$`-Bedingung `true` ergibt, werden die jeweiligen Anweisungen ausgeführt. Andernfalls wird die `$else$`-Bedingung überprüft. Wenn die Auswertung der `$else$`-Bedingung `true` ergibt, werden die jeweiligen Anweisungen ausgeführt. Andernfalls beendet die `$endif$`-Bedingung die Auswertung des Ausdrucks.<br /><br /> Anwendungsbeispiele finden Sie unter [Visual Studio project/item template parameter logic (Visual Studio-Projekt: Parameterlogik in Elementvorlagen)](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|

## <a name="see-also"></a>Siehe auch
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [Bedingte Konstrukte](../msbuild/msbuild-conditional-constructs.md)
- [Exemplarische Vorgehensweise: Erstellen einer neuen MSBuild-Projektdatei](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
