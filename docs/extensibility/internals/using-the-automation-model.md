---
title: Über das Automatisierungsmodell | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be793e5cc4db30fa410e0218a7f780b6c2826838
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324596"
---
# <a name="using-the-automation-model"></a>Verwenden des Automatisierungsmodells
Nachdem Sie Ihr VSPackage in Automation verbunden haben, Sie erhalten die Eigenschaften und Methoden durch Aufrufen der <xref:EnvDTE.DTEClass.GetObject%2A> Methode für die <xref:EnvDTE._DTE> Objekts auf und übergibt eine Zeichenfolge, die das Objekt, das Sie abrufen möchten.

## <a name="obtaining-project-objects"></a>Abrufen von Projektobjekten
 Es folgen zwei Codebeispiele, die zeigen, wie ein automatisierungsbenutzer das Projekt Automatisierungsobjekte erhält. Weitere Informationen zum Abrufen des DTE-Objekts, finden Sie unter [Vorgehensweise: Abrufen von Verweisen auf die DTE und DTE2-Objekt](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 An diesem Punkt können Sie die standard-Projekt-Objekte, die Teil eines bestimmten VSPackage, um das Hierarchiemodell zu verschieben.

 Im folgenden Codebeispiel wird veranschaulicht, wie ein benutzerdefiniertes Objekt erhalten, um eine Eigenschaft eines benutzerdefinierten Projekttyps.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Der folgende Code Listet die Namen aller Eigenschaften in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung **allgemeine** option die **Tools** Menü:

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Siehe auch
- <xref:EnvDTE.DTEClass.GetObject%2A>