---
title: Erstellen Sie Webpart für SharePoint, die mit dem designer
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9963c2f7e829e9d295ca254aa651e37e3ad08efd
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401147"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint mithilfe eines Designers

Wenn Sie Webparts für eine SharePoint-Website erstellen, können Benutzer Inhalt, Darstellung und Verhalten der Seiten auf dieser Website direkt mithilfe eines Browsers ändern. In dieser exemplarischen Vorgehensweise erfahren Sie, wie ein Webpart visuell zu erstellen, mit dem SharePoint **visuelles Webpart** Projektvorlage in Visual Studio.

Das erstellte Webpart zeigt eine monatliche Kalenderansicht und ein Kontrollkästchen für jede Kalenderliste auf der Website an. Die Benutzer können angeben, welche Kalenderlisten in die monatliche Kalenderansicht eingeschlossen werden, indem sie die Kontrollkästchen aktivieren.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen ein Webpart mithilfe der **visuelles Webpart** Projektvorlage.
- Entwerfen des Webparts mit dem Visual Web Developer-Designer in Visual Studio
- Hinzufügen von Code, um die Ereignisse der Steuerelemente des Webparts zu behandeln
- Testen des Webparts in SharePoint

    > [!NOTE]
    > Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt, als in den folgenden Anweisungen aufgeführt werden. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Unterstützte Editionen von Windows und SharePoint.

## <a name="create-a-web-part-project"></a>Erstellen eines Webpartprojekts

Erstellen Sie ein Webpartprojekt zunächst mithilfe der **visuelles Webpart** Projektvorlage.

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mithilfe der **als Administrator ausführen** Option.

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

3. In der **neues Projekt** im Dialogfeld unter entweder **Visual C#-** oder **Visual Basic**, erweitern Sie **Office/SharePoint**, und wählen Sie dann die  **SharePoint-Lösungen** Kategorie.

4. Wählen Sie in der Liste der Vorlagen, die **SharePoint 2013 - Visual Web Part** Vorlage, und wählen Sie dann die **OK** Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird. Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe angeben.

5. In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld aus.

6. Wählen Sie die **Fertig stellen** Schaltfläche, um die standardmäßige lokale SharePoint-Website zu akzeptieren.

## <a name="designing-the-web-part"></a>Entwerfen des Webparts

Entwerfen des Webparts durch Hinzufügen von Steuerelementen aus der **Toolbox** auf die Oberfläche des Visual Web Developer-Designer.

1. Wählen Sie auf dem Visual Web Developer-Designer die **Entwurf** Registerkarte, um zur Entwurfsansicht zu wechseln.

2. Wählen Sie in der Menüleiste **Ansicht** > **Toolbox** aus.

3. In der **Standard** Knoten die **Toolbox**, wählen Sie die **"CheckBoxList"** steuern, und führen Sie die folgenden Schritte aus:

    - Öffnen Sie das Kontextmenü für die **"CheckBoxList"** steuern, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für die erste Zeile im Designer, und wählen Sie dann **einfügen**.

    - Ziehen Sie die **"CheckBoxList"** -Steuerelement aus der **Toolbox**, und verbinden Sie das Steuerelement, mit der ersten Zeile im Designer.

4. Wiederholen Sie den vorherigen Schritt, aber verschieben Sie eine Schaltfläche in die nächste Zeile des Designers.

5. Wählen Sie im Designer die **"Button1"** Schaltfläche.

6. Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"** .

     Die **Eigenschaften** Fenster wird geöffnet.

7. In der **Text** -Eigenschaft der Schaltfläche, geben Sie **Update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Behandeln der Ereignisse von Steuerelementen des Webparts

Fügen Sie Code hinzu, der es dem Benutzer ermöglicht, der Masterkalenderansicht Kalender hinzuzufügen.

1. Führen Sie einen der folgenden Schritte aus:

   - Doppelklicken Sie im Designer auf die **Update** Schaltfläche.

   - In der **Eigenschaften** Fenster für die **Update** Schaltfläche der **Ereignisse** Schaltfläche. In der **klicken Sie auf** -Eigenschaft, geben Sie **Button1_Click**, und wählen Sie dann die EINGABETASTE.

     Die Benutzersteuerelement-Codedatei wird im Code-Editor geöffnet, und der `Button1_Click`-Ereignishandler wird angezeigt. Später fügen Sie Code an diesen Ereignishandler.

2. Fügen Sie am Anfang der Benutzersteuerelement-Codedatei die folgenden Anweisungen hinzu.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Fügen Sie der `VisualWebPart1`-Klasse folgende Codezeile hinzu. In diesem Code wird ein monatliches Kalenderansichtssteuerelement deklariert.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Ersetzen Sie die `Page_Load`-Methode der `VisualWebPart1`-Klasse durch folgenden Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

   - Fügt dem Benutzersteuerelement eine monatliche Kalenderansicht hinzu.

   - Fügt ein Kontrollkästchen für jede Kalenderliste der Website hinzu.

   - Gibt eine Vorlage für jeden Typ von Element an, das in der Kalenderansicht angezeigt wird.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Ersetzen Sie die `Button1_Click`-Methode der `VisualWebPart1`-Klasse durch folgenden Code. Mit diesem Code werden der Masterkalenderansicht Elemente aus jedem ausgewählten Kalender hinzugefügt.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Testen Sie das Webpart

Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet. Das Webpart wird automatisch dem Webpartkatalog in SharePoint hinzugefügt. Um dieses Projekt zu testen, müssen Sie die folgenden Aufgaben ausführen:

- Fügen Sie jeder von zwei separaten Kalenderlisten ein Ereignis hinzu.
- Fügen Sie das Webpart einer Webpartseite hinzu.
- Geben Sie die Listen an, die in die monatliche Kalenderansicht eingeschlossen werden sollen.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>So fügen Sie Kalenderlisten der Website Ereignisse hinzu

1. Wählen Sie in Visual Studio die **F5** Schlüssel.

     Die SharePoint-Website geöffnet wird, und die [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] Schnellstartleiste auf der Seite angezeigt.

2. Klicken Sie auf der Schnellstartleiste unter **listet**, wählen Sie die **Kalender** Link.

     Die **Kalender** Seite wird angezeigt.

     Wenn Sie keine Link "Kalender" auf der Schnellstartleiste angezeigt wird, wählen Sie die **Websiteinhalte** Link. Wenn die Seite "Websiteinhalte" nicht angezeigt wird eine **Kalender** Element, erstellen Sie eine.

3. Klicken Sie auf der Seite "Kalender", wählen Sie ein Tag aus, und wählen Sie dann die **hinzufügen** -Link in der ausgewählten Tag ein Ereignis hinzuzufügen.

4. In der **Titel** geben **Ereignis in den Standardkalender**, und wählen Sie dann die **speichern** Schaltfläche.

5. Wählen Sie die **Websiteinhalte** verknüpfen, und wählen Sie dann die **fügen Sie eine app** Kachel.

6. Auf der **erstellen** Seite die **Kalender** geben, benennen Sie den Kalender, und wählen Sie dann die **erstellen** Schaltfläche.

7. Fügen Sie ein Ereignis an den neuen Kalender, benennen Sie das Ereignis **Ereignis im benutzerdefinierten Kalender**, und wählen Sie dann die **speichern** Schaltfläche.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>So fügen Sie das Webpart einer Webpartseite hinzu

1. Auf der **Websiteinhalte** öffnen die **Websiteseiten** Ordner.

2. Wählen Sie auf dem Menüband der **Dateien** Registerkarte Öffnen der **neues Dokument** Menü und wählen Sie dann die **Clientwebpart-Seite** Befehl.

3. Auf der **neue Webpartseite** Seite, nennen Sie die Seite **SampleWebPartPage.aspx**, und wählen Sie dann die **erstellen** Schaltfläche.

     Die Webpartseite wird angezeigt.

4. Wählen Sie im oberen Bereich der Webpartseite, die **einfügen** Registerkarte, und wählen Sie dann die **Webpart** Schaltfläche.

5. Wählen Sie die **benutzerdefinierte** Ordner, wählen Sie die **VisualWebPart1** -Webpart, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Das Webpart wird auf der Seite angezeigt. Die folgenden Steuerelemente werden für das Webpart angezeigt:

    - Eine monatliche Kalenderansicht.

    - Ein **Update** Schaltfläche.

    - Ein **Kalender** Kontrollkästchen.

    - Ein **benutzerdefinierter Kalender** Kontrollkästchen.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>So geben Sie die Listen an, die in die monatliche Kalenderansicht eingeschlossen werden sollen

Geben Sie im Webpart Kalender, die Sie verwenden möchten, in die monatliche Kalenderansicht einschließen, und wählen Sie dann die **Update** Schaltfläche.

Die Ereignisse aus allen angegebenen Kalendern werden in der monatlichen Kalenderansicht angezeigt.

## <a name="see-also"></a>Siehe auch

[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
[Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)
[Exemplarische Vorgehensweise: Erstellen Sie ein Webpart für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
