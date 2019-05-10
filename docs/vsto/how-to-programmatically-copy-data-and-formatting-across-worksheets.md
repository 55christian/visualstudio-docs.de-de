---
title: 'Vorgehensweise: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 77feefe7a2d274403e483dbaa3167f53f72ae168
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575298"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Vorgehensweise: Programmgesteuertes Kopieren von Daten und Formatierungen zwischen Arbeitsblättern
  Sie können Kopieren von Daten aus einem Bereich auf einem Blatt in alle übrigen Arbeitsblätter in einer Arbeitsmappe mithilfe der <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> Methode. Geben Sie einen Bereich, und Kopieren von Daten, formatieren oder beides werden sollen.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Beispiel
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Dieses Beispiel erfordert einen Bereich mit dem Namen `rangeData` in einem Arbeitsblatt.

## <a name="see-also"></a>Siehe auch
- [Arbeiten mit Arbeitsblättern](../vsto/working-with-worksheets.md)
- [Vorgehensweise: Programmgesteuertes fügen Sie neuer Arbeitsblätter zu Arbeitsmappen hinzu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Vorgehensweise: Programmgesteuertes Ändern der Formatierung in Arbeitsblattzeilen, die ausgewählte Zellen enthalten](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
