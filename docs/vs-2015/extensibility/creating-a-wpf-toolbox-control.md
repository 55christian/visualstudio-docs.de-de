---
title: Erstellen eines WPF-Toolbox-Steuerelements | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 768d9747635f2106d16f755db6799e356c890838
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096373"
---
# <a name="creating-a-wpf-toolbox-control"></a>Erstellen eines WPF-Toolbox-Steuerelements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Vorlage für Toolbox-Steuerelement für WPF (Windows Presentation Framework) können Sie die WPF-Steuerelemente erstellen, die automatisch hinzugefügt werden, die **Toolbox** beim Installieren der Erweiterung. In diesem Thema wird gezeigt, wie Sie die Vorlage zu verwenden, zum Erstellen einer **Toolbox** -Steuerelement, das Sie für andere Benutzer verteilen können.  
  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Erstellen eines WPF-Toolbox-Steuerelements  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Erstellen Sie eine Erweiterung mit einem WPF-Toolbox-Steuerelement  
  
1. Erstellen Sie ein VSIX-Projekt mit dem Namen `MyToolboxControl`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2. Wenn das Projekt geöffnet wird, eine **WPF-Toolbox-Steuerelement** Item-Vorlage, die mit dem Namen `MyToolboxControl`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **WPF-Toolbox-Steuerelement**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an `MyToolboxControl.cs`.  
  
     Die Projektmappe enthält jetzt ein Benutzersteuerelement, ein `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , die das Steuerelement, fügt die **Toolbox**, und ein **Microsoft.VisualStudio.ToolboxControl** Ressourceneintrag im VSIX-Manifest für  die Bereitstellung.  
  
#### <a name="to-create-the-control-ui"></a>So erstellen Sie eine Steuerelement-Benutzeroberfläche  
  
1. MyToolboxControl.xaml im Designer geöffnet.  
  
     Der Designer zeigt ein <xref:System.Windows.Controls.Grid>-Steuerelement an, das ein <xref:System.Windows.Controls.Button>-Steuerelement enthält.  
  
2. Ordnen Sie das Rasterlayout. Bei der Auswahl der <xref:System.Windows.Controls.Grid> zu steuern, Blau Schiebeleisten-Steuerelemente, die auf dem oberen und linken Rand des Rasters angezeigt werden. Sie können Zeilen und Spalten zum Raster hinzufügen, indem Sie auf die Balken.  
  
3. Fügen Sie untergeordnete Steuerelemente in das Raster an. Sie können ein untergeordnetes Steuerelement positionieren, ziehen Sie es aus der **Toolbox** in einen Bereich des Rasters oder durch Festlegen seiner `Grid.Row` und `Grid.Column` Attribute in der XAML. Das folgende Beispiel fügt zwei Bezeichnungen auf der obersten Zeile des Rasters und eine Schaltfläche auf der zweiten Zeile.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Umbenennen des Steuerelements  
 Standardmäßig wird das Steuerelement angezeigt, der **Toolbox** als **MyToolboxControl** in einer Gruppe namens **MyToolboxControl.MyToolboxControl**. Sie können diese Namen in der Datei MyToolboxControl.xaml.cs ändern.  
  
1. Öffnen Sie in der Codeansicht MyToolboxControl.xaml.cs.  
  
2. Suchen Sie die MyToolboxControl-Klasse, und benennen Sie sie in TestControl. (Die schnellste Möglichkeit hierzu ist die-Klasse umbenennen wählen Sie dann **umbenennen** aus dem Kontextmenü, und führen Sie die Schritte aus. (Weitere Informationen zu den **umbenennen** Befehl, finden Sie unter [Umgestaltung mit Umbenennen (c#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3. Wechseln Sie zu der `ProvideToolboxControl` Attribut, und ändern Sie den Wert des ersten Parameters, der **Test**. Dies ist der Name der Gruppe, die das Steuerelement in enthält die **Toolbox**.  
  
     Der resultierende Code sollte wie folgt aussehen:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Erstellen, Tests und Bereitstellung  
 Wenn Sie das Projekt debuggen, finden Sie sollten das Steuerelement installiert, die der **Toolbox** der experimentellen Instanz von Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>So erstellen Sie das Steuerelement und testen es  
  
1. Das Projekt neu, und starten Sie das Debuggen.  
  
2. Erstellen Sie in der neuen Instanz von Visual Studio ein WPF-Anwendungsprojekt. Stellen Sie sicher, dass der XAML-Designer geöffnet ist.  
  
3. Suchen Sie in der **Toolbox** nach dem Steuerelement, und ziehen Sie es dann auf die Entwurfsoberfläche.  
  
4. Debuggen Sie die WPF-Anwendung.  
  
5. Stellen Sie sicher, dass das Steuerelement angezeigt wird.  
  
#### <a name="to-deploy-the-control"></a>So stellen Sie das Steuerelement bereit  
  
1. Nachdem Sie das getestete Projekt erstellt haben, finden Sie die VSIX-Datei in der "\bin\debug\" des Projekts.  
  
2. Sie können es auf einem lokalen Computer installieren, durch Doppelklicken auf die VSIX-Datei, und folgen den Installationsvorgang zu starten. Um das Steuerelement zu deinstallieren, wechseln Sie zu **Extras / Erweiterungen und Updates** suchen Sie nach der Erweiterung, und klicken Sie auf **Deinstallieren**.  
  
3. Laden Sie die VSIX-Datei in ein Netzwerk oder auf einer Website hoch.  
  
     Wenn Sie die Datei zum Hochladen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website, die andere Benutzer verwenden können **Extras / Erweiterungen und Updates** in Visual Studio für das Steuerelement online suchen und installieren Sie es.
