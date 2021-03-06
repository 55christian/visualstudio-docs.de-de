---
title: Aktualisieren von Outlook-Formularbereichen in Projekten migriert auf .NET Framework 4, 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7e300cd9f6f7d631a029310b01fbfdad7cb4686
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836043"
---
# <a name="update-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualisieren von Formularbereichen in Outlook-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden
  Wenn das Zielframework eines Outlook VSTO-Add-In-Projekts mit einem Formularbereich in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie einige Änderungen am generierten Formularbereichscode und an Code vornehmen, durch den bestimmte Formularbereichsklassen zur Laufzeit instanziiert werden.

## <a name="update-the-generated-form-region-code"></a>Aktualisieren Sie den generierten formularbereichscode
 Wenn das Zielframework des Projekts in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie den generierten Formularbereichscode ändern. Die vorgenommenen Änderungen sind bei Formularbereichen, die Sie in Visual Studio entworfen haben, und Formularbereichen, die Sie aus Outlook importiert haben, unterschiedlich. Weitere Informationen zu den Unterschieden zwischen diesen Formularbereichstypen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>So aktualisieren Sie den generierten Code für einen in Visual Studio entworfenen Formularbereich

1. Öffnen Sie die CodeBehind-Datei des Formularbereichs im Code-Editor. Diese Datei hat den Namen " *IhrFormularbereich*.Designer.cs" oder " *IhrFormularbereich*.Designer.vb". Klicken Sie im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen**, um diese Datei in Visual Basic-Projekten anzuzeigen.

2. Ändern Sie die Deklaration der Formularbereichsklasse so, dass sie von <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> statt von `Microsoft.Office.Tools.Outlook.FormRegionControl` abgeleitet wird.

3. Ändern Sie den Konstruktor der Formularbereichklasse, wie in den folgenden Codebeispielen dargestellt.

     Im folgenden Codebeispiel wird der Konstruktor einer Formularbereichsklasse in einem Projekt dargestellt, das auf .NET Framework 3.5 ausgerichtet ist.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.InitializeComponent();
    }
    ```

     Im folgenden Codebeispiel wird der Konstruktor einer Formularbereichsklasse in einem Projekt dargestellt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet ist.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.InitializeComponent();
    }
    ```

4. Ändern Sie die Signatur der `InitializeManifest` -Methode, wie unten dargestellt. Stellen Sie sicher, dass Sie den Code in der Methode nicht ändern. Dieser Code stellt Formularbereichseinstellungen dar, die Sie im Designer angewendet haben. In Visual C#-Projekten müssen Sie den Bereich mit der Bezeichnung `Form Region Designer generated code` erweitern, um diese Methode anzuzeigen.

     Im folgenden Codebeispiel wird die Signatur der `InitializeManifest` -Methode in einem Projekt dargestellt, das auf .NET Framework 3.5 ausgerichtet ist.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)
    {
        // Do not change code in this method.
    }
    ```

     Im folgenden Codebeispiel wird die Signatur der `InitializeManifest` -Methode in einem Projekt dargestellt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet ist.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,
        Microsoft.Office.Tools.Outlook.Factory factory)
    {
        // Do not change code in this method.
    }
    ```

5. Fügen Sie Ihrem Projekt ein neues Outlook-Formularbereichselement hinzu. Öffnen Sie die CodeBehind-Datei für den neuen Formularbereich, suchen Sie die *YourNewFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen in der Datei, und kopieren Sie diese Klassen in die Zwischenablage.

6. Löschen Sie den neuen Formularbereich, den Sie dem Projekt hinzugefügt haben.

7. Suchen Sie in der CodeBehind-Datei des Formularbereichs, den Sie aktualisieren, damit er im neu ausgerichteten Projekt funktioniert, die *YourOriginalFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen, und ersetzen Sie sie durch den Code, den Sie aus dem neuen Formularbereich kopiert haben.

8. Suchen Sie in den *YourNewFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen alle Verweise auf die *YourNewFormRegion* -Klasse, und ändern Sie jeden Verweis stattdessen in die *YourOriginalFormRegion* -Kasse. Wenn der aktualisierte Formularbereich z. B. `SalesDataFormRegion` und der neue in Schritt 5 erstellte Formularbereich `FormRegion1`heißt, ändern Sie alle Verweise von `FormRegion1` in `SalesDataFormRegion`.

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>So aktualisieren Sie den generierten Code für einen aus Outlook importierten Formularbereich

1. Öffnen Sie die CodeBehind-Datei des Formularbereichs im Code-Editor. Diese Datei hat den Namen " *IhrFormularbereich*.Designer.cs" oder " *IhrFormularbereich*.Designer.vb". Klicken Sie im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen**, um diese Datei in Visual Basic-Projekten anzuzeigen.

2. Ändern Sie die Deklaration der Formularbereichsklasse so, dass sie von <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> statt von `Microsoft.Office.Tools.Outlook.ImportedFormRegion` abgeleitet wird.

3. Ändern Sie den Konstruktor der Formularbereichklasse, wie in den folgenden Codebeispielen dargestellt.

     Im folgenden Codebeispiel wird der Konstruktor einer Formularbereichsklasse in einem Projekt dargestellt, das auf .NET Framework 3.5 ausgerichtet ist.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

     Im folgenden Codebeispiel wird die Signatur des Konstruktors einer Formularbereichsklasse in einem Projekt dargestellt, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet ist.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

4. Ändern Sie für jede Codezeile in der `InitializeControls` -Methode, die ein Steuerelement in der Formularbereichsklasse initialisiert, den Code wie unten dargestellt.

     Im folgenden Codebeispiel wird veranschaulicht, wie ein Steuerelement in einem Projekt initialisiert wird, das auf .NET Framework 3.5 ausgerichtet ist. In diesem Code verfügt die `GetFormRegionControl`-Methode über einen Typparameter, der den Typ des Steuerelements angibt, das zurückgegeben wird.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     Im folgenden Codebeispiel wird veranschaulicht, wie ein Steuerelement in einem Projekt initialisiert wird, das auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ausgerichtet ist. In diesem Code weist die <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> -Methode keinen Typparameter auf. Sie müssen den Rückgabewert in den Typ des Steuerelements umwandeln, das Sie initialisieren.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Fügen Sie Ihrem Projekt ein neues Outlook-Formularbereichselement hinzu. Öffnen Sie die CodeBehind-Datei für den neuen Formularbereich, suchen Sie die *YourNewFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen in der Datei, und kopieren Sie diese Klassen in die Zwischenablage.

6. Löschen Sie den neuen Formularbereich, den Sie dem Projekt hinzugefügt haben.

7. Suchen Sie in der CodeBehind-Datei des Formularbereichs, den Sie aktualisieren, damit er im neu ausgerichteten Projekt funktioniert, die *YourOriginalFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen, und ersetzen Sie sie durch den Code, den Sie aus dem neuen Formularbereich kopiert haben.

8. Suchen Sie in den *YourNewFormRegion*`Factory` - und `WindowFormRegionCollection` -Klassen alle Verweise auf die *YourNewFormRegion* -Klasse, und ändern Sie jeden Verweis stattdessen in die *YourOriginalFormRegion* -Kasse. Wenn der aktualisierte Formularbereich z. B. `SalesDataFormRegion` und der neue in Schritt 5 erstellte Formularbereich `FormRegion1`heißt, ändern Sie alle Verweise von `FormRegion1` in `SalesDataFormRegion`.

## <a name="instantiate-form-region-classes"></a>Instanziieren von Formularbereichklassen
 Sie müssen jeden Code ändern, durch den bestimmte Formularbereichsklassen dynamisch instanziiert werden. In Projekten, die auf .NET Framework 3.5 ausgerichtet sind, können Sie Formularbereichklassen wie `Microsoft.Office.Tools.Outlook.FormRegionManifest` direkt instanziieren. In Projekten, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind, sind diese Klassen Schnittstellen, die Sie nicht direkt instanziieren können.

 Wenn das Zielframework des Projekts in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher geändert wird, müssen Sie die Schnittstellen mithilfe von Methoden instanziieren, die von der `Globals.Factory`-Eigenschaft bereitgestellt werden. Weitere Informationen zu den `Globals.Factory` -Eigenschaft finden Sie unter [Global den Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).

 In der folgenden Tabelle sind die Formularbereichstypen und die Methode aufgeführt, die zum Instanziieren der Typen in Projekten verwendet wird, die auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ausgerichtet sind.

|Typ|Zu verwendende Factorymethode|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Siehe auch
- [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)
