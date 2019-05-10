---
title: 'Vorgehensweise: Programmgesteuertes Hinzufügen von Grafiken und WordArt zu Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f805153a35517c473e95beb871ae7d12a2776bd4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967607"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Vorgehensweise: Programmgesteuertes Hinzufügen von Grafiken und WordArt zu Dokumenten
  Sie können Ihren Dokumenten zur Entwurfszeit oder zur Laufzeit Bilder und Zeichnungsobjekte hinzufügen. Mithilfe von WordArt können Sie Microsoft Office Word-Dokumenten dekorativen Text hinzufügen. Diese Spezialeffekte für Text sind Zeichnungsobjekte, die Sie anpassen und in Ihr Dokument einfügen können.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Hinzufügen eines Bilds zur Entwurfszeit
 Wenn Sie eine Anpassung auf Dokumentebene entwickeln, können Sie dem Dokument zur Entwurfszeit ein Bild hinzufügen.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>So fügen Sie einem Word-Dokument zur Entwurfszeit ein Bild hinzu

1. Platzieren Sie den Cursor an der Stelle, an der Sie das Bild in das Dokument einfügen möchten.

2. Klicken Sie auf die **einfügen** Registerkarte des Menübands.

3. In der **Abbildungen** auf **Bild**.

4. In der **Bild einfügen** Dialogfeld, navigieren Sie zu dem Bild eingefügt werden soll, und klicken Sie auf **einfügen**.

     Das Bild wird dem Dokument an der aktuellen Cursorposition hinzugefügt.

## <a name="add-a-picture-at-runtime"></a>Hinzufügen eines Bildes zur Laufzeit
 Sie können ein Bild an der aktuellen Cursorposition in ein Dokument einfügen.

### <a name="to-add-a-picture-at-the-cursor-location"></a>So fügen Sie ein Bild an der Cursorposition hinzu

1. Rufen Sie die <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A>-Methode der <xref:Microsoft.Office.Interop.Word.InlineShapes>-Auflistung auf, und übergeben Sie den Namen der Datei.

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>Hinzufügen von WordArt zur Entwurfszeit
 Wenn Sie eine Anpassung auf Dokumentebene entwickeln, können Sie dem Dokument zur Entwurfszeit WordArt hinzufügen.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>So fügen Sie einem Word-Dokument zur Entwurfszeit WordArt hinzu

1. Platzieren Sie den Cursor an der Stelle, an der Sie WordArt in das Dokument einfügen möchten.

2. Klicken Sie auf die **einfügen** Registerkarte des Menübands.

3. In der **Text** auf **WordArt**, und wählen Sie dann ein WordArt-Format.

4. Fügen Sie den Text, der im Dokument angezeigt werden sollen die **WordArt-Text bearbeiten** Dialogfeld und klicken Sie auf **OK**.

     Der Text wird dem Dokument mit dem ausgewählten WordArt-Format hinzugefügt.

## <a name="add-wordart-at-runtime"></a>Hinzufügen von WordArt zur Laufzeit
 Sie können WordArt an der aktuellen Cursorposition in ein Dokument einfügen. Die Verfahren unterscheiden sich für Anpassungen auf Dokumentebene und VSTO-Add-Ins.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>So fügen Sie WordArt in einer Anpassung auf Dokumentebene an der Cursorposition hinzu

1. Rufen Sie die linke und obere Position der aktuellen Cursorposition ab.

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2. Rufen Sie die <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A>-Methode des <xref:Microsoft.Office.Interop.Word.Shapes>-Objekts im Dokument auf.

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>So fügen Sie WordArt in einem VSTO-Add-In an der Cursorposition hinzu

1. Rufen Sie die linke und obere Position der aktuellen Cursorposition ab.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2. Rufen Sie die <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A>-Methode des <xref:Microsoft.Office.Interop.Word.Shapes>-Objekts des aktiven Dokuments (oder eines anderen angegebenen Dokuments) auf.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>Kompilieren des Codes

- Ein Bild mit dem Namen *SamplePicture.jpg* muss vorhanden sein, auf Laufwerk C.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md)
- [Vorgehensweise: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Vorgehensweise: Programmgesteuertes Wiederherstellen der Auswahl nach Suchvorgängen](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Vorgehensweise: Programmgesteuertes Speichern von Dokumenten](../vsto/how-to-programmatically-save-documents.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
