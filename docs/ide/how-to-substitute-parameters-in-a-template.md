---
title: Hinzufügen von Namensparametern zu Projekt- und Elementvorlagen
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- template parameters
- template parameters, substituting
- Visual Studio templates, using parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9ddfe065d30b958e52e22f30f946d01d626fcf0e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591410"
---
# <a name="how-to-substitute-parameters-in-a-template"></a>Vorgehensweise: Ersetzen von Parametern in einer Vorlage

Mithilfe von Vorlagenparametern können Sie Bezeichner wie Klassennamen und Namespaces ersetzen, wenn Sie eine Datei auf Basis einer Vorlage erstellen. Sie können Vorlagenparameter zu vorhandenen Vorlagen hinzufügen oder Ihre eigene Vorlage mithilfe von Vorlagenparametern erstellen.

Vorlagenparameter werden im Format $*Parameter*$ geschrieben. Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).

Im folgenden Abschnitt wird erläutert, wie Sie eine Vorlage ändern, um den Namen eines Namespaces durch den „sicheren Projektnamen“ zu ersetzen.

## <a name="example---namespace-name"></a>Beispiel: Namespacename

1. Fügen Sie den Parameter in eine oder mehrere Codedateien in der Vorlage ein. Zum Beispiel:

    ```csharp
    namespace $safeprojectname$
    ```

1. Suchen Sie in der *VSTEMPLATE*-Datei der Vorlage nach dem `ProjectItem`-Element, in dem diese Datei enthalten ist.

1. Legen Sie das `ReplaceParameters`-Attribut für das `ProjectItem`-Element auf `true` fest:

    ```xml
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>
    ```

## <a name="see-also"></a>Siehe auch

- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [ProjectItem-Element (Visual Studio-Projektelementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)
