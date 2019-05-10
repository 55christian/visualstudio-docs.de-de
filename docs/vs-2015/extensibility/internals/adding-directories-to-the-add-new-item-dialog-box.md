---
title: Hinzufügen von Verzeichnissen, die im Dialogfeld Neues Element hinzufügen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958134"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Element hinzufügen“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden Codebeispiel wird veranschaulicht, wie zum Registrieren einer neuen Gruppe von Verzeichnissen, für die **neues Element hinzufügen** Dialogfeld. Verzeichnisse für die **neues Element hinzufügen** Dialogfeld unterscheiden sich für die einzelnen Projekte. Aus diesem Grund werden die Verzeichnisse unter dem projektunterschlüssel, finden Sie im registriert \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>Registrierungsskript  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Der Template_Path-Wert gibt den vollständigen Pfad des Verzeichnisses, das die Projektvorlagen enthält. Diese Vorlagen können entweder VSZ-Dateien oder prototypischen Vorlagendateien zu klonenden sein.  
  
 Der Wert SortPriority gibt es sich um eine Sortierung Priorität.  
  
## <a name="adding-items-to-an-existing-project"></a>Hinzufügen von Elementen zu einem vorhandenen Projekt  
 Sie können auch Elemente zu einem vorhandenen Projekt hinzufügen. Z. B. für eine [!INCLUDE[csprcs](../../includes/csprcs-md.md)] -Projekt können Sie Elemente zum Hinzufügen der \<Stamm > Ordner "\Programme\Microsoft Visual Studio \VC#\CSharpProjectItems\LocalProjectItems". In diesem Fall die `%GUID_Project%` ist die GUID für ein C#-Projekt ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Sie können auch ein vorhandenes Projekt erweitern, indem Sie die Programmierung von einem Projektuntertyp. Mit einem Projektuntertyp können Sie ein Projekt erweitern, ohne einen neuen Projekttyp schreiben zu müssen. Weitere Informationen zu Projektuntertypen, finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Hinzufügen von Elementen, das Hinzufügen neuer Elemente in Dialogfeldern](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Projekt“](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
