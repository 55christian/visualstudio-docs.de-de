---
title: 'Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e05bd9173b83ec3303a058dcf61ea48a7ef7675c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438573"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-XML
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie zum Erstellen einer benutzerdefinierten Menübandregisterkarte mit den **Menüband (XML)** Element.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Schaltflächen auf der **-Add-Ins** Registerkarte. Die **-Add-Ins** Registerkarte ist die Standardeinstellung, die in der Menüband-XML-Datei definiert ist.

- Automatisieren von Microsoft Office Word mithilfe der Schaltflächen auf der **-Add-Ins** Registerkarte.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Erstellen eines Projekts
 Der erste Schritt besteht im Erstellen eines VSTO-Add-In-Projekts für Word. Später passen Sie die **-Add-Ins** Registerkarte dieses Dokuments.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie eine **Word-Add-in** Projekt mit dem Namen **MyRibbonAddIn**.

     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Öffnet die **"ThisAddIn.cs"** oder **"ThisAddIn.vb"** Codedatei und fügt die **MyRibbonAddIn** Projekt **Projektmappen-Explorer**.

## <a name="create-the-vsto-add-ins-tab"></a>Erstellen Sie die Registerkarte "VSTO-Add-ins"
 Zum Erstellen der **-Add-Ins** hinzu eine **Menüband (XML)** Element zu Ihrem Projekt. Später in dieser exemplarischen Vorgehensweise werden Sie dieser Registerkarte einige Schaltflächen hinzufügen.

### <a name="to-create-the-add-ins-tab"></a>Erstellen Sie die Registerkarte "Add-Ins"

1. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

2. In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Menüband (XML)**.

3. Ändern Sie den Namen des neuen Menübands in **MyRibbon**, und klicken Sie dann auf **Hinzufügen**.

     Die **MyRibbon.cs** oder **MyRibbon.vb** Datei wird im Designer geöffnet. Eine XML-Datei mit dem Namen **MyRibbon.xml** auch aus dem Projekt hinzugefügt.

4. In **Projektmappen-Explorer**, mit der rechten Maustaste **"ThisAddIn.cs"** oder **"ThisAddIn.vb"**, und klicken Sie dann auf **Ansichtscode**.

5. Fügen Sie der Klasse **ThisAddin** den folgenden Code hinzu. Mit diesem Code wird die `CreateRibbonExtensibilityObject`-Methode überschrieben und der Office-Anwendung die Menüband-XML-Klasse zurückgegeben.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. In **Projektmappen-Explorer**, mit der rechten Maustaste die **MyRibbonAddIn** Projekt, und klicken Sie dann auf **erstellen**. Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.

## <a name="add-buttons-to-the-add-ins-tab"></a>Hinzufügen von Schaltflächen auf der Registerkarte "Add-Ins"
 Das Ziel dieses VSTO-Add-Ins besteht darin, Benutzern eine Möglichkeit bereitzustellen, dem aktiven Dokument Textbausteine und eine bestimmte Tabelle hinzuzufügen. Um die Benutzeroberfläche zu gewährleisten, fügen Sie zwei Schaltflächen, um die **-Add-Ins** Registerkarte durch Ändern der Menüband-XML-Datei. Später in dieser exemplarischen Vorgehensweise definieren Sie Rückrufmethoden für die Schaltflächen. Weitere Informationen über die Menüband-XML-Datei finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Die Registerkarte "Add-Ins" Schaltflächen hinzu

1. In **Projektmappen-Explorer**, mit der rechten Maustaste **MyRibbon.xml** , und klicken Sie dann auf **öffnen**.

2. Ersetzen Sie den Inhalt von der **Registerkarte** -Element mit dem folgenden XML-Code. Dieser XML-Code ändert die Bezeichnung der Standardsteuerelementgruppe in **Content**, und fügt zwei neue Schaltflächen mit den Bezeichnungen **Text einfügen** und **Tabelle einfügen**.

    ```xml
    <tab idMso="TabAddIns">
        <group id="ContentGroup" label="Content">
            <button id="textButton" label="Insert Text"
                 screentip="Text" onAction="OnTextButton"
                 supertip="Inserts text at the cursor location."/>
            <button id="tableButton" label="Insert Table"
                 screentip="Table" onAction="OnTableButton"
                 supertip="Inserts a table at the cursor location."/>
        </group>
    </tab>
    ```

## <a name="automate-the-document-by-using-the-buttons"></a>Automatisieren Sie das Dokument mithilfe der Schaltflächen
 Müssen Sie hinzufügen, `onAction` Rückrufmethoden für die **Text einfügen** und **Tabelle einfügen** Schaltflächen, Aktionen auszuführen, wenn der Benutzer darauf klickt. Weitere Informationen über Rückrufmethoden für Menübandsteuerelemente finden Sie unter [Menüband-XML-](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>So fügen Sie Rückrufmethoden für die Schaltflächen hinzu

1. In **Projektmappen-Explorer**, mit der rechten Maustaste **MyRibbon.cs** oder **MyRibbon.vb**, und klicken Sie dann auf **öffnen**.

2. Fügen Sie den folgenden Code am Anfang der **MyRibbon.cs** oder **MyRibbon.vb** Datei. Dieser Code erstellt einen Alias für den Namespace <xref:Microsoft.Office.Interop.Word>.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. Fügen Sie der `MyRibbon` -Klasse die folgende Methode hinzu. Dies ist eine Rückrufmethode für die **Text einfügen** Schaltfläche, eine Zeichenfolge mit dem aktiven Dokument an der aktuellen Position des Cursors hinzugefügt.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. Fügen Sie der `MyRibbon` -Klasse die folgende Methode hinzu. Dies ist eine Rückrufmethode für die **Tabelle einfügen** Schaltfläche, eine Tabelle mit dem aktiven Dokument an der aktuellen Position des Cursors hinzugefügt.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>Testen des VSTO-Add-Ins
 Beim Ausführen des Projekts, Word geöffnet und die Registerkarte mit dem Namen **-Add-Ins** im Menüband angezeigt wird. Klicken Sie auf die **Text einfügen** und **Tabelle einfügen** Schaltflächen auf der **-Add-Ins** Tab, um den Code zu testen.

### <a name="to-test-your-vsto-add-in"></a>So testen Sie Ihr VSTO-Add-In

1. Drücken Sie **F5** um Ihr Projekt auszuführen.

2. Überprüfen Sie, ob die **-Add-Ins** Registerkarte auf dem Menüband angezeigt wird.

3. Klicken Sie auf die Registerkarte **Add-Ins** .

4. Überprüfen Sie, ob die **Content** Gruppe auf dem Menüband angezeigt wird.

5. Klicken Sie auf die **Text einfügen** Schaltfläche der **Content** Gruppe.

     Eine Zeichenfolge wird dem Dokument an der aktuellen Position des Cursors hinzugefügt.

6. Klicken Sie auf die **Tabelle einfügen** Schaltfläche der **Content** Gruppe.

     Eine Tabelle wird dem Dokument an der aktuellen Position des Cursors hinzugefügt.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zum Anpassen der Office-Benutzeroberfläche finden Sie in diesen Themen:

- Anpassen des Menübands einer anderen Office-Anwendung. Weitere Informationen zu den Anwendungen, die Anpassung des Menübands unterstützen, finden Sie unter [Übersicht über das Menüband](../vsto/ribbon-overview.md).

- Anpassen des Menüband einer Office-Anwendung mithilfe des Menüband-Designers an. Weitere Informationen finden Sie unter [Ribbon Designer](../vsto/ribbon-designer.md).

- Erstellen eines benutzerdefinierten Aktionsbereichs. Weitere Informationen finden Sie unter [aktionsbereichsübersicht](../vsto/actions-pane-overview.md).

- Anpassen der Benutzeroberfläche von Microsoft Office Outlook mithilfe von Outlook-Formularbereichen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Entwerfen ein Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>Siehe auch
- [Übersicht über das Menüband](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
