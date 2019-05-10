---
title: 'Vorgehensweise: Erstellen ein SharePoint-Webparts mithilfe eines Designers | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 354fe62914a8708ac63acdde7d30060aca8d52fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966822"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Vorgehensweise: Erstellen Sie ein SharePoint-Webpart mithilfe eines Designers
  Sie können ein Webpart erstellen, durch das Hinzufügen einer **visuelles Webpart** Element, das einem SharePoint-Projekt. Dadurch wird der Visual Web Developer-Designer in Visual Studio geöffnet, in dem Sie Steuerelemente und Code zum Webpart hinzufügen können. Visuelle Webparts funktionieren genauso wie Webparts. Der einzige Unterschied ist, dass Sie visuelle Webparts im Visual Web Developer-Designer entwerfen.

### <a name="to-create-a-project-for-visual-web-parts"></a>So erstellen Sie ein Projekt für visuelle Webparts

1. Klicken Sie in der Menüleiste auf **Datei** >**Neu** > **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2. In der **neues Projekt** im Dialogfeld unter entweder **Visual C#**  oder **Visual Basic**, erweitern Sie die **Office/SharePoint** Knoten, und klicken Sie dann Wählen Sie die **SharePoint-Lösungen** Kategorie.

3. Wählen Sie in der Liste der Projektvorlagen das Projekt **SharePoint 2013 - Visual Web Part**, und wählen Sie dann die **OK** Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird.

4. Auf der **Geben Sie die Website und Sicherheitsebene für debugging** Seite Geben Sie die URL der SharePoint-Website, die auf dem lokalen Computer befindet, und wählen Sie dann die **Fertig stellen** Schaltfläche.

     In **Projektmappen-Explorer**, ein Webpart wird angezeigt. Nach dem Entwerfen des Webparts in Visual Web Developer-Designer, werden Sie sie auf der Website testen, die Sie angeben.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>So fügen Sie einem vorhandenen SharePoint-Projekt ein visuelles Webpart hinzu

1. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

2. In der **neues Element hinzufügen** Dialogfeld auf die **Office/SharePoint** Knoten.

3. Wählen Sie in der Liste der Projektvorlagen das Projekt **visuelles Webpart**, nennen Sie sie aus, und wählen Sie dann die **hinzufügen** Schaltfläche.

     In **Projektmappen-Explorer**, das Webpart wird angezeigt. Nach dem Entwerfen des Webparts in Visual Web Developer-Designer, werden Sie sie auf der Website testen, die Sie angeben.

## <a name="see-also"></a>Siehe auch
- [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint mithilfe eines Designers](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
