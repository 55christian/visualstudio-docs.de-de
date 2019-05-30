---
title: 'Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 79a54867044961d972e2ded452958d2463038e7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318521"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Exemplarische Vorgehensweise: Speichern von benutzereinstellungen auf einer Startseite

Sie können die benutzereinstellungen für die Startseite beibehalten. Anhand dieser exemplarischen Vorgehensweise können Sie ein Steuerelement erstellen, die eine Einstellung in der Registrierung gespeichert, wenn der Benutzer auf eine Schaltfläche klickt, und ruft dann diese Einstellung jedes Mal, wenn der Startseite geladen. Da die Startseite-Projektvorlage ein anpassbares Steuerelement enthält und der Standardwert beginnen Seite XAML, die steuern aufruft, müssen Sie nicht die Startseite selbst ändern.

Der Speicher für benutzereinstellungen, die in dieser exemplarischen Vorgehensweise instanziiert wird, ist eine Instanz von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> -Schnittstelle, die Lese- und Schreibvorgänge in folgendem Registrierungspfad, wenn sie aufgerufen wird: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<CollectionName>**

Wenn sie in der experimentellen Instanz von Visual Studio ausgeführt wird, liest und schreibt in der einstellungsspeicher **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<Auflistungsname >.**

Weitere Informationen dazu, wie Sie die Einstellungen beibehalten werden, finden Sie unter [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).
>
> Sie können die Projektvorlage für die Startseite mit **Erweiterungs-Manager**.

## <a name="set-up-the-project"></a>Einrichten des Projekts

1. Erstellen Sie ein Startseitenprojekt, wie im [erstellen Sie eine benutzerdefinierte Startseite](creating-a-custom-start-page.md). Nennen Sie das Projekt **SaveMySettings**.

2. In **Projektmappen-Explorer**, fügen Sie dem StartPageControl-Projekt die folgenden Assemblyverweise hinzu:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Open *"MeinSteuerelement.xaml"* .

4. Im XAML-Bereich, in der obersten Ebene <xref:System.Windows.Controls.UserControl> Elementdefinition, fügen Sie die folgenden Ereignisdeklaration nach den Namespacedeklarationen hinzu.

    ```xml
    Loaded="OnLoaded"
    ```

5. Klicken Sie in den Entwurfsbereich, klicken Sie auf den Hauptbereich des Steuerelements, und drücken Sie dann **löschen**.

     Mit diesem Schritt Entfernen der <xref:System.Windows.Controls.Border> -Element und alle Elemente, und lässt Sie nur die obersten Ebene <xref:System.Windows.Controls.Grid> Element.

6. Von der **Toolbox**, ziehen Sie eine <xref:System.Windows.Controls.StackPanel> Steuerelement zum Raster.

7. Ziehen Sie jetzt eine <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>, und eine Schaltfläche, um die <xref:System.Windows.Controls.StackPanel>.

8. Hinzufügen einer **X: Name** -Attribut für die <xref:System.Windows.Controls.TextBox>, und ein `Click` -Ereignis für die <xref:System.Windows.Controls.Button>, wie im folgenden Beispiel gezeigt.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Implementieren Sie das Benutzersteuerelement

1. In der XAML-Bereich mit der Maustaste der `Click` Attribut der <xref:System.Windows.Controls.Button> -Element, und klicken Sie dann auf **navigieren Sie zum Ereignishandler**.

     Dieser Schritt öffnet *MyControl.xaml.cs*, und erstellt einen Stub-Ereignishandler für die `Button_Click` Ereignis.

2. Fügen Sie die folgenden `using` Anweisungen am Anfang der Datei.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Hinzufügen eine privaten `SettingsStore` -Eigenschaft, wie im folgenden Beispiel gezeigt.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Diese Eigenschaft ruft zunächst einen Verweis auf die <xref:EnvDTE80.DTE2> -Schnittstelle, die das Automatisierungsobjektmodell von enthält die <xref:System.Windows.FrameworkElement.DataContext%2A> der Benutzersteuerelement, und klicken Sie dann verwendet, um eine Instanz des DTE der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> Schnittstelle. Klicken Sie dann wird diese Instanz, um die aktuellen benutzereinstellungen zurück.

4. Geben Sie die `Button_Click` Ereignis wie folgt.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     Schreibt den Inhalt des Textfelds, das auf ein Feld "MySetting" in einer Auflistung "MySettings" in der Registrierung. Wenn die Auflistung nicht vorhanden ist, wird es erstellt.

5. Fügen Sie den folgenden Ereignishandler für die `OnLoaded` Ereignis des Steuerelements.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Dieser Code legt den Text des Textfelds, das auf den aktuellen Wert des "MySetting" fest.

6. Erstellen Sie das Benutzersteuerelement.

7. In **Projektmappen-Explorer**öffnen *"Source.Extension.vsixmanifest"* .

8. Legen Sie im manifest-Editor, **Produktname** zu **speichern My Settings Startseite**.

     Diese Funktion legt den Namen der Startseite fest, wie die in angezeigt werden die **Customize Start Page** Liste der **Optionen** Dialogfeld.

9. Erstellen Sie *"StartPage.xaml"* .

## <a name="test-the-control"></a>Testen Sie das Steuerelement

1. Drücken Sie **F5**.

     Die experimentelle Instanz von Visual Studio wird geöffnet.

2. In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **Optionen**.

3. In der **Umgebung** Knoten, klicken Sie auf **Start**, und dann auf die **Customize Start Page** Liste **[installierte Extension] speichern My Settings Startseite** .

     Klicken Sie auf **OK**.

4. Schließen Sie die Startseite, falls er geöffnet ist, und klicken Sie dann auf die **Ansicht** Menü klicken Sie auf **Startseite**.

5. Klicken Sie auf der Startseite auf die **MyControl** Registerkarte.

6. Geben Sie in das Textfeld ein **Cat**, und klicken Sie dann auf **Meine Einstellung speichern**.

7. Schließen Sie die Startseite, und öffnen Sie es noch mal.

     Das Wort "Katze" sollte in das Textfeld angezeigt werden.

8. Ersetzen Sie das Wort "Katze" mit dem Wort "Hund". Klicken Sie nicht auf die Schaltfläche.

9. Schließen Sie die Startseite, und öffnen Sie es noch mal.

     Der Begriff "Hund" sollte in das Textfeld angezeigt werden, auch wenn Sie die Einstellung zu speichern nicht, da Visual Studio Toolfenster im Arbeitsspeicher beibehält, auch wenn sie geschlossen werden, bis Visual Studio geschlossen wird.

10. Schließen Sie die experimentelle Instanz von Visual Studio.

11. Drücken Sie **F5** die experimentelle Instanz erneut öffnen.

12. Das Wort "Katze" sollte in das Textfeld angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Sie können dieses Steuerelement zum Speichern und Abrufen von eine beliebige Anzahl von benutzerdefinierten Einstellungen mithilfe von anderen Werten verschiedene Ereignishandler zum Abrufen und Festlegen der `SettingsStore` Eigenschaft. Solange Sie einen anderen `propertyName` Parameter für jeden Aufruf von <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, überschreiben die Werte nicht miteinander in der Registrierung.

## <a name="see-also"></a>Siehe auch

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Hinzufügen von Visual Studio-Befehlen zu einer Startseite](../extensibility/adding-visual-studio-commands-to-a-start-page.md)