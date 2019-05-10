---
title: Touch-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf68bf5dada310a23136e431fdaecad3e738d4bc
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655542"
---
# <a name="touch-task"></a>Touch-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Legt den Zugriff und den Änderungszeitpunkt für Dateien fest  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `Touch` -Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`AlwaysCreate`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, werden Dateien erstellt, die noch nicht vorhanden sind|  
|`Files`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die hinzuzufügende Dateiauflistung an|  
|`ForceTouch`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, wird eine Dateiänderung erzwungen, auch wenn die Dateien schreibgeschützt sind|  
|`Time`|Optionaler `String` -Parameter.<br /><br /> Gibt einen Zeitpunkt an, der sich von der aktuellen Uhrzeit unterscheidet. Das Format muss von der <xref:System.DateTime.Parse%2A>-Methode akzeptiert werden.|  
|`TouchedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Auflistung von Elementen, die erfolgreich bearbeitet wurden|  
  
## <a name="remarks"></a>Anmerkungen  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden mit der `Touch`-Aufgabe der Zugriff und die Zeitpunkte der in der `Files`-Elementauflistung angegebenen Dateien geändert und die Liste der erfolgreich geänderten Dateien in der `FilesTouched`-Elementauflistung platziert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
