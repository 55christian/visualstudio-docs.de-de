---
title: Text im Dokument mithilfe der Schaltfläche im Textfeld angezeigt.
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text boxes, displaying text in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f3c467abcee8fb4faafd2da06ba261e7f3039fe
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328756"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-document-using-a-button"></a>Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche
  In dieser exemplarischen Vorgehensweise wird die Verwendung von Schaltflächen und Textfeldern in einer Anpassung auf Dokumentebene für Microsoft Office Word beschrieben.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen von Steuerelementen zum Word-Dokument in einem Projekt auf Dokumentebene zur Entwurfszeit

- Auffüllen eines Textfelds beim Klicken auf eine Schaltfläche

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Erstellen eines Projekts
 Im ersten Schritt wird ein Word-Dokumentprojekt erstellt.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Word-Dokumentprojekt mit dem Namen **My Word Button**. Wählen Sie im Assistenten **ein neues Dokument erstellen**.

     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet das neue Word-Dokument im Designer und fügt die **My Word Button** Projekt **Projektmappen-Explorer**.

## <a name="add-controls-to-the-word-document"></a>Hinzufügen von Steuerelementen zum Word-Dokument
 Die Steuerelemente der Benutzeroberfläche umfassen eine Schaltfläche und ein Textfeld für das Word-Dokument.

### <a name="to-add-a-button-and-a-text-box"></a>So fügen Sie eine Schaltfläche und ein Textfeld hinzu

1. Stellen Sie sicher, dass das Dokument im Visual Studio-Designer geöffnet ist.

2. Aus der **Standardsteuerelementen** Registerkarte die **Toolbox**, ziehen Sie eine <xref:Microsoft.Office.Tools.Word.Controls.TextBox> Steuerelement auf das Dokument.

   > [!NOTE]
   > In Word werden Steuerelemente standardmäßig in einer Reihe mit Text abgelegt. Sie können anpassen, wie Steuerelemente und Formobjekte eingefügt werden, indem Sie auf die Standardeinstellung ändern der **bearbeiten** Registerkarte die **Optionen** in Word im Dialogfeld.

3. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

4. Suchen **TextBox1** in die **Eigenschaften** Fenster Dropdown-Listenfeld, und Ändern der **Namen** Eigenschaft des Textfelds in **DisplayText**.

5. Ziehen Sie eine **Schaltfläche** -Steuerelement auf das Dokument, und ändern Sie die folgenden Eigenschaften.

   |Eigenschaft|Wert|
   |--------------|-----------|
   |**Name**|**insertText**|
   |**Text**|**Einfügen von Text**|

   Jetzt können Sie den Code schreiben, der beim Klicken auf die Schaltfläche ausgeführt wird.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Füllen Sie im Textfeld aus, wenn die Schaltfläche geklickt wird
 Jedes Mal, wenn der Benutzer auf die Schaltfläche klickt **Hello World!** wird in das Textfeld hinzugefügt.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>So schreiben Sie beim Klicken auf die Schaltfläche in das Textfeld

1. In **Projektmappen-Explorer**, mit der rechten Maustaste **ThisDocument**, und klicken Sie dann auf **Ansichtscode** im Kontextmenü auf.

2. Fügen Sie dem <xref:System.Windows.Forms.Control.Click>-Ereignishandler der Schaltfläche den folgenden Code hinzu:

     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]

3. In C# müssen Sie dem <xref:Microsoft.Office.Tools.Word.Document.Startup>-Ereignis einen Ereignishandler für die Schaltfläche hinzufügen. Informationen zum Erstellen von Ereignishandlern finden Sie unter [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]

## <a name="test-the-application"></a>Testen der Anwendung
 Sie können jetzt testen, das Dokument, um sicherzustellen, dass die Nachricht **Hello World!** wird in das Textfeld angezeigt, wenn Sie die Schaltfläche klicken.

### <a name="to-test-your-document"></a>So testen Sie das Dokument

1. Drücken Sie **F5** um Ihr Projekt auszuführen.

2. Klicken Sie auf die Schaltfläche.

3. Überprüfen Sie, ob **Hallo Welt!** wird in das Textfeld angezeigt.

## <a name="next-steps"></a>Nächste Schritte
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Word-Dokumenten. Die folgenden Aufgaben könnten sich daran anschließen:

- Verwenden eines Kombinationsfelds zum Ändern der Formatierung. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Änderung dokumentformatierung mit CheckBox-Steuerelementen](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

- Auswählen von Diagrammformaten mithilfe von Optionsfeldern. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Optionsfeldern](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Siehe auch
- [Windows Forms-Steuerelemente in Office-Dokumente – Übersicht](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Exemplarische Vorgehensweisen mit Word](../vsto/walkthroughs-using-word.md)
- [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)
- [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
