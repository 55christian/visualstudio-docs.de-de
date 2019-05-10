---
title: 'Vorgehensweise: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25b30db78706dce95188289187ce55011ce1362d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441741"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Vorgehensweise: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen
  Wenn Sie einen Teil eines Dokuments schützen, verhindern Sie, dass Benutzer Inhalte in diesem Teil des Dokuments ändern oder löschen. Es gibt mehrere Möglichkeiten, Teile eines Microsoft Office Word-Dokuments mithilfe von Inhaltssteuerelementen zu schützen.

- Sie können ein Inhaltssteuerelement schützen.

- Sie können einen Teil eines Dokuments schützen, der nicht in einem Inhaltssteuerelement enthalten ist.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="EditDeleteControl"></a> Schützen Sie ein ContentControl-Element
 Sie können verhindern, dass Benutzer bearbeiten oder löschen ein ContentControl-Element, durch Festlegen von Eigenschaften des Steuerelements in einem Projekt auf Dokumentebene zur Entwurfszeit oder zur Laufzeit.

 Sie können auch Inhaltssteuerelemente schützen, die Sie einem Dokument zur Laufzeit hinzufügen, indem Sie ein VSTO-Add-In-Projekt verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>So schützen Sie ein Inhaltssteuerelement zur Entwurfszeit

1. Wählen Sie in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Designer gehosteten Dokument das Inhaltssteuerelement aus, das Sie schützen möchten.

2. In der **Eigenschaften** Fenster legen Sie eine oder beide der folgenden Eigenschaften:

    - Um zu verhindern, dass Benutzer das Steuerelement bearbeiten, legen Sie **LockContents** zu **"true"**.

    - Um zu verhindern, dass Benutzer das Steuerelement löschen, legen Sie **LockContentControl** zu **"true"**.

3. Klicken Sie auf **OK**.

### <a name="to-protect-a-content-control-at-runtime"></a>Um ein Inhaltssteuerelement zur Laufzeit zu schützen.

1. Festlegen der `LockContents` Eigenschaft des Inhaltssteuerelements auf **"true"** zu verhindern, dass Benutzer das Steuerelement bearbeiten, und legen Sie die `LockContentControl` Eigenschaft **"true"** verhindert, dass Benutzer das Steuerelement löschen.

     Das folgende Codebeispiel veranschaulicht die Verwendung der <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A>-Eigenschaft und <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A>-Eigenschaft zwei verschiedener <xref:Microsoft.Office.Tools.Word.RichTextContentControl>-Objekte in einem Projekt auf Dokumentebene. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument` -Klasse in Ihrem Projekt hinzu und rufen die `AddProtectedContentControls` -Methode aus dem `ThisDocument_Startup` -Ereignishandler auf.

     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]

     Das folgende Codebeispiel veranschaulicht die Verwendung der <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A>-Eigenschaft und <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A>-Eigenschaft zwei verschiedener <xref:Microsoft.Office.Tools.Word.RichTextContentControl>-Objekte in einem VSTO-Add-In-Projekt. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn` -Klasse in Ihrem Projekt hinzu und rufen die `AddProtectedContentControls` -Methode aus dem `ThisAddIn_Startup` -Ereignishandler auf.

     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Schützen Sie einen Teil eines Dokuments, die nicht in einem Inhaltssteuerelement enthalten ist
 Sie können verhindern, dass Benutzer einen Bereich eines Dokuments ändern, indem Sie ihn in <xref:Microsoft.Office.Tools.Word.GroupContentControl> einfügen. Dies ist in den folgenden Szenarien nützlich:

- Sie möchten einen Bereich schützen, der keine Inhaltssteuerelemente enthält.

- Sie möchten einen Bereich schützen, der bereits Inhaltssteuerelemente enthält, während der Text oder andere Elemente, die Sie schützen möchten, nicht in den Inhaltssteuerelementen enthalten sind.

> [!NOTE]
> Wenn Sie ein <xref:Microsoft.Office.Tools.Word.GroupContentControl> erstellen, das eingebettete Inhaltssteuerelemente enthält, sind die eingebetteten Inhaltssteuerelemente nicht automatisch geschützt. Um zu verhindern, dass Benutzer ein eingebettetes Inhaltssteuerelement bearbeiten, verwenden Sie die **LockContents** -Eigenschaft des Steuerelements.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>So schützen Sie einen Bereich eines Dokuments zur Entwurfszeit

1. Wählen Sie in dem im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Designer gehosteten Dokument den Bereich aus, den Sie schützen möchten.

2. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. In der **Steuerelemente** gruppieren, klicken Sie auf die **Gruppe** Dropdown-Schaltfläche, und klicken Sie dann auf **Gruppe**.

     In der `ThisDocument`-Klasse in Ihrem Projekt wird automatisch ein <xref:Microsoft.Office.Tools.Word.GroupContentControl> generiert, das den geschützten Bereich enthält. Ein Rahmen, der das Gruppensteuerelement stellt zur Entwurfszeit sichtbar ist, aber es gibt keinen sichtbaren Rahmen zur Laufzeit.

### <a name="to-protect-an-area-of-a-document-at-runtime"></a>So schützen Sie einen Bereich eines Dokuments zur Laufzeit

1. Wählen Sie den zu schützenden Bereich programmgesteuert aus, und rufen Sie dann die <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A>-Methode auf, um <xref:Microsoft.Office.Tools.Word.GroupContentControl> zu erstellen.

     Im folgenden Codebeispiel für ein Projekt auf Dokumentebene wird dem ersten Absatz des Dokuments Text hinzugefügt, der erste Absatz ausgewählt und dann <xref:Microsoft.Office.Tools.Word.GroupContentControl> instanziiert. Um diesen Code auszuführen, fügen Sie ihn der `ThisDocument` -Klasse in Ihrem Projekt hinzu und rufen die `ProtectFirstParagraph` -Methode aus dem `ThisDocument_Startup` -Ereignishandler auf.

     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]

     Im folgenden Codebeispiel für ein VSTO-Add-In-Projekt wird dem ersten Absatz des aktiven Dokuments Text hinzugefügt, der erste Absatz ausgewählt und dann <xref:Microsoft.Office.Tools.Word.GroupContentControl> instanziiert. Um diesen Code auszuführen, fügen Sie ihn der `ThisAddIn` -Klasse in Ihrem Projekt hinzu und rufen die `ProtectFirstParagraph` -Methode aus dem `ThisAddIn_Startup` -Ereignishandler auf.

     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]

## <a name="see-also"></a>Siehe auch
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [ContentControl-Elemente](../vsto/content-controls.md)
- [Vorgehensweise: Hinzufügen von Inhaltssteuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
