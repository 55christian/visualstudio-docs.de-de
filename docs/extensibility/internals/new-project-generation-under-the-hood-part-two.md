---
title: 'Neue Projektgenerierung: In die Hintergründe, Teil 2 | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ccdd4cd8bafc4bc4a899ea47d62ec10e578569c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909322"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>Neue Projektgenerierung: Einblick in die Hintergründe, Teil 2

In [Generieren neuer Projekte: In die Hintergründe, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) erläutert, wie die **neues Projekt** Dialogfeld Feld wird gefüllt. Angenommen, Sie haben ausgewählt eine **Visual C#-Windows-Anwendung**, ausgefülltes der **Namen** und **Speicherort** Textfelder, und klicken auf OK.

## <a name="generating-the-solution-files"></a>Zum Erstellen der Projektmappendateien
 Auswählen einer Anwendungsvorlage leitet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entzippen und öffnen die entsprechende VSTEMPLATE-Datei, und starten Sie eine Vorlage, um die XML-Befehle in dieser Datei zu interpretieren. Diese Befehle erstellen Projekte und Projektelemente in der neuen oder vorhandenen Projektmappe ein.

 Die Vorlage entpackt Quelldateien namens Elementvorlagen, aus dem gleichen ZIP-Ordner, der die VSTEMPLATE-Datei enthält. Die Vorlage übernimmt diese Dateien in das neue Projekt, und sie entsprechend anpassen.

### <a name="template-parameter-replacement"></a>Vorlage Parameter ersetzt
 Wenn die Vorlage eine Item-Vorlage in ein neues Projekt kopiert, ersetzt Vorlagenparameter durch Zeichenfolgen zum Anpassen der das. Ein Vorlagenparameter ist eine spezielle Token, das vorangestellt ist, und ein Dollarzeichen gefolgt sind, z. B. $date$.

 Betrachten Sie eine typische Projektelementvorlage aus. Extrahieren Sie und untersuchen Sie die Datei "Program.cs" im Ordner "Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip".

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

Wenn Sie ein neues Windows-Anwendungsprojekt mit dem Namen einfach erstellen, die Vorlage ersetzt die `$safeprojectname$` Parameter mit dem Namen des Projekts.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../../ide/template-parameters.md).

## <a name="a-look-inside-a-vstemplate-file"></a>Ein Einblick in ein. VSTemplate-Datei
 Eine einfache VSTEMPLATE-Datei weist Folgendes Format auf

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 Wir haben uns über die \<TemplateData > im Abschnitt der [Generieren neuer Projekte: In die Hintergründe, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). Die in diesem Abschnitt werden verwendet, um die Darstellung der steuern die **neues Projekt** Dialogfeld.

 Die Tags in der \<TemplateContent > im Abschnitt Steuerelement der Generierung von neuen Projekten und Projektelementen. Hier ist die \<TemplateContent > aus der cswindowsapplication.vstemplate-Datei im Ordner "\Programme\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip".

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 Die \<Projekt >-Tag steuert die Generierung von ein Projekt, und die \<ProjectItem > Tag steuert die Generierung eines Projektelements. Wenn der Parameter ReplaceParameters auf "true" festgelegt ist, wird die Vorlage alle Vorlagenparameter in der Projektdatei oder das Element anpassen. In diesem Fall werden alle Projektelemente, mit Ausnahme von Settings.settings angepasst.

 Der TargetFileName-Parameter gibt den Namen und den relativen Pfad der resultierende Projektdatei oder des Elements. Dadurch können Sie eine Ordnerstruktur für das Projekt zu erstellen. Wenn Sie dieses Argument nicht angeben, müssen das Projektelement den gleichen Namen wie der Projektelementvorlage.

 Windows-Anwendung Ordnerstruktur sieht folgendermaßen aus:

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 Die erste und einzige \<Projekt >-Tag in die Vorlage liest:

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 Dies weist die neuen Projektvorlage die Projektdatei Simple.csproj durch Kopieren und Anpassen der Vorlage Element windowsapplication.csproj erstellen.

### <a name="designers-and-references"></a>Designer und Verweise
 Sie können im Projektmappen-Explorer sehen, dass der Ordner "Properties" vorhanden ist und die erwarteten Dateien enthält. Aber wie sieht es mit Projekt verweist, und Designer-dateiabhängigkeiten, z. B. "Resources.Designer.cs", "Resources.resx" und "Form1.Designer.cs" auf "Form1.cs"?  Diese werden in der Datei Simple.csproj eingerichtet, wenn sie erstellt wird.

 Hier ist die \<ItemGroup > von Simple.csproj, die die Projektverweisen erstellt:

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 Sie können sehen, dass diese die sechs Projektverweise, die im Projektmappen-Explorer angezeigt werden. Hier ist ein Abschnitt von einem anderen \<ItemGroup >. Viele Codezeilen wurden aus Gründen der Übersichtlichkeit gelöscht. In diesem Abschnitt werden die Settings.Designer.cs Settings.settings abhängig:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Siehe auch

- [Neue Projektgenerierung: Einblick in die Hintergründe, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)