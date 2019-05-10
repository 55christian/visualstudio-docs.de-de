---
title: Bestimmen die Standard-Namespace eines Projekts | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 0bc5cba2651f447e36491c641e9b0d05f728e5c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822580"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Ermitteln des Standardnamespaces eines Projekts
Für [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], wenn die `CustomToolNamespace` Eigenschaft wird festgelegt, auf die Eingabedatei, klicken Sie dann den Wert der `CustomToolNamespace` wird der Wert, der der Namespace-Standardparameter, die an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> Methode. Andernfalls die `wszDefaultNamespace` übergebene Parameter `Generate` ist immer gleich den Stamm-Namespace. Weitere Informationen zu Namespaces finden Sie unter [Namespace Schlüsselwörter](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] werden ordnerbasierten Namespace verwendet. Der Namespace besteht, also den Stamm-Namespace sowie die Namen von Ordnern, die das benutzerdefinierte Tool enthält. Ordnernamen weisen in ein gültiger Bezeichner konvertiert, und Punkte trennen Sie alle Namen. Z. B. wenn die Eingabedatei FolderA\FolderB\FolderC\MyInput.txt ist und der Stamm-Namespace CL9 ist, klicken Sie dann der berechneten Standardnamespace wäre **CL9. FolderA.FolderB.FolderC**.  
  
 Eine Ausnahme von dieser Regel tritt auf, wenn der Hierarchiekette Ordner für Webverweise enthält. Z. B. wenn:  
  
- FolderC wurden Ordner für Webverweise, der Namespace **CL9. FolderC**.  
  
- FolderB wurden Ordner für Webverweise, der Namespace **CL9. FolderB.FolderC**.  
  
  Der Namespace verwendet, also das folgende Format:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Einzeldatei-Generatoren](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrieren von Generatoren einzelner Dateien](../extensibility/internals/registering-single-file-generators.md)   
 [Verfügbarmachen von Typen für visuelle Designer](../extensibility/internals/exposing-types-to-visual-designers.md)