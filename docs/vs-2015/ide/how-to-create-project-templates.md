---
title: 'Vorgehensweise: Erstellen von Projektvorlagen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5a43fe714028b7211904a0bb993d2964bfe612ce
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416918"
---
# <a name="how-to-create-project-templates"></a>Vorgehensweise: Erstellen von Projektvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Vorgehensweise ermöglicht Ihnen das Erstellen einer Vorlage mithilfe des **Assistenten zum Exportieren von Vorlagen**, bei dem Ihre Vorlage in einer ZIP-Datei verpackt wird. Sie können für eine verbesserte Bereitstellung auch Vorlagen im Dateiformat VSIX erstellen, indem Sie die Erweiterung des „Assistenten zum Exportieren von Vorlagen“ oder Vorlagen verwenden, die in [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] enthalten sind. Außerdem können Sie Vorlagen manuell erstellen.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>So erstellen Sie eine benutzerdefinierte Projektvorlage mit dem Standard-Assistenten zum Exportieren von Vorlagen  
  
1. Erstellen eines Projekts.  
  
    > [!NOTE]
    > Verwenden Sie nur gültige Bezeichnerzeichen beim Benennen eines Projekts, das als Quelle für eine Vorlage verwendet wird. Eine aus einem Projekt exportierte Vorlage, das mit ungültigen Zeichen benannt wurde, kann in zukünftigen Projekten, die auf dieser Vorlage basieren, Kompilierungsfehler verursachen. Weitere Informationen zu gültigen Bezeichnerzeichen finden Sie unter [Declared Element Names (Namen deklarierter Elemente)](http://msdn.microsoft.com/library/09d8843b-c0dc-4afe-9dab-87c439a69e66).  
  
2. Bearbeiten Sie das Projekt solange, bis es als Vorlage exportiert werden kann.  
  
3. Ändern Sie gegebenenfalls die Codedateien, um anzugeben, an welcher Stelle Parameterersetzungen stattfinden sollen. Weitere Informationen zu parameterersetzungen finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4. Klicken Sie im Menü **Datei** auf **Vorlage exportieren**. Der **Assistent zum Exportieren von Vorlagen** wird geöffnet.  
  
5. Klicken Sie auf **Projektvorlage**.  
  
6. Wenn sich in Ihrer aktuellen Projektmappe mehr als ein Projekt befindet, müssen Sie das Projekt auswählen, das Sie als Vorlage exportieren möchten.  
  
7. Klicken Sie auf **Weiter**.  
  
8. Wählen Sie ein Symbol und ein Vorschaubild für die Vorlage aus. Diese werden im Dialogfeld **Neues Projekt** angezeigt.  
  
9. Geben Sie einen Namen und eine Beschreibung für die Vorlage ein.  
  
10. Klicken Sie auf **Fertig stellen**. Das Projekt wird als ZIP-Datei exportiert und am angegebenen Speicherort platziert. Außerdem wird es in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] importiert, wenn diese Option ausgewählt wurde.  
  
     Wenn [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] installiert ist, können Sie die fertige Vorlage für die Bereitstellung in einer VSIX-Datei umschließen, indem Sie die Vorlage **VSIX-Projekt** verwenden. Weitere Informationen finden Sie unter [Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorgehensweise: Create Item Templates (Vorgehensweise: Erstellen von Elementvorlagen)](../ide/how-to-create-item-templates.md)
