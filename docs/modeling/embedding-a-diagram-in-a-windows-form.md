---
title: Einbetten eines Diagramms in Windows Form
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b2ed12175e986178d43ffe5e3da8b85e2ab22e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62994579"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Einbetten eines Diagramms in Windows Form

Sie können einem DSL-Diagramm in einem Windows-Steuerelement, einbetten, die in Visual Studio-Fenster angezeigt wird.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Einbetten von einem DSL-Diagramm in einem Windows-Steuerelement

1. Fügen Sie einen neuen **Benutzersteuerelement** Datei DslPackage-Projekt.

2. Fügen Sie ein Panel-Steuerelement, auf das Benutzersteuerelement. In diesem Bereich wird das DSL-Diagramm enthalten.

     Fügen Sie andere Steuerelemente, die erforderlich sind.

     Legen Sie die Anker-Eigenschaften der Steuerelemente.

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste der Benutzersteuerelement-Datei, und klicken Sie auf **Ansichtscode**. Fügen Sie diesen Konstruktor und die Variable auf den Code hinzu:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Fügen Sie eine neue Datei in das DslPackage-Projekt mit dem folgenden Inhalt hinzu:

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. Um die DSL zu testen, indem Sie **F5** , und öffnen Sie eine beispielmodelldatei. Das Diagramm auf das Steuerelement angezeigt wird. Die Toolbox und andere Funktionen funktionieren ordnungsgemäß.

## <a name="update-the-form-using-store-events"></a>Aktualisieren Sie das Formular mit Speicherereignisse

1. Fügen Sie in den Formular-Designer eine **ListBox** mit dem Namen `listBox1`. Dadurch wird eine Liste der Elemente im Modell angezeigt. Es wieder synchronisiert wird, mit dem Modell mit *Speichern von Ereignissen*. Weitere Informationen finden Sie unter [Handler weitergegeben werden Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Überschreiben Sie in der Datei mit benutzerdefiniertem Code weitere Methoden, um die DocView--Klasse:

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. Fügen Sie in den Code-behind das Benutzersteuerelement Methoden zum Lauschen auf die Elemente hinzugefügt und entfernt:

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. Um die DSL zu testen, indem Sie **F5** und in der experimentellen Instanz von Visual Studio, öffnen Sie eine beispielmodelldatei.

     Beachten Sie, dass im Listenfeld eine Liste der Elemente im Modell angezeigt wird und er korrekt ist, nachdem alle Hinzufügungen oder löschungen und rückgängig und wiederholen.

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
