---
title: 'Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26eb7e0798fbcf6aad33dd45892a23fb0d54b812
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575701"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Vorgehensweise: Programmgesteuertes Überprüfen der Rechtschreibung in Dokumenten
  Verwenden Sie zum Überprüfen der Rechtschreibung in einem Dokument die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> Methode. Diese Methode gibt einen booleschen Wert, der angibt, ob der angegebene Parameter richtig geschrieben ist.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Überprüfen der Rechtschreibung und Ergebnisse in einem Meldungsfeld anzeigen

1. Rufen Sie die <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> Methode und übergeben sie einen Textbereich zu prüfen, Rechtschreibfehler. Wenn Sie dieses Codebeispiel verwenden möchten, führen Sie es aus der Klasse `ThisDocument` oder `ThisAddIn` in Ihrem Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
