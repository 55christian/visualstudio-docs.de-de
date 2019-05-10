---
title: 'Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24bbd859b4867225e5ec5df95d298dd04146df46
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421015"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements
  Sie können ein Hoststeuerelement an eine Datenquelle binden und die Datenquelle mit den Änderungen aktualisieren, die im Steuerelement an den Daten vorgenommen werden. In diesem Prozess gibt es zwei Hauptschritte:

1. Aktualisieren der In-Memory-Datenquelle mit den geänderten Daten im Steuerelement. In der Regel ist die In-Memory-Datenquelle ein <xref:System.Data.DataSet>, eine <xref:System.Data.DataTable>oder ein anderes Datenobjekt.

2. Aktualisieren der Datenbank mit den geänderten Daten in der In-Memory-Datenquelle. Dies trifft nur zu, wenn die Datenquelle mit einer Back-End-Datenbank verbunden ist, beispielsweise einer SQL Server- oder Microsoft Office Access-Datenbank.

   Weitere Informationen über Hoststeuerelemente und Datenbindung finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md) und [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Aktualisieren der in-Memory-Datenquelle
 Standardmäßig speichern Hoststeuerelemente, die eine einfache Datenbindung ermöglichen (z. B. Inhaltssteuerelemente auf einem Word-Dokument oder NamedRange-Steuerelemente auf einem Excel-Arbeitsblatt), keine Datenänderungen in der In-Memory-Datenquelle. Das heißt, wenn ein Endbenutzer einen Wert in einem Hoststeuerelement ändert und anschließend das Steuerelement verlässt, wird der neue Wert im Steuerelement nicht automatisch in der Datenquelle gespeichert.

 Um die Daten in der Datenquelle speichern zu können, Sie Code schreiben, der die Datenquelle als Reaktion auf ein bestimmtes Ereignis zur Laufzeit aktualisiert, oder Sie können konfigurieren, dass das Steuerelement, um die Datenquelle automatisch aktualisiert werden soll, wenn der Wert im Steuerelement ändert.

 <xref:Microsoft.Office.Tools.Excel.ListObject> -Änderungen an der In-Memory-Datenquelle müssen nicht gespeichert werden. Wenn Sie ein <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement an Daten binden, speichert das <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement automatisch Änderungen in der In-Memory-Datenquelle, ohne dass zusätzlicher Code benötigt wird.

### <a name="to-update-the-in-memory-data-source-at-runtime"></a>Um die in-Memory-Datenquelle zur Laufzeit zu aktualisieren.

- Rufen Sie die <xref:System.Windows.Forms.Binding.WriteValue%2A> -Methode des <xref:System.Windows.Forms.Binding> -Objekts auf, über das das Steuerelement an die Datenquelle gebunden ist.

     Im folgenden Beispiel werden Änderungen, die an einem <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement auf einem Excel-Arbeitsblatt vorgenommen wurden, in der Datenquelle gespeichert. Für dieses Beispiel wird davon ausgegangen, dass Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement namens `namedRange1` haben, dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft an ein Feld in einer Datenquelle gebunden ist.

     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]

### <a name="automatically-update-the-in-memory-data-source"></a>Die in-Memory-Datenquelle automatisch aktualisieren
 Sie können ein Steuerelement auch so konfigurieren, dass es die In-Memory-Datenquelle automatisch aktualisiert. In einem Projekt auf Dokumentebene ist dies mithilfe von Code oder mit dem Designer möglich. In einem VSTO-Add-in-Projekt müssen Sie Code verwenden.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>So legen Sie fest, dass ein Steuerelement die In-Memory-Datenquelle automatisch über Code aktualisiert

1. Verwenden Sie den System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged-Modus, der die <xref:System.Windows.Forms.Binding> -Objekt, das das Steuerelement an die Datenquelle gebunden. Es gibt zwei Optionen zum Aktualisieren der Datenquelle:

   - Um die Datenquelle zu aktualisieren, wenn das Steuerelement validiert wird, wird diese Eigenschaft auf System.Windows.Forms.DataSourceUpdateMode.OnValidation fest.

   - Um die Datenquelle aktualisiert, wenn der Wert der datengebundenen Eigenschaft des Steuerelements ändert, wird diese Eigenschaft auf System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged fest.

     > [!NOTE]
     > Die System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged-Option gilt nicht für Word-Hoststeuerelemente, da Word keine Angebot Dokument- oder steuerelementänderungen Benachrichtigungen ist. Diese Option kann jedoch für Windows Forms-Steuerelemente auf Word-Dokumenten verwendet werden.

     Im folgenden Beispiel wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement so konfiguriert, dass die Datenquelle automatisch aktualisiert wird, wenn sich der Wert im Steuerelement ändert. Für dieses Beispiel wird davon ausgegangen, dass Sie ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement namens `namedRange1` haben, dessen <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> -Eigenschaft an ein Feld in einer Datenquelle gebunden ist.

     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>So legen Sie mit dem Designer fest, dass ein Steuerelement die In-Memory-Datenquelle automatisch aktualisiert

1. Öffnen Sie in Visual Studio das Word-Dokument oder die Excel-Arbeitsmappe im Designer.

2. Klicken Sie auf das Steuerelement, von dem die Datenquelle automatisch aktualisiert werden soll.

3. Erweitern Sie im Fenster **Eigenschaften** die **(DataBindings)** -Eigenschaft.

4. Neben der **(Erweitert)** -Eigenschaft, klicken Sie auf die Schaltfläche mit den Auslassungspunkten (![VisualStudioEllipsesButton-bildschirmabbildung](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton-bildschirmabbildung")).

5. Klicken Sie im Dialogfeld **Formatierung und erweiterte Bindung** auf die Dropdownliste **Datenquellen-Aktualisierungsmodus** , und wählen Sie einen der folgenden Werte aus:

    - Um die Datenquelle zu aktualisieren, wenn das Steuerelement validiert wird, wählen Sie **OnValidation**aus.

    - Um die Datenquelle zu aktualisieren, wenn sich der Wert der datengebundenen Eigenschaft des Steuerelements ändert, wählen Sie **OnPropertyChanged**aus.

        > [!NOTE]
        > Die **OnPropertyChanged** -Option gilt nicht für Word-Hoststeuerelemente, da Word keine Benachrichtigungen über Dokument- oder Steuerelementänderungen bereitstellt. Diese Option kann jedoch für Windows Forms-Steuerelemente auf Word-Dokumenten verwendet werden.

6. Schließen sie das Dialogfeld **Formatierung und erweiterte Bindung** .

## <a name="update-the-database"></a>Aktualisieren der Datenbank
 Wenn die In-Memory-Datenquelle mit einer Datenbank verknüpft ist, müssen Sie die Datenbank mit den Änderungen an der Datenquelle aktualisieren. Weitere Informationen zum Aktualisieren einer Datenbank finden Sie unter [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md) und [Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .

### <a name="to-update-the-database"></a>So aktualisieren Sie die Datenbank

1. Rufen Sie die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> -Methode der <xref:System.Windows.Forms.BindingSource> -Instanz für das Steuerelement auf.

     Die <xref:System.Windows.Forms.BindingSource> -Instanz wird automatisch generiert, wenn Sie einem Dokument oder einer Arbeitsmappe zur Entwurfszeit ein datengebundenes Steuerelement hinzufügen. Die <xref:System.Windows.Forms.BindingSource> -Instanz verbindet das Steuerelement mit dem typisierten Dataset im Projekt. Weitere Informationen finden Sie unter [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview).

     Für das folgende Codebeispiel wird vorausgesetzt, dass das Projekt eine <xref:System.Windows.Forms.BindingSource> -Instanz namens `customersBindingSource`enthält.

     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]

2. Rufen Sie die `Update` Methode des generierten TableAdapter in Ihrem Projekt.

     Der TableAdapter wird automatisch generiert, wenn Sie ein vom datengebundenen Steuerelement zu einem Dokument oder die Arbeitsmappe zur Entwurfszeit hinzufügen. Der TableAdapter verbindet das typisierte Dataset in Ihrem Projekt mit der Datenbank. Weitere Informationen finden Sie unter [Übersicht über TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Im folgenden Codebeispiel wird davon ausgegangen, dass Sie eine Verbindung mit der Customers-Tabelle in der Northwind-Datenbank verfügen und Ihr Projekt einen TableAdapter Namens enthält `customersTableAdapter` und ein typisiertes Dataset namens `northwindDataSet`.

     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]

## <a name="see-also"></a>Siehe auch
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
- [Gewusst wie: Aktualisieren von Daten mit einem TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Vorgehensweise: Führen Sie einen Bildlauf durch Datenbankdatensätze in einem Arbeitsblatt](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)
