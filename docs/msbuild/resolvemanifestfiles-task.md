---
title: ResolveManifestFiles-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ebbc2a036700c26ccd6ca3bec7b235722432e9f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595175"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles-Aufgabe
Löst folgende Elemente im Buildprozess in Dateien für die Manifestgenerierung auf: erstellte Elemente, Abhängigkeiten, Satelliten, Inhalte, Debugsymbole und Dokumentationen

## <a name="parameters"></a>Parameter
 In der folgenden Tabelle werden die Parameter der `ResolveManifestFiles` -Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt den Namen des Bereitstellungsmanifests an|
|`EntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Gibt die verwaltete Assembly oder den ClickOnce-Manifestverweis an, der den Einstiegspunkt für das Manifest darstellt|
|`ExtraFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die zusätzlichen Dateien an|
|`ManagedAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die verwalteten Assemblys an|
|`NativeAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die nativen Assemblys an|
|`OutputAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die generierten Assemblys an|
|`OutputDeploymentManifestEntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt den Einstiegspunkt des Ausgabebereitstellungsmanifests an|
|`OutputEntryPoint`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Ausgabeparameter.<br /><br /> Gibt den Ausgabeeinstiegspunkt an|
|`OutputFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die Ausgabedateien an|
|`PublishFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Veröffentlichungsdateien an|
|`SatelliteAssemblies`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Satellitenassemblys an|
|`SigningManifests`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, werden die ClickOnce-Manifeste signiert|
|`TargetCulture`|Optionaler `String`-Parameter.<br /><br /> Gibt die Zielkultur für Satellitenassemblys an|
|`TargetFrameworkVersion`|Optionaler `String`-Parameter.<br /><br /> Gibt die .NET Framework-Zielversion an|

## <a name="remarks"></a>Hinweise
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Siehe auch
- [Aufgaben](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
