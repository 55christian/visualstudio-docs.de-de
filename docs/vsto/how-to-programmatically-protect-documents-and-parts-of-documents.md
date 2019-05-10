---
title: 'Vorgehensweise: Programmgesteuertes Schützen von Dokumenten und Teilen von Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62d84dcb7ce22f1199d12a958250a465cd25a49c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412457"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Vorgehensweise: Programmgesteuertes Schützen von Dokumenten und Teilen von Dokumenten
  Sie können Schutz zu einem Microsoft Office Word-Dokument hinzufügen, um zu verhindern, dass Benutzer irgendwelche Änderungen an dem Dokument vornehmen können.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Sie können auch bestimmte Bereiche des Dokuments als Ausnahmen markieren, sodass angegebene Benutzer lediglich diese Bereiche des Dokuments bearbeiten können. Beispielsweise könnten Sie ein gesamtes Dokument mit Ausnahme eines bestimmten Lesezeichens schützen. Optional können Sie ein Kennwort hinzufügen, sodass Benutzer den Dokumentschutz nur aufheben können, wenn ihnen das Kennwort bekannt ist.

> [!NOTE]
> Im folgenden Beispiel wird kein Kennwortschutz verwendet. Wenn Sie Dokumentschutz hinzufügen, empfiehlt es sich aber, ein Kennwort zu verwenden. Weitere Informationen finden Sie im Dokumentschutz-Beispiel unter [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md).

 Sie können auch Inhaltssteuerelemente verwenden, um Teile von Dokumenten zu schützen. Weitere Informationen finden Sie unter [Vorgehensweise: Schützen von Teilen von Dokumenten mithilfe von Inhaltssteuerelementen](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Schützen eines Dokuments, das Teil einer Anpassung auf Dokumentebene ist

### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>So schützen Sie ein Dokument, das Bestandteil einer Anpassung auf Dokumentebene ist

1. Rufen Sie in Ihrem Projekt die <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> -Methode der `ThisDocument` -Klasse auf.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>So schließen Sie ein Lesezeichen-Steuerelement vom Dokumentschutz aus

1. Schützen Sie das gesamte Dokument mit der <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> -Methode.

     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]

2. Schließen Sie `Bookmark1` vom Dokumentschutz aus.

     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]

### <a name="compile-the-code"></a>Kompilieren des Codes
 Wenn Sie diese Codebeispiele verwenden möchten, führen Sie sie in Ihrem Projekt aus der `ThisDocument` -Klasse aus. Für diese Codebeispiele wird davon ausgegangen, dass ein <xref:Microsoft.Office.Tools.Word.Bookmark> -Steuerelement namens `Bookmark1` im Dokument vorhanden ist, in dem sich dieser Code befindet.

## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Schützen eines Dokuments mithilfe eines VSTO-Add-Ins

### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>So schützen Sie ein Dokument mithilfe eines VSTO-Add-Ins auf Anwendungsebene

1. Rufen Sie die <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> -Methode des <xref:Microsoft.Office.Interop.Word.Document> -Objekts auf, das Sie schützen möchten.

     Im folgenden Codebeispiel wird das aktive Dokument geschützt. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]

## <a name="see-also"></a>Siehe auch
- [Dokumentschutz in Projektmappen auf Anwendungsebene](../vsto/document-protection-in-document-level-solutions.md)
- [Kennwortschutz für Office-Dokumente](../vsto/password-protection-on-office-documents.md)
- [Vorgehensweise: Zulassen Sie Code Hintergrund von Dokumenten mit eingeschränkten Berechtigungen ausgeführt werden zu.](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Vorgehensweise: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)
