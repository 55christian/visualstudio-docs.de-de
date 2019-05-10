---
title: MSBuild-Aufgaben | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90b6731cf75a1825139aba57fe8491cd7cb0253f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004560"
---
# <a name="msbuild-tasks"></a>MSBuild-Aufgaben
Eine Buildplattform muss während des Buildprozesses eine beliebige Anzahl von Aktionen auszuführen können. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verwendet dazu *Aufgaben*. Eine Aufgabe ist eine Einheit von ausführbarem Code, der von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verwendet wird, um atomische Buildoperationen auszuführen.

## <a name="task-logic"></a>Aufgabenlogik
 Das XML-Projektdateiformat von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] kann Buildoperationen selbst nicht vollständig ausführen. Daher muss die Aufgabenlogik außerhalb der Projektdatei implementiert werden.

 Die Ausführungslogik einer Aufgabe wird als .NET-Klasse implementiert, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert, die im <xref:Microsoft.Build.Framework>-Namespace definiert ist.

 Die Aufgabenklasse definiert darüber hinaus die für eine Aufgabe in der Projektdatei verfügbaren Eingabe- und Ausgabeparameter. Auf alle konfigurierbaren öffentlichen nicht statischen und nicht abstrakten Eigenschaften, die von der Aufgabenklasse verfügbar gemacht werden, kann in der Projektdatei zugegriffen werden, indem ein entsprechendes Attribut mit demselben Namen auf dem [Aufgabe](../msbuild/task-element-msbuild.md)-Element platziert wird.

 Sie können eine eigene Aufgabe schreiben, indem Sie eine verwaltete Klasse erstellen, die die <xref:Microsoft.Build.Framework.ITask>-Schnittstelle implementiert. Weitere Informationen finden Sie unter [Schreiben von Aufgaben](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Ausführen einer Aufgabe aus einer Projektdatei
 Vor dem Ausführen einer Aufgabe in der Projektdatei müssen Sie zuerst den Typ in der Assembly zuordnen, der die Aufgabe mithilfe des Elements [UsingTask](../msbuild/usingtask-element-msbuild.md) in den Aufgabennamen implementiert. Auf diese Weise kann [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] erkennen, wo sich die Ausführungslogik der Aufgabe befindet, wenn es sie in der Projektdatei findet.

 Erstellen Sie ein Element mit dem Namen der Aufgabe als untergeordnetes Element eines `Target`-Elements, um eine Aufgabe in einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdatei auszuführen. Wenn eine Aufgabe Parameter akzeptiert, werden diese als Attribute des Elements übergeben.

 Als Parameter können Eigenschaften und Elementlisten von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verwendet werden. Der folgende Code erstellt z.B. die `MakeDir`-Aufgabe und legt für die `Directories`-Eigenschaft des `MakeDir`-Objekts denselben Wert fest, der im vorherigen Beispiel auch für die `BuildDir`-Eigenschaft deklariert wurde.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Aufgaben können zudem Informationen an die Projektdatei zurückgeben, die für die spätere Verwendung in Elementen oder Eigenschaften gespeichert werden können. Der folgende Code ruft z.B. die `Copy`-Aufgabe auf und speichert die Informationen aus der `CopiedFiles`-Ausgabeeigenschaft in der `SuccessfullyCopiedFiles`-Elementliste.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>Verfügbare Aufgaben
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bietet zahlreiche Aufgaben wie z.B. [Copy](../msbuild/copy-task.md) zum Kopieren von Dateien, [MakeDir](../msbuild/makedir-task.md) zum Erstellen von Verzeichnissen und [Csc](../msbuild/csc-task.md) zum Kompilieren von [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Quellcodedateien. Eine vollständige Liste der verfügbaren Aufgaben sowie Nutzungsinformationen finden Sie unter [Aufgabenreferenz](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Überschriebene Aufgaben
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sucht in mehreren Speicherorten nach Aufgaben. Beim ersten Speicherort handelt es sich um Dateien mit der Erweiterung *.OverrideTasks*, die in den .NET Framework-Verzeichnissen gespeichert sind. Aufgaben in diesen Dateien überschreiben alle anderen Aufgaben mit denselben Namen, einschließlich Aufgaben in der Projektdatei. Beim zweiten Speicherort handelt es sich um Dateien mit der Erweiterung *.Tasks*, die in den .NET Framework-Verzeichnissen gespeichert sind. Wird die Aufgabe in keinem dieser beiden Speicherorte gefunden, so wird die Aufgabe in der Projektdatei verwendet.

## <a name="see-also"></a>Siehe auch
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Schreiben von Aufgaben](../msbuild/task-writing.md)
- [Inlineaufgaben](../msbuild/msbuild-inline-tasks.md)