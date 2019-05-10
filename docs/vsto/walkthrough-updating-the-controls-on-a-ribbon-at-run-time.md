---
title: 'Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e293a0136e6ae2d8b6a6747201e484fdea43f91e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62981113"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-runtime"></a>Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit

In dieser exemplarischen Vorgehensweise veranschaulicht, wie die Menüband-Objektmodells zum Aktualisieren der Steuerelemente auf einem Menüband, nachdem das Menüband in der Office-Anwendung geladen wird.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Das Beispiel ruft Daten aus der Beispieldatenbank "Northwind" ab, um ein Kombinationsfeld und ein Menü in Microsoft Office Outlook mit Daten aufzufüllen. Elemente, die Sie automatisch in diesen Steuerelementen auswählen, füllen Felder wie z. B. **zu** und **Betreff** einer e-Mail-Nachricht.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen Sie ein neues Outlook VSTO-Add-in-Projekt.

- Entwerfen einer benutzerdefinierten Menübandgruppe.

- Fügen Sie der benutzerdefinierten Gruppe zu einer integrierten Registerkarte hinzu.

- Aktualisieren Sie die Steuerelemente auf dem Menüband zur Laufzeit.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Erstellen eines neuen Outlook VSTO-Add-in-Projekts

Erstellen Sie zunächst ein neues Outlook VSTO-Add-In-Projekt.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>So erstellen Sie ein neues Outlook VSTO-Add-In-Projekt

1. In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], erstellen Sie ein Outlook VSTO-Add-in-Projekt mit dem Namen **"Ribbon_Update_At_Runtime"**.

2. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Projektmappenverzeichnis erstellen**aus.

3. Speichern Sie das Projekt im Standardprojektverzeichnis.

     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Entwerfen einer benutzerdefinierten Menübandgruppe

Das Menüband in diesem Beispiel wird angezeigt, wenn ein Benutzer eine neue e-Mail-Nachricht verfasst. Um eine benutzerdefinierte Gruppe für die Multifunktionsleiste zu erstellen, ein Menübandelement zunächst Ihrem Projekt hinzufügen, und dann die Gruppe im Menüband-Designer entwerfen. Diese benutzerdefinierte Gruppe können Sie das Generieren von nachverfolgungs-e-Mail-Nachrichten an den Kunden durch Abrufen der Namen und Auftragsverläufe aus einer Datenbank.

### <a name="to-design-a-custom-group"></a>So entwerfen Sie eine benutzerdefinierte Gruppe

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband (Visueller Designer)** aus.

3. Ändern Sie den Namen des neuen Menübands in **CustomerRibbon**, und klicken Sie dann auf **hinzufügen**.

     Die *CustomerRibbon.cs* oder *CustomerRibbon.vb* im Menüband-Designer wird geöffnet und zeigt eine standardmäßige Registerkarte und Gruppe.

4. Klicken Sie auf den Menüband-Designer, um diese auszuwählen.

5. In der **Eigenschaften** Fenster, klicken Sie auf den Dropdownpfeil neben der **RibbonType** -Eigenschaft, und klicken Sie dann auf **Microsoft.Outlook.Mail.Compose**.

     Dadurch wird das Menüband angezeigt wird, wenn der Benutzer eine neue e-Mail in Outlook verfasst.

6. Klicken Sie im Menüband-Designer auf **Group1** um es auszuwählen.

7. In der **Eigenschaften** legen **Bezeichnung** zu **Kundenbestellungen**.

8. Von der **Steuerelemente für Office-Menübänder** Registerkarte die **Toolbox**, ziehen Sie eine **"ComboBox"** auf die **Kundenbestellungen** Gruppe.

9. Klicken Sie auf **ComboBox1** um es auszuwählen.

10. In der **Eigenschaften** legen **Bezeichnung** zu **Kunden**.

11. Aus der **Steuerelemente für Office-Menübänder** Registerkarte die **Toolbox**, ziehen Sie eine **Menü** auf die **Kundenbestellungen** Gruppe.

12. In der **Eigenschaften** legen **Bezeichnung** zu **Produkt gekauft**.

13. Legen Sie **dynamische** zu **"true"**.

     Dadurch können Sie zum Hinzufügen und entfernen Steuerelemente im Menü zur Laufzeit aus, nachdem das Menüband in der Office-Anwendung geladen wird.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Fügen Sie der benutzerdefinierten Gruppe zu einer integrierten Registerkarte hinzu.

Eine integrierte Registerkarte ist eine Registerkarte, die bereits auf dem Menüband einer Outlook Explorer- oder Inspektor ist. In diesem Verfahren fügen Sie die benutzerdefinierte Gruppe einer integrierten Registerkarte hinzu und geben dann die Position der benutzerdefinierten Gruppe auf der Registerkarte an.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>So fügen Sie die benutzerdefinierte Gruppe einer integrierten Registerkarte hinzu

1. Klicken Sie auf die **TabAddins (integriert)** Tab, um es auszuwählen.

2. In der **Eigenschaften** Fenster, erweitern Sie die **ControlId** -Eigenschaft, und legen **OfficeId** zu **"TabNewMailMessage" fest**.

     Dadurch wird die **Kundenbestellungen** Gruppe der **Nachrichten** Registerkarte des Menübands, die in einer neuen e-Mail-Nachricht angezeigt wird.

3. Klicken Sie auf die **Kundenbestellungen** Gruppe, um es auszuwählen.

4. In der **Eigenschaften** Fenster, erweitern Sie die **Position** -Eigenschaft, klicken Sie auf den Dropdownpfeil neben der **PositionType** -Eigenschaft, und klicken Sie dann auf  **BeforeOfficeId**.

5. Legen Sie die **OfficeId** Eigenschaft **"GroupClipboard" fest**.

     Dies positioniert die **Kundenbestellungen** vor der Gruppe der **Zwischenablage** Gruppe der **Nachrichten** Registerkarte.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle

Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.

### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.

     Dies startet den **Assistenten zur Datenquellenkonfiguration**.

2. Wählen Sie **Datenbank**, und klicken Sie dann auf **Weiter**.

3. Wählen Sie **Dataset**, und klicken Sie dann auf **Weiter**.

4. Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank Microsoft SQL Server Compact 4.0, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.

5. Nachdem eine Verbindung ausgewählt oder erstellt wurde, klicken Sie auf **Weiter**.

6. Klicken Sie auf **Weiter** um die Verbindungszeichenfolge zu speichern.

7. Auf der **Datenbankobjekte auswählen** Seite **Tabellen**.

8. Aktivieren Sie das Kontrollkästchen neben jeder der folgenden Tabellen:

    1. **Kunden**

    2. **Auftragsdetails**

    3. **Aufträge**

    4. **Produkte**

9. Klicken Sie auf **Fertig stellen**.

## <a name="update-controls-in-the-custom-group-at-runtime"></a>Aktualisieren der Steuerelemente in der benutzerdefinierten Gruppe zur Laufzeit

Verwenden Sie Menüband-Objektmodell, um die folgenden Aufgaben auszuführen:

- Hinzufügen von Kundennamen, die **Kunden** im Kombinationsfeld.

- Hinzufügen von Menüs und Schaltflächen-Steuerelemente, die **gekaufte Produkte** Menü, das Darstellen von Bestellungen und Produkte verkauft.

- Füllen Sie die für Betreff und Text Felder neuer e-Mail-Nachrichten mit Daten aus der **Kunden** im Kombinationsfeld und **gekaufte Produkte** Menü.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>So aktualisieren Sie Steuerelemente in der benutzerdefinierten Gruppe mithilfe des Menüband-Objektmodells

1. Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen** .

2. In der **Verweis hinzufügen** Dialogfeld klicken Sie auf die **.NET** Registerkarte die **System.Data.Linq** Assembly, und klicken Sie dann auf **OK**.

    Diese Assembly enthält Klassen für die Verwendung von LINQ (Language-Integrated Queries). Sie verwenden LINQ zum Auffüllen der Steuerelemente in der benutzerdefinierten Gruppe mit Daten aus der Datenbank "Northwind".

3. In **Projektmappen-Explorer**, klicken Sie auf **CustomerRibbon.cs** oder **CustomerRibbon.vb** um es auszuwählen.

4. Auf der **Ansicht** Menü klicken Sie auf **Code**.

    Die Menüband-Codedatei wird im Code-Editor geöffnet.

5. Fügen Sie am Anfang der Menüband-Codedatei die folgenden Anweisungen hinzu. Diese Anweisungen ermöglichen den einfachen Zugriff auf LINQ-Namespaces und den Namespace der primären Interopassembly (PIA) von Outlook.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Fügen Sie den folgenden Code innerhalb der `CustomerRibbon` Klasse. Dieser Code deklariert die Datentabelle und die Tabellenadapter, die Sie zum Speichern von Informationen aus den Kunden-, Bestellungen-, Bestelldetails- und Produkttabellen der Datenbank "Northwind" verwenden.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Fügen Sie der Klasse `CustomerRibbon` den folgenden Codeblock hinzu. Dieser Code fügt drei Hilfsmethoden, die Steuerelemente für die Multifunktionsleiste zur Laufzeit zu erstellen.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. Ersetzen Sie die `CustomerRibbon_Load`-Ereignishandlermethode durch den folgenden Code. Dieser Code verwendet eine LINQ-Abfrage, um die folgenden Aufgaben auszuführen:

   - Füllen Sie die **Kunden** Kombinationsfeld, indem Sie mit dem-ID und die Namen von 20 Kunden in der Northwind-Datenbank.

   - Aufrufen der Hilfsmethode `PopulateSalesOrderInfo`. Diese Methode aktualisiert die **ProductsPurchased** Menü mit Bestellnummern, die den zurzeit ausgewählten Kunden betreffen.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Fügen Sie der `CustomerRibbon` -Klasse folgenden Code hinzu. Dieser Code verwendet LINQ-Abfragen, um die folgenden Aufgaben auszuführen:

   - Hinzufügen eines Untermenüs zum die **ProductsPurchased** Menü für jeden Kaufauftrag im Zusammenhang mit dem ausgewählten Kunden.

   - Hinzufügen von Schaltflächen zu jedem Untermenü für die Produkte, die sich auf die Bestellung beziehen.

   - Hinzufügen von Ereignishandlern zu jeder Schaltfläche.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. In **Projektmappen-Explorer**, doppelklicken Sie auf dem Menüband-Codedatei.

     Der Menüband-Designer wird geöffnet.

11. Doppelklicken Sie im Menüband-Designer auf die **Kunden** im Kombinationsfeld.

     Die Menüband-Codedatei wird im Code-Editor geöffnet, und der `ComboBox1_TextChanged`-Ereignishandler wird angezeigt.

12. Ersetzen Sie den `ComboBox1_TextChanged` -Ereignishandler durch den folgenden Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

    - Aufrufen der Hilfsmethode `PopulateSalesOrderInfo`. Diese Methode aktualisiert die **gekaufte Produkte** Menü mit Bestellungen, die den ausgewählten Kunden betreffen.

    - Aufrufen der Hilfsmethode `PopulateMailItem` und Übergeben des aktuellen Texts, der den Namen des ausgewählten Kunden darstellt. Diese Methode füllt, das für Betreff und Text Felder neuer e-Mail-Nachrichten.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Fügen Sie der `Click` -Klasse den folgenden `CustomerRibbon` -Ereignishandler hinzu. Dieser Code fügt den Namen ausgewählter Produkte dem Feld "Text" Neuer e-Mail-Nachrichten.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Fügen Sie der `CustomerRibbon` -Klasse folgenden Code hinzu. Mit diesem Code werden die folgenden Aufgaben ausgeführt:

    - Füllt die neue e-Mail-Nachrichten an-Zeile mit der e-Mail-Adresse des aktuell ausgewählten Kunden.

    - Fügt Text an den Betreff und Text neuer e-Mail-Nachrichten.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Testen Sie die Steuerelemente in der benutzerdefinierten Gruppe

Wenn Sie ein neues e-Mail-Formular in Outlook öffnen, eine benutzerdefinierte Gruppe mit dem Namen **Kundenbestellungen** angezeigt wird, auf die **Nachrichten** Registerkarte des Menübands.

Erstellen Sie eine Kunden-nachverfolgungs-e-Mail-Nachricht, einen Kunden auswählen, und wählen Sie dann auf vom Kunden erworbenen Produkte. Die Steuerelemente in der **Kundenbestellungen** Gruppe zur Laufzeit mit Daten aus der Northwind-Datenbank aktualisiert werden.

### <a name="to-test-the-controls-in-the-custom-group"></a>So testen Sie die Steuerelemente in der benutzerdefinierten Gruppe

1. Drücken Sie **F5** um Ihr Projekt auszuführen.

     Outlook wird gestartet.

2. In Outlook auf der **Datei** Startmenü **neu**, und klicken Sie dann auf **e-Mail-Nachricht**.

     Die folgenden Aktionen werden ausgeführt:

    - Eine neues Inspektor-Fenster für E-Mail-Nachrichten wird angezeigt.

    - Auf der **Nachricht** Registerkarte des Menübands die **Kundenbestellungen** Gruppe angezeigt wird, bevor Sie die **Zwischenablage** Gruppe.

    - Die **Kunden** Kombinationsfeld, in der Gruppe wird mit den Namen der Kunden in der Northwind-Datenbank aktualisiert.

3. Auf der **Nachricht** Registerkarte des Menübands in die **Kundenbestellungen** gruppieren, wählen Sie einen Kunden aus der **Kunden** im Kombinationsfeld.

     Die folgenden Aktionen werden ausgeführt:

    - Die **gekaufte Produkte** Menü wird aktualisiert, um jeder Auftrag für den ausgewählten Kunden angezeigt.

    - Jedes Bestellungsuntermenü wird so aktualisiert, dass die in der betreffenden Bestellung gekauften Produkte angezeigt werden.

    - Des ausgewählten Kunden-e-Mail-Adresse hinzugefügt, die **zu** Zeile die e-Mail-Nachricht, und der Betreff und Text der e-Mail-Nachricht werden mit Text aufgefüllt.

4. Klicken Sie auf die **Products Purchases** Menü, zeigen Sie auf eine beliebige Bestellung, und klicken Sie dann auf ein Produkt aus der Bestellung.

     Der Produktname wird dem Nachrichtentext der E-Mail-Nachricht hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Anpassen der Office-Benutzeroberfläche finden Sie in diesen Themen:

- Fügen Sie jeder Anpassung auf Dokumentebene kontextbasierte Benutzeroberfläche hinzu. Weitere Informationen finden Sie unter [aktionsbereichsübersicht](../vsto/actions-pane-overview.md).

- Erweitern Sie ein standardmäßiges oder benutzerdefiniertes Microsoft Office Outlook-Formular. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Entwerfen ein Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu Outlook. Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Siehe auch

- [Zugriff auf das Menüband zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)
- [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Menüband-Designer](../vsto/ribbon-designer.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md)
- [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Vorgehensweise: Ändern der Position einer Registerkarte des Menübands](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)
- [Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Vorgehensweise: Add-In-Benutzeroberflächenfehler anzeigen](../vsto/how-to-show-add-in-user-interface-errors.md)