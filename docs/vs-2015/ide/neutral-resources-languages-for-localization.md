---
title: Neutrale Ressourcensprachen für die Lokalisierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da39ed9373daaa1dbef21ad36931ce97ea1f1e1b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558267"
---
# <a name="neutral-resources-languages-for-localization"></a>Neutrale Ressourcensprachen für die Lokalisierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Klasse <xref:System.Resources.NeutralResourcesLanguageAttribute> gibt die Kultur der Ressourcen an, die in der Hauptassembly enthalten sind. Mit diesem Attribut wird die Leistung optimiert, sodass das <xref:System.Resources.ResourceManager>-Objekt nicht nach Ressourcen sucht, die in der Hauptassembly enthalten sind.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie neutrale Sprachressourcen festgelegt werden. Der Code kann in ein Buildskript, die AssemblyInfo.vb-Datei oder die AssemblyInfo.cs-Datei eingefügt werden.  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Resources.ResourceManager>   
 [Einführung in internationale Anwendungen basierend auf .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Hierarchische Organisation der Ressourcen für die Lokalisierung](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
