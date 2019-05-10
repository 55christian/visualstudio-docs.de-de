---
title: 'Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 2 | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1b6477c112de7b19b00bcd173984533f5737014
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436724"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 2
  Nachdem Sie einen benutzerdefinierten Typ des SharePoint-Projektelements definiert und diesen einer Projektvorlage in Visual Studio zugeordnet haben, empfiehlt es sich, außerdem einen Assistenten für die Vorlage bereitzustellen. Mithilfe des Assistenten können Sie Informationen von Benutzern sammeln, während diese Ihre Vorlage verwenden, um ein neues Projekt zu erstellen, das das Projektelement enthält. Mit den gesammelten Informationen kann das Projektelement initialisiert werden.

 In dieser exemplarischen Vorgehensweise fügen Sie einen Assistenten der Projektvorlage für Websitespalten, die gezeigt wird [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Wenn ein Benutzer ein Websitespaltenprojekt erstellt, wird der Assistent sammelt Informationen zur Websitespalte (z. B. Basistyp und Gruppe) und fügt diese Informationen, um die *"Elements.xml"* -Datei in das neue Projekt.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen eines Assistenten für einen benutzerdefinierten SharePoint-Projektelementtyp, dem eine Projektvorlage zugeordnet ist.

- Definieren Sie eine benutzerdefinierte Assistenten-Benutzeroberfläche, die den integrierten Visual Studio-Assistenten für SharePoint-Projekte ähnelt.

- Erstellen zwei *SharePoint-Befehle* , mit denen die in die lokale SharePoint-Website aufrufen, während der Assistent ausgeführt wird. SharePoint-Befehle sind Methoden, mit denen Visual Studio-Erweiterungsassemblys APIs im SharePoint-Serverobjektmodell aufrufen können. Weitere Informationen finden Sie unter [Aufrufe in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Initialisieren von SharePoint-Projektdateien mit im Assistenten gesammelten Daten mithilfe von ersetzbaren Parametern

- Erstellen einer neuen SNK-Datei in jeder neuen Projektinstanz für Websitespalten. Mit dieser Datei wird die Projektausgabe signiert, sodass die SharePoint-Projektmappenassembly im globalen Assemblycache bereitgestellt werden kann.

- Debuggen und Testen des Assistenten

> [!NOTE]
> Eine Reihe von Beispielworkflows, finden Sie unter [Beispiele für die SharePoint-Workflow](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Vorraussetzungen
 Um diese exemplarische Vorgehensweise durchführen zu können, müssen Sie zunächst die Projektmappe SiteColumnProjectItem erstellen, gehen Sie [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer außerdem die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage in das SDK zum Erstellen eines VSIX-Pakets zum Bereitstellen des Projektelements. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Assistenten für Projekt- und Elementvorlagen in Visual Studio. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md) und <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstelle.

- Websitespalten in SharePoint Weitere Informationen finden Sie unter [Spalten](http://go.microsoft.com/fwlink/?LinkId=183547).

## <a name="understand-the-wizard-components"></a>Grundlegendes zu den Assistenten-Komponenten
 Der Assistent, der in dieser exemplarischen Vorgehensweise veranschaulicht wird, enthält mehrere Komponenten. In der folgenden Tabelle werden diese Komponenten beschrieben.

|Komponente|Beschreibung|
|---------------|-----------------|
|Implementieren des Assistenten|Mit der `SiteColumnProjectWizard`-Klasse wird die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle implementiert. Diese Schnittstelle definiert die Methoden, die von Visual Studio aufgerufen werden, wenn der Assistent gestartet wird, wenn der Assistent beendet wird und gelegentlich, während der Assistent ausgeführt wird.|
|Benutzeroberfläche des Assistenten|Dies ist ein WPF-basiertes Fenster mit dem Namen `WizardWindow`. Dieses Fenster enthält zwei Benutzersteuerelemente: `Page1` und `Page2`. Diese Benutzersteuerelemente stellen die beiden Seiten des Assistenten dar.<br /><br /> In dieser exemplarischen Vorgehensweise wird die Benutzeroberfläche des Assistenten von der <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>-Methode der diesbezüglichen Implementierung dargestellt.|
|Datenmodell des Assistenten|Hierbei handelt es sich um die Vermittlerklasse `SiteColumnWizardModel`, die eine Ebene zwischen der Benutzeroberfläche und der Implementierung des Assistenten bereitstellt. In diesem Beispiel wird mithilfe der Klasse eine Abstrahierung zwischen der Implementierung und der Benutzeroberfläche des Assistenten vorgenommen. Diese Klasse ist keine erforderliche Komponenten von Assistenten.<br /><br /> In dieser exemplarischen Vorgehensweise wird von der Implementierung des Assistenten beim Anzeigen der entsprechenden Benutzeroberfläche `SiteColumnWizardModel`-Objekt an das Fenster des Assistenten übergeben. Die Methoden dieses Objekts dienen der Benutzeroberfläche des Assistenten zum Speichern der Werte von Steuerelementen in der Benutzeroberfläche sowie zum Durchführen von Aufgaben wie die Validierung der eingegebenen Website-URL. Nachdem der Assistent vom Benutzer beendet wurde, wird der abschließende Zustand der Benutzeroberfläche von der Implementierung des Assistenten mit dem `SiteColumnWizardModel`-Objekt bestimmt.|
|Projektsignierungs-Manager|Mit der Hilfsklasse `ProjectSigningManager` wird von der Implementierung des Assistenten eine neue key.snk-Datei in jeder neuen Projektinstanz erstellt.|
|SharePoint-Befehle|Mit diesen Methoden werden vom Datenmodell des Assistenten während der Ausführung des Assistenten Aufrufe in die lokale SharePoint-Website durchgeführt. Da SharePoint-Befehle .NET Framework 3.5 zum Ziel haben müssen, werden diese Befehle in einer anderen Assembly als der übrige Code des Assistenten implementiert.|

## <a name="create-the-projects"></a>Erstellen Sie die Projekte
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie mehrere Projekte der Projektmappe SiteColumnProjectItem hinzufügen, die Sie in erstellt [Exemplarische Vorgehensweise: Erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Ein WPF-Projekt. In diesem Projekt implementieren Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle, und Sie definieren die Assistenten-Benutzeroberfläche.

- Ein Klassenbibliotheksprojekt, mit dem die benutzerdefinierten SharePoint-Befehle definiert werden. Für dieses Projekt muss .NET Framework 3.5 als Zielversion verwendet werden.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-wpf-project"></a>So erstellen Sie das WPF-Projekt

1. Öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Projektmappe "SiteColumnProjectItem".

2. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SiteColumnProjectItem** Knoten "Projektmappe", wählen Sie **hinzufügen**, und wählen Sie dann **neues Projekt**.

3. Am oberen Rand der **neues Projekt hinzufügen** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** wird in der Liste der Versionen von .NET Framework ausgewählt.

4. Erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten, und wählen Sie die **Windows** Knoten.

5. Wählen Sie in der Liste der Projektvorlagen das Projekt **WPF-Benutzersteuerelementbibliothek**, nennen Sie das Projekt **ProjectTemplateWizard**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **ProjectTemplateWizard** -Projekt zur Projektmappe und öffnet die Standarddatei "UserControl1.xaml".

6. Löschen Sie die Datei UserControl1.xaml aus dem Projekt.

#### <a name="to-create-the-sharepoint-commands-project"></a>So erstellen Sie das SharePoint-Befehlsprojekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den SiteColumnProjectItem-Knoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.

2. Am oberen Rand der **neues Projekt hinzufügen** Dialogfeld wählen **.NET Framework 3.5** in der Liste der Versionen von .NET Framework.

3. Erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten, und wählen Sie dann die **Windows** Knoten.

4. Wählen Sie die **Klassenbibliothek** -Projektvorlage aus, nennen Sie das Projekt **SharePointCommands**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **SharePointCommands** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-projects"></a>Konfigurieren Sie die Projekte
 Bevor Sie den Assistenten erstellen, müssen Sie den Projekten einige Codedateien und Assemblyverweise hinzufügen.

#### <a name="to-configure-the-wizard-project"></a>So konfigurieren Sie ein Assistentenprojekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ProjectTemplateWizard** Projektknoten, und wählen Sie dann **Eigenschaften**.

2. In der **Projekt-Designer**, wählen Sie die **Anwendung** Registerkarte für ein Visual Basic#-Projekt oder die **Kompilieren** Visual Basic-Projekt auf der Registerkarte.

3. Stellen Sie sicher, dass für das Zielframework .NET Framework 4.5 und nicht .NET Framework 4.5 Client Profile festgelegt ist.

     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Projekten für eine bestimmte .NET Framework-Version](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

4. Öffnen Sie das Kontextmenü für die **ProjectTemplateWizard** Projekts **hinzufügen**, und wählen Sie dann **neues Element**.

5. Wählen Sie die **Fenster (WPF)** -Element aus, nennen Sie das Element **WizardWindow**, und wählen Sie dann die **hinzufügen** Schaltfläche.

6. Hinzufügen von zwei **Benutzersteuerelement (WPF)** Elemente, die das Projekt, und nennen Sie diese **Page1** und **Page2**.

7. Fügen Sie dem Projekt vier Codedateien mit den folgenden Namen hinzu:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. Öffnen Sie das Kontextmenü für die **ProjectTemplateWizard** Projektknoten, und wählen Sie dann **Verweis hinzufügen**.

9. Erweitern Sie die **Assemblys** Knoten, wählen Sie die **Erweiterungen** Knoten, und wählen Sie dann die Kontrollkästchen neben den folgenden Assemblys:

    - EnvDTE

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.SharePoint

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.Shell.Interop.10.0

    - Microsoft.VisualStudio.Shell.Interop.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. Wählen Sie die **OK** , um die Assemblys dem Projekt hinzuzufügen.

11. In **Projektmappen-Explorer**unter der **Verweise** Ordner für die **ProjectTemplateWizard** Projekts **EnvDTE**.

12. In der **Eigenschaften** Fenster ändern Sie den Wert von der **Embed Interop Types** Eigenschaft **"false"**.

13. Wenn Sie ein Visual Basic-Projekt entwickeln, können Sie den Namespace "ProjectTemplateWizard" in Ihr Projekt importieren, mit der **Projekt-Designer**.

     Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen oder Entfernen von importierten Namespaces &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>So konfigurieren Sie das Projekt "SharePointCommands"

1. In **Projektmappen-Explorer**, wählen Sie die **SharePointCommands** Projektknoten.

2. Wählen Sie auf der Menüleiste **Projekt**, **vorhandenes Element hinzufügen**.

3. In der **vorhandenes Element hinzufügen** Dialogfeld, navigieren Sie zu dem Ordner, der die Codedateien für das Projekt "ProjectTemplateWizard" enthält, und wählen Sie dann die **CommandIds** Codedatei.

4. Wählen Sie den Pfeil neben der **hinzufügen** Schaltfläche, und wählen Sie dann die **als Link hinzufügen** im Menü "", der angezeigt wird.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt die Codedatei, die **SharePointCommands** Projekt als Link. Die Codedatei befindet sich in der **"ProjectTemplateWizard"** -Projekt, aber der Code in der Datei wird auch im kompiliert die **SharePointCommands** Projekt.

5. In der **SharePointCommands** fügen eine weitere Codedatei mit dem Namen Befehle.

6. Wählen Sie das Projekt "SharePointCommands" und dann auf der Menüleiste die Option **Projekt** > **Verweis hinzufügen**.

7. Erweitern Sie die **Assemblys** Knoten, wählen Sie die **Erweiterungen** Knoten, und wählen Sie dann die Kontrollkästchen neben den folgenden Assemblys:

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

8. Wählen Sie die **OK** , um die Assemblys dem Projekt hinzuzufügen.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Erstellen Sie die Assistenten-Modell, Signatur-Manager und SharePoint-Befehls-IDs
 Fügen Sie dem Projekt ProjectTemplateWizard Code hinzu, um die folgenden Komponenten im Beispiel zu implementieren:

- Die SharePoint-Befehls-IDs. Durch diese Zeichenfolgen werden die vom Assistenten verwendeten SharePoint-Befehle identifiziert. Weiter unten in dieser exemplarischen Vorgehensweise fügen Sie Code zum Projekt "SharePointCommands", das die Befehle zu implementieren.

- Das Datenmodell des Assistenten.

- Der Signatur-Manager für Projekte.

  Weitere Informationen zu diesen Komponenten finden Sie unter [verstehen der Komponenten von Assistenten](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>So definieren Sie die SharePoint-Befehls-IDs

1. Öffnen Sie im Projekt "ProjectTemplateWizard" die Codedatei "CommandIds", und ersetzen Sie den gesamten Inhalt dieser Datei durch den folgenden Code.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>So erstellen Sie das Assistentenmodell

1. Öffnen Sie die Codedatei "SiteColumnWizardModel", und ersetzen Sie den gesamten Inhalt dieser Datei durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>So erstellen Sie den Signatur-Manager für Projekte

1. Öffnen Sie die Codedatei "ProjectSigningManager", und ersetzen Sie dann den gesamten Inhalt dieser Datei durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Erstellen der Benutzeroberfläche des Assistenten
 Fügen Sie XAML hinzu, um die Benutzeroberfläche des Fensters für den Assistenten zu definieren, sowie die beiden Benutzersteuerelemente, die die Benutzeroberfläche für die Seiten des Assistenten bereitstellen, und fügen Sie Code hinzu, um das Verhalten des Fensters und der Benutzersteuerelemente zu definieren. Der erstellte Assistent ähnelt dem integrierten Assistenten für SharePoint-Projekte in Visual Studio.

> [!NOTE]
> In den folgenden Schritten treten mehrere Compilerfehler im Projekt auf, nachdem Sie diesem XAML oder Code hinzugefügt haben. Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.

#### <a name="to-create-the-wizard-window-ui"></a>So erstellen Sie die Benutzeroberfläche für das Fenster des Assistenten

1. Klicken Sie im Projekt "ProjectTemplateWizard" Öffnen Sie das Kontextmenü für die Datei "WizardWindow.xaml", und wählen Sie dann **öffnen** um das Fenster im Designer zu öffnen.

2. Ersetzen Sie in der XAML-Ansicht des Designers das aktuelle XAML durch das folgende XAML. Mit dem XAML wird eine Benutzeroberfläche einschließlich einer Überschrift, einem <xref:System.Windows.Controls.Grid> mit den Seiten des Assistenten sowie Navigationsschaltflächen unten im Fenster definiert.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > Das Fenster, das in diesem XAML erstellt wird ergibt sich aus der <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Basisklasse. Wenn Sie Visual Studio ein benutzerdefiniertes WPF-Dialogfeld hinzufügen, wird empfohlen, das Dialogfeld von dieser Klasse abzuleiten, um ein einheitliches Aussehen mit anderen Dialogfeldern von Visual Studio sicherzustellen und Probleme mit modalen Dialogfeldern zu vermeiden, die andernfalls auftreten können. Weitere Informationen finden Sie unter [erstellen und Verwalten von modalen Dialogfeldern](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).

3. Wenn Sie ein Visual Basic-Projekt entwickeln, entfernen Sie die `ProjectTemplateWizard` Namespace aus der `WizardWindow` Class-Name in der `x:Class` Attribut des der `Window` Element. Dieses Element befindet sich in der ersten XAML-Zeile. Wenn Sie fertig sind, sollte die erste Zeile wie im folgenden Beispiel aussehen.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Öffnen Sie die CodeBehind-Datei für die Datei WizardWindow.xaml.

5. Ersetzen Sie den Inhalt dieser Datei mit Ausnahme der `using`-Deklarationen am Dateianfang durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>So erstellen Sie die Benutzeroberfläche für die erste Seite des Assistenten

1. Im Projekt "ProjectTemplateWizard" das Kontextmenü für die Datei "Page1.xaml", und wählen Sie dann **öffnen** auf das Benutzersteuerelement im Designer zu öffnen.

2. Ersetzen Sie in der XAML-Ansicht des Designers das aktuelle XAML durch das folgende XAML. Vom XAML wird eine Benutzeroberfläche mit einem Textfeld definiert, in dem Benutzer die URL der lokalen Websites eingeben können, die sie zum Debuggen verwenden möchten. Die Benutzeroberfläche weist zudem Optionsfelder auf, mit denen Benutzer angeben können, ob es sich um ein Sandkastenprojekt handelt.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. Wenn Sie ein Visual Basic-Projekt entwickeln, entfernen Sie den `ProjectTemplateWizard`-Namespace aus dem `Page1`-Klassennamen im `x:Class`-Attribut des `UserControl`-Elements. Dies erfolgt in der ersten Zeile des XAML. Anschließend sollte die erste Zeile wie folgt aussehen.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Ersetzen Sie den Inhalt der Datei "Page1.xaml" mit Ausnahme der `using`-Deklarationen am Dateianfang durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>So erstellen Sie die Benutzeroberfläche für die zweite Seite des Assistenten

1. Klicken Sie im Projekt "ProjectTemplateWizard" das Kontextmenü für die Datei "Page2.xaml" öffnen, und wählen Sie dann **öffnen**.

     Das Benutzersteuerelement wird im Designer geöffnet.

2. Ersetzen Sie in der XAML-Ansicht das aktuelle durch folgendes XAML. Mit dem XAML wird eine Benutzeroberfläche einschließlich einer Dropdownliste zum Auswählen des Basistyps der Websitespalte, eines Kombinationsfelds zum Angeben der integrierten oder benutzerdefinierten Gruppe, unter der die Websitespalte im Katalog angezeigt werden soll, sowie eines Textfelds zum Angeben des Namens der Websitespalte definiert.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. Wenn Sie ein Visual Basic-Projekt entwickeln, entfernen Sie den `ProjectTemplateWizard`-Namespace aus dem `Page2`-Klassennamen im `x:Class`-Attribut des `UserControl`-Elements. Dies erfolgt in der ersten Zeile des XAML. Anschließend sollte die erste Zeile wie folgt aussehen.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Ersetzen Sie den Inhalt der CodeBehind-Datei für die Datei "Page2.xaml" mit Ausnahme der `using`-Deklarationen am Dateianfang durch den folgenden Code.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Der Assistent zum Implementieren von
 Definieren Sie die wichtigsten Funktionen des Assistenten, indem Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle implementieren. Diese Schnittstelle definiert die Methoden, die von Visual Studio aufgerufen werden, wenn der Assistent gestartet wird, wenn der Assistent beendet wird und gelegentlich, während der Assistent ausgeführt wird.

#### <a name="to-implement-the-wizard"></a>So implementieren Sie den Assistenten

1. Öffnen Sie die Codedatei SiteColumnProjectWizard im Projekt ProjectTemplateWizard.

2. Ersetzen Sie den gesamten Inhalt der Datei durch folgenden Code:

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>Erstellen Sie die SharePoint-Befehle
 Erstellen Sie zwei benutzerdefinierte Befehle, die einen Aufruf in das SharePoint-Serverobjektmodell durchführen. Mit einem Befehl wird angegeben, ob die Website-URL, die vom Benutzer im Assistenten eingegeben wird, gültig ist. Mit dem anderen Befehl werden alle Feldtypen von der angegebenen SharePoint-Website abgerufen, sodass Benutzer auswählen können, welcher Typ als Basis für die neue Websitespalte verwendet werden soll.

#### <a name="to-define-the-sharepoint-commands"></a>So definieren Sie die SharePoint-Befehle

1. In der **SharePointCommands** Projekt, öffnen Sie die Codedatei Commands.

2. Ersetzen Sie den gesamten Inhalt der Datei durch folgenden Code:

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>Checkpoint
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für den Assistenten benötigte Code in das Projekt eingefügt. Erstellen Sie das Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.

#### <a name="to-build-your-project"></a>So erstellen Sie das Projekt

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Entfernen die key.snk-Datei aus der Projektvorlage
 In [Exemplarische Vorgehensweise: Erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), die Projektvorlage, die Sie erstellt haben, enthält eine key.snk-Datei, die mit dem einzelnen Projektinstanzen für Websitespalten signiert. Diese key.snk-Datei wird nicht mehr benötigt, da vom Assistenten nun eine neue key.snk-Datei für jedes Projekt generiert wird. Entfernen Sie die key.snk-Datei aus der Projektvorlage, und entfernen Sie die Verweise auf die Datei.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>So entfernen Sie die key.snk-Datei aus der Projektvorlage

1. In **Projektmappen-Explorer**unter der **SiteColumnProjectTemplate** Knoten, öffnen Sie das Kontextmenü für die **"Key.snk"** Datei, und wählen Sie dann **Löschen**.

2. Wählen Sie im Dialogfeld zur Bestätigung, die angezeigt wird, die **OK** Schaltfläche.

3. Unter den **SiteColumnProjectTemplate** Knoten, öffnen Sie die Datei "SiteColumnProjectTemplate.vstemplate", und klicken Sie dann das folgende Element daraus entfernen.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Speichern und schließen Sie die Datei.

5. Unter den **SiteColumnProjectTemplate** Knoten, öffnen Sie die Datei ProjectTemplate.csproj oder ProjectTemplate.vbproj, und entfernen Sie die folgenden `PropertyGroup` -Element daraus.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Entfernen Sie das folgende `None`-Element:

    ```xml
    <None Include="key.snk" />
    ```

7. Speichern und schließen Sie die Datei.

## <a name="associating-the-wizard-with-the-project-template"></a>Die Projektvorlage Zuordnen des Assistenten
 Nun, da Sie den Assistenten implementiert haben, müssen Sie den Assistenten mit Zuordnen der **Websitespalte** Projektvorlage. Hierzu müssen drei Verfahren ausgeführt werden:

1. Signieren der Assistenten-Assembly mit einem starkem Namen

2. Abrufen des öffentlichen Schlüsseltokens der Assistenten-Assembly

3. Fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei für die **Websitespalte** Projektvorlage.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>So signieren Sie die Assistenten-Assembly mit einem starkem Namen

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ProjectTemplateWizard** Projekt, und wählen Sie dann **Eigenschaften**.

2. Auf der **Signierung** Registerkarte die **Assembly signieren** Kontrollkästchen.

3. In der **Schlüsseldatei mit starkem Namen auswählen** wählen  **\<neu... >**.

4. In der **Schlüssel für einen starken Namen erstellen** Dialogfeld Geben Sie einen Namen für die neue Datei mit dem Schlüssel löschen der **Schlüsseldatei mit Kennwort schützen** aus, und wählen Sie dann die **OK** Schaltfläche.

5. Öffnen Sie das Kontextmenü für die **ProjectTemplateWizard** Projekt, und wählen Sie dann **erstellen** zum Erstellen der Datei "ProjectTemplateWizard.dll".

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>So rufen Sie das öffentliche Schlüsseltoken der Assistenten-Assembly ab

1. Auf der **Menü "Start"**, wählen Sie **Programme**, wählen Sie **Microsoft Visual Studio**, wählen Sie **Visual Studio-Tools**, und wählen Sie dann auf  **Developer-Eingabeaufforderung**.

     Ein Visual Studio-Eingabeaufforderungsfenster wird geöffnet.

2. Führen Sie den folgenden Befehl aus, und Ersetzen Sie dabei *PathToWizardAssembly* durch den vollständigen Pfad zu der erstellten "ProjectTemplateWizard.dll"-Assembly für das Projekt "ProjectTemplateWizard" auf Ihrem Entwicklungscomputer:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Das öffentliche Schlüsseltoken für die Assembly ProjectTemplateWizard.dll wird in das Fenster der Visual Studio-Eingabeaufforderung geschrieben.

3. Lassen Sie das Fenster der Visual Studio-Eingabeaufforderung geöffnet. Sie benötigen das öffentliche Schlüsseltoken während der nächsten Prozedur.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>So fügen Sie einen Verweis auf die Assistenten-Assembly in der VSTEMPLATE-Datei hinzu

1. In **Projektmappen-Explorer**, erweitern Sie die **SiteColumnProjectTemplate** Projektknoten, und öffnen Sie die Datei SiteColumnProjectTemplate.vstemplate.

2. Fügen Sie das folgende `WizardExtension`-Element zwischen dem `</TemplateContent>`-Tag und dem `</VSTemplate>`-Tag am Ende der Datei hinzu. Ersetzen Sie die *Ihr Token* Wert der `PublicKeyToken` Attribut mit dem Token des öffentlichen Schlüssels, den Sie in der vorherigen Prozedur abgerufen haben.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Weitere Informationen zu den `WizardExtension` Element finden Sie unter [WizardExtension-Element &#40;Visual Studio-Vorlagen&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).

3. Speichern und schließen Sie die Datei.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Hinzufügen von ersetzbaren Parametern zur Datei "Elements.xml" in der Projektvorlage
 Fügen Sie mehrere ersetzbare Parameter an die *"Elements.xml"* Datei im SiteColumnProjectTemplate-Projekt. Diese Parameter werden in der `RunStarted`-Methode in der zuvor definierten `SiteColumnProjectWizard`-Klasse initialisiert. Wenn ein Benutzer ein Websitespaltenprojekt erstellt, ersetzt Visual Studio automatisch diese Parameter werden in der *"Elements.xml"* -Datei in das neue Projekt mit den Werten, die sie im Assistenten angegeben.

 Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen ($) beginnt und endet. Zusätzlich zu den selbst definierten ersetzbaren Parametern können Sie auch integrierte Parameter verwenden, die vom SharePoint-Projektsystem definiert und initialisiert werden. Weitere Informationen finden Sie unter [ersetzbare Parameter](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>So fügen Sie der Datei Elements.xml ersetzbare Parameter hinzu

1. Ersetzen Sie im SiteColumnProjectTemplate-Projekt den Inhalt der *"Elements.xml"* -Datei mit den folgenden XML-Code.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     Durch das neue XML werden die Werte der Attribute `Name`, `DisplayName`, `Type` und `Group` in benutzerdefinierte ersetzbare Parameter geändert.

2. Speichern und schließen Sie die Datei.

## <a name="add-the-wizard-to-the-vsix-package"></a>Fügen Sie den Assistenten zum VSIX-Paket
 Um den Assistenten mit dem VSIX-Paket und der Projektvorlage für Websitespalten bereitzustellen, fügen Sie der Datei source.extension.vsixmanifest im VSIX-Projekt Verweise auf das Assistentenprojekt und das SharePoint-Befehlsprojekt hinzu.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>So fügen Sie den Assistenten dem VSIX-Paket hinzu

1. In **Projektmappen-Explorer**in die **SiteColumnProjectItem** Projekt, öffnen Sie das Kontextmenü für die **"Source.Extension.vsixmanifest"** Datei, und wählen Sie dann auf **Öffnen**.

     Die Datei wird von Visual Studio im Manifest-Editor geöffnet.

2. Auf der **Assets** Registerkarte des Editors wählen Sie die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.

3. In der **Typ** wählen **Microsoft.VisualStudio.Assembly**.

4. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

5. In der **Projekt** wählen **ProjectTemplateWizard**, und wählen Sie dann die **OK** Schaltfläche.

6. Auf der **Assets** Registerkarte des Editors wählen Sie die **neu** erneut.

     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.

7. In der **Typ** aus, geben Sie **SharePoint.Commands.v4**.

8. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

9. In der **Projekt** wählen die **SharePointCommands** Projekt, und wählen Sie dann die **OK** Schaltfläche.

10. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe**, und klicken Sie dann stellen Sie sicher, dass die Projektmappe ohne Fehler erstellt wurde.

## <a name="test-the-wizard"></a>Testen Sie den Assistenten
 Sie können den Assistenten jetzt testen. Debuggen Sie die Projektmappe SiteColumnProjectItem zunächst in der experimentellen Instanz von Visual Studio. Anschließend testen Sie den Assistenten für das Websitespaltenprojekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das Projekt aus, um sicherzustellen, dass die Websitespalte ordnungsgemäß funktioniert.

#### <a name="to-start-debugging-the-solution"></a>So debuggen Sie die Projektmappe

1. Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "SiteColumnProjectItem".

2. Öffnen Sie im Projekt "ProjectTemplateWizard" die Codedatei "SiteColumnProjectWizard", und fügen Sie dann der ersten Codezeile in der `RunStarted`-Methode einen Haltepunkt hinzu.

3. Wählen Sie auf der Menüleiste **Debuggen** > **Ausnahmen**.

4. In der **Ausnahmen** Dialogfeld Feld, stellen Sie sicher, dass die **ausgelöst** und **vom Benutzercode unbehandelt** Kontrollkästchen für **Common Language Runtime-Ausnahmen**werden gelöscht, und wählen Sie dann die **OK** Schaltfläche.

5. Starten Sie das Debuggen durch Auswählen der **F5** -Taste oder wählen Sie auf der Menüleiste die Optionen **Debuggen** > **Debuggen starten**.

     Die Erweiterung wird unter "%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Websitespalte\1.0 installiert", und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>So testen Sie den Assistenten in Visual Studio

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Datei** > **neu** > **Projekt**.

2. Erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten (je nach der die Projektvorlage unterstützten Sprache), erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

3. Wählen Sie in der Liste der Projektvorlagen das Projekt **Websitespalte**, nennen Sie das Projekt **SiteColumnWizardTest**, und wählen Sie dann die **OK** Schaltfläche.

4. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `RunStarted`-Methode festgelegt haben.

5. Fahren Sie mit dem Debuggen des Projekts durch Auswahl der **F5** -Taste oder wählen Sie auf der Menüleiste die Optionen **Debuggen** > **Weiter**.

6. In der **SharePoint Customization Wizard**, geben Sie die URL der Website, die Sie für das Debuggen verwenden möchten, und wählen Sie dann die **Weiter** Schaltfläche.

7. In der zweiten Seite des der **SharePoint Customization Wizard**, die folgenden Optionen:

   - In der **Typ** wählen **booleschen**.

   - In der **Gruppe** wählen **benutzerdefinierte Ja/Nein-Spalten**.

   - In der **Namen** geben **Eigene Ja/Nein-Spalte**, und wählen Sie dann die **Fertig stellen** Schaltfläche.

     In **Projektmappen-Explorer**, ein neues Projekt angezeigt wird, und das ein Projektelement mit dem Namen **"Field1"**, Visual Studio geöffnet wird, des Projekts *"Elements.xml"* Datei im Editor.

8. Überprüfen Sie, ob *"Elements.xml"* enthält die Werte, die Sie im Assistenten angegeben.

#### <a name="to-test-the-site-column-in-sharepoint"></a>So testen Sie die Websitespalte in SharePoint

1. Wählen Sie in der experimentellen Instanz von Visual Studio die **F5** Schlüssel.

     Die Websitespalte wird verpackt und bereitgestellt werden, auf die SharePoint-Website, die **Website-URL** -Eigenschaft des Projekts angibt. Im Webbrowser wird die Standardseite dieser Website geöffnet.

    > [!NOTE]
    > Wenn die **Skriptdebugging deaktiviert** wählen Sie im angezeigten Dialogfeld die **Ja** Schaltfläche, um das Debuggen des Projekts fortzusetzen.

2. Auf der **Websiteaktionen** Menü wählen **Standorteinstellungen**.

3. Auf der Seite Siteeinstellungen unter **Galerien**, wählen Sie die **Site Spalten** Link.

4. Überprüfen Sie in der Liste der Websitespalten, ob eine **benutzerdefinierte Ja/Nein-Spalten** Gruppe enthält eine Spalte mit dem Namen **Eigene Ja/Nein-Spalte**, und schließen Sie dann den Webbrowser.

## <a name="clean-up-the-development-computer"></a>Bereinigung auf dem Entwicklungscomputer
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektvorlage aus der experimentellen Instanz von Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Tools** > **Erweiterungen und Updates**.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen, **Websitespalte**, und wählen Sie dann die **Deinstallieren** Schaltfläche.

3. Wählen Sie in das Dialogfeld, das angezeigt wird, die **Ja** , um zu bestätigen, dass Sie verwenden möchten, deinstallieren Sie die Erweiterung aus, und wählen Sie dann die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.

4. Schließen Sie die experimentelle Instanz von Visual Studio und die Instanz, in der die Projektmappe "CustomActionProjectItem" geöffnet ist.

     Informationen zum Bereitstellen von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterungen finden Sie unter [Auslieferung von Visual Studio-Erweiterungen](/visualstudio/extensibility/shipping-visual-studio-extensions).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Schemareferenz zu Visual Studio-Vorlagen](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)
