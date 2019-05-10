---
title: ResolveNonMSBuildProjectOutput-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aaf99affe9c29762aa8b47ea76419da429089b7c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653618"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bestimmt die Ausgabedateien für Nicht-MSBuild-Projektverweise  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `ResolveNonMSBuildProjectOutput` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Optionaler `String` -Parameter.<br /><br /> Gibt eine XML-Zeichenfolge an, die aufgelöste Projektausgaben enthält|  
|`ProjectReferences`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die Projektverweise an|  
|`ResolvedOutputPaths`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält eine Liste der aufgelösten Verweispfade und behält die ursprünglichen Projektverweisattribute bei|  
|`UnresolvedProjectReferences`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Liste der Projektverweiselemente, die nicht mithilfe der Liste vorab aufgelöster Ausgaben aufgelöst werden konnten<br /><br /> Da Visual Studio nur Nicht-MSBuild-Projekte vorab auflöst, weisen Projektverweise in dieser Liste das MSBuild-Format auf.|  
  
## <a name="remarks"></a>Anmerkungen  
 Zusätzlich zu den in der Tabelle aufgeführten Parametern erbt dieser Task Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
