---
title: 'Vorgehensweise: Programm gesteuertes Erstellen neuer Arbeitsmappen'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 030bc801399ddcc73f145c0b45ca065c9a9ecc7a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251877"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Vorgehensweise: Programm gesteuertes Erstellen neuer Arbeitsmappen
  Wenn Sie eine Arbeitsmappe programmgesteuert erstellen, ist diese ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Workbook>-Objekt und kein <xref:Microsoft.Office.Tools.Excel.Workbook>-Hostelement.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Sie können ein <xref:Microsoft.Office.Tools.Excel.Workbook>-Hostelement für ein <xref:Microsoft.Office.Interop.Excel.Workbook>-Objekt im VSTO-Add-In-Projekt generieren. Weitere Informationen finden [Sie unter Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-workbook"></a>So erstellen Sie eine neue Arbeitsmappe

1. Verwenden Sie die <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> -Methode der <xref:Microsoft.Office.Interop.Excel.Workbooks> -Auflistung.

     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]

    > [!NOTE]
    > Sie können eine Arbeitsmappe auf der Grundlage einer anderen Vorlage als der Standardvorlage erstellen: Übergeben Sie die Vorlage, die Sie verwenden möchten, als Parameter an die Methode <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.

## <a name="see-also"></a>Siehe auch
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-Ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Arbeiten mit Arbeitsmappen](../vsto/working-with-workbooks.md)
- [Vorgehensweise: Programm gesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md)
- [Vorgehensweise: Programm gesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md)
- [Vorgehensweise: Programm gesteuertes schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md)
- [Programmgesteuerte Einschränkungen von Host Elementen und Host Steuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)
- [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md)
