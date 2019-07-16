---
title: 'Vorgehensweise: Erstellen einer Aktivitätsbibliothek | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9463e46a7341a7da5c4aa79ae477d6aa0ff0c6cc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686645"
---
# <a name="how-to-create-an-activity-library"></a>Vorgehensweise: Erstellen einer Aktivitätsbibliothek
Benutzerdefinierte Aktivitäten werden verwendet, um bestimmte Geschäftsprozesse in einem Workflow zu modellieren. Die Vorlage Aktivitätsbibliothek in [!INCLUDE[vs2010](../includes/vs2010-md.md)] wurde bereitgestellt, damit Sie solche benutzerdefinierten Aktivitäten visuell mithilfe von [!INCLUDE[wfd1](../includes/wfd1-md.md)] erstellen können.  
  
### <a name="to-create-a-workflow-activity-library"></a>So erstellen Sie eine Workflowaktivitätsbibliothek  
  
1. Starten Sie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Auf der **Datei** Startmenü **neu**, und wählen Sie dann **Projekt...** .  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3. In der **Projekttypen** wählen Sie im Bereich **Workflow** entweder die **Visual C#-** Projekte oder **Visual Basic** Gruppierungen je Ihre Bevorzugte Sprache.  
  
4. In der **Vorlagen** wählen Sie im Bereich **Aktivitätsbibliothek**.  
  
5. In der **Namen** Feld Geben Sie einen beschreibenden Namen für Ihr Projekt, das es einfach identifizieren zu können.  
  
6. In der **Speicherort** den Suchbegriff in das Verzeichnis, in dem Sie das Projekt speichern, oder klicken Sie auf möchten **Durchsuchen** dorthin navigieren.  
  
7. In der **Lösung** , geben Sie einen beschreibenden Namen für die Projektmappe, und klicken Sie dann **OK**.  
  
    > [!NOTE]
    > Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in [!INCLUDE[vs2010](../includes/vs2010-md.md)], klicken Sie mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, klicken Sie dann  **Neues Projekt...** zum Öffnen der **neues Projekt** Dialogfeld. Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8. Die Projektvorlage erstellt eine Aktivitätsdefinition im XAML-Format. [!INCLUDE[wfd1](../includes/wfd1-md.md)] wird geöffnet und zeigt den Zeichenbereich für die benutzerdefinierte Aktivität an.  
  
9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfsoberfläche, um sie in Ihre benutzerdefinierte Aktivität aufzunehmen.  
  
    > [!CAUTION]
    > Sie können nur eine untergeordnete Aktivität dem Text der benutzerdefinierten Aktivität hinzufügen. Diese untergeordnete Aktivität kann jedoch eine zusammengesetzte Aktivität sein, z. B. eine <xref:System.Activities.Statements.Sequence>-Aktivität oder <xref:System.Activities.Statements.Flowchart>-Aktivität.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen einer Aktivität](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)