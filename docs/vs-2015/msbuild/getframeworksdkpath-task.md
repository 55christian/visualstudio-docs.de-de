---
title: GetFrameworkSdkPath-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d527b00e8cbfe6a6f4ad5d112a23e46d4edb8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149567"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ruft den Pfad zu [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] ab  
  
## <a name="task-parameters"></a>Aufgabenparameter  
 In der folgenden Tabelle werden die Parameter der `GetFrameworkSdkPath`-Aufgabe beschrieben.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 2.0 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|  
|`FrameworkSdkVersion35Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 3.5 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|  
|`FrameworkSdkVersion40Path`|Optionaler schreibgeschützter `String`-Parameter<br /><br /> Gibt den Pfad zum .NET SDK-Version 4.0 zurück, falls vorhanden Andernfalls wird `String.Empty` zurückgegeben.|  
|`Path`|Optionaler `String`-Ausgabeparameter.<br /><br /> Enthält den Pfad zum neuesten .NET SDK, wenn eine Version vorhanden ist. Andernfalls wird `String.Empty` zurückgegeben.|  
  
## <a name="remarks"></a>Anmerkungen  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird mit der Aufgabe `GetFrameworkSdkPath` der Pfad zu [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] in der `SdkPath`-Eigenschaft gespeichert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
