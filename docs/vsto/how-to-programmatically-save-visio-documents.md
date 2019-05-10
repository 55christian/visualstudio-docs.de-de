---
title: 'Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 85a45da13594a6f204e91f93ddcee64acb29c493
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419388"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Vorgehensweise: Programmgesteuertes Speichern von Visio-Dokumenten
  Es gibt mehrere Methoden zum Speichern von Microsoft Office Visio-Dokumenten:

- Speichern von Änderungen in einem vorhandenen Dokument

- Speichern eines neuen Dokuments oder Speichern eines Dokuments unter einem neuen Namen

- Speichern eines Dokuments mit angegebenen Argumenten

  Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die Methoden [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) , [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) und [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) .

## <a name="save-an-existing-document"></a>Speichern Sie ein vorhandenes Dokument

### <a name="to-save-a-document"></a>So speichern Sie einen Dokument

- Rufen Sie die `Microsoft.Office.Interop.Visio.Document.Save`-Methode der `Microsoft.Office.Tools.Visio.Document`-Klasse eines zuvor gespeicherten Dokuments auf.

     Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.

    > [!NOTE]
    > Die `Microsoft.Office.Interop.Visio.Document.Save`-Methode löst eine Ausnahme aus, falls ein neues Visio-Dokument noch nicht gespeichert wurde.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]

## <a name="save-a-document-with-a-new-name"></a>Speichern Sie ein Dokument mit einem neuen Namen.
 Verwenden Sie die `Microsoft.Office.Interop.Visio.Document.SaveAs`-Methode, um ein neues Dokument oder ein Dokument unter einem neuen Namen zu speichern. Diese Methode erfordert, dass Sie den neuen Dateinamen angeben.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>So speichern Sie das aktive Visio-Dokument unter einem neuen Namen

- Rufen Sie die `Microsoft.Office.Interop.Visio.Document.SaveAs`-Methode des zu speichernden `Microsoft.Office.Tools.Visio.Document` aus, indem Sie einen vollqualifizierten Pfad einschließlich eines Dateinamens verwenden. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird die Datei automatisch überschrieben.

     Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Speichern eines Dokuments unter einem neuen Namen und den angegebenen Argumenten
 Verwenden Sie die `Microsoft.Office.Interop.Visio.Document.SaveAsEx`-Methode, um ein Dokument unter einem neuen Namen zu speichern, und geben Sie ggf. auf das Dokument anwendbare Argumente an.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>So speichern Sie ein Dokument unter einem neuen Namen und mit angegebenen Argumenten

- Rufen Sie die `Microsoft.Office.Interop.Visio.Document.SaveAsEx`-Methode des zu speichernden `Microsoft.Office.Tools.Visio.Document` aus, indem Sie einen vollqualifizierten Pfad einschließlich eines Dateinamens verwenden. Wenn der Ordner bereits eine Datei dieses Namens enthält, wird eine Ausnahme ausgelöst.

     Im folgenden Codebeispiel wird das aktive Dokument unter einem neuen Namen gespeichert, das Dokument als schreibgeschützt markiert und in der Liste zuletzt verwendeter Dokumente angezeigt. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Codebeispiel benötigen Sie Folgendes:

- Zum Speichern eines Dokuments, das einen neuen Namen verfügt, ein Verzeichnis namens `Test` Wohnsitz in die *eigene* Ordner (für Windows XP und früher) oder die *Dokumente* Ordner (für Windows Vista).

## <a name="see-also"></a>Siehe auch
- [Visio-Projektmappen](../vsto/visio-solutions.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Vorgehensweise: Programmgesteuertes Erstellen Sie Neuer Visio-Dokumente](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Öffnen von Visio-Dokumenten](../vsto/how-to-programmatically-open-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Schließen von Visio-Dokumenten](../vsto/how-to-programmatically-close-visio-documents.md)
- [Vorgehensweise: Programmgesteuertes Drucken von Visio-Dokumenten](../vsto/how-to-programmatically-print-visio-documents.md)
