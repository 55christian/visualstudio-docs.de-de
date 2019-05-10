---
title: 'Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fccd328c521789c8ebb4b32c49b2a03a46027eb5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427765"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern
  Sie können hinzufügen <xref:Microsoft.Office.Tools.Excel.Chart> Steuerelementen zu einem Microsoft Office Excel-Arbeitsblatt zur Entwurfszeit und zur Laufzeit in Anpassungen auf Dokumentebene. Sie können auch hinzufügen <xref:Microsoft.Office.Tools.Excel.Chart> Steuerelementen zur Laufzeit in VSTO-Add-ins.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 In diesem Thema werden die folgenden Aufgaben beschrieben:

- [Hinzufügen von Chart-Steuerelementen zur Entwurfszeit](#designtime)

- [Hinzufügen von Chart-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene](#runtimedoclevel)

- [Hinzufügen von Chart-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt](#runtimeaddin)

  Weitere Informationen zu <xref:Microsoft.Office.Tools.Excel.Chart> Steuerelemente finden Sie [Diagramm-Steuerelement](../vsto/chart-control.md).

## <a name="designtime"></a> Hinzufügen von Chart-Steuerelementen zur Entwurfszeit
 Sie können das <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement Ihrem Arbeitsblatt auf die gleiche Weise wie ein Diagramm innerhalb der Anwendung hinzufügen.

> [!NOTE]
> Die <xref:Microsoft.Office.Tools.Excel.Chart> Steuerelement ist nicht verfügbar ist, aus der **Toolbox** oder **Datenquellen** Fenster.

### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>So fügen Sie einem Arbeitsblatt in Excel ein Chart-Hoststeuerelement hinzu

1. Auf der **einfügen** Registerkarte die **Diagramme** auf **Spalte**, klicken Sie auf eine Diagrammkategorie, und klicken Sie dann auf den Typ des gewünschten Diagramms.

2. In der **Diagramm einfügen** Dialogfeld klicken Sie auf **OK**.

3. Auf der **Entwurf** Registerkarte die **Daten** auf **Daten auswählen**.

4. In der **Auswählen einer Datenquelle** (Dialogfeld), klicken Sie in der **Diagramm** **Datenbereich** und deaktivieren Sie die Standardauswahl.

5. In der **Daten für Diagramm** Stylesheet, wählen Sie den Bereich von Zellen, die die Daten für das Diagramm enthält (Zellen **A5** über **D8**).

6. In der **Auswählen einer Datenquelle** Dialogfeld klicken Sie auf **OK**.

## <a name="runtimedoclevel"></a> Hinzufügen von Chart-Steuerelementen zur Laufzeit in einem Projekt auf Dokumentebene
 Sie können hinzufügen, die <xref:Microsoft.Office.Tools.Excel.Chart> Steuerelement dynamisch zur Laufzeit. Dynamisch erstellte Diagramme werden nicht im Dokument wie Hoststeuerelemente dauerhaft gespeichert, wenn das Dokument geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein Chart-Steuerelement programmgesteuert hinzu

1. Fügen Sie im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>-Ereignishandler von `Sheet1` den folgenden Code hinzu, um das <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement hinzuzufügen:

     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]

## <a name="runtimeaddin"></a> Hinzufügen von Chart-Steuerelementen zur Laufzeit in einem VSTO-Add-in-Projekt
 Sie können ein <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement programmgesteuert jedem geöffneten Arbeitsblatt in einem VSTO-Add-In-Projekt hinzufügen. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

 Dynamisch erstellte Chart-Steuerelemente werden nicht im Arbeitsblatt wie Hoststeuerelemente dauerhaft gespeichert, wenn das Arbeitsblatt geschlossen wird. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>So fügen Sie einem Arbeitsblatt ein Chart-Steuerelement programmgesteuert hinzu

1. Der folgende Code generiert ein Arbeitsblatt-Hostelement, das auf dem geöffneten Arbeitsblatt basiert, und fügt dann ein <xref:Microsoft.Office.Tools.Excel.Chart>-Steuerelement hinzu.

     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]

## <a name="compile-the-code"></a>Kompilieren des Codes
 Für dieses Beispiel gelten die folgenden Anforderungen:

- Die Daten für das Diagramm sind im Bereich von A5 bis D8 im Arbeitsblatt gespeichert.

## <a name="see-also"></a>Siehe auch
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Chart-Steuerelement](../vsto/chart-control.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
