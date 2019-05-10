---
title: Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, host controls
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host items [Office development in Visual Studio], programmatic limitations
- Excel [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], passing to methods and properties
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], programmatic limitations
- documents [Office development in Visual Studio], host items
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d885ba9d32126e0d77828047adbde84d557fd821
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447076"
---
# <a name="programmatic-limitations-of-host-items-and-host-controls"></a>Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen
  Jedes Hostelement und Hoststeuerelement ist so konzipiert, dass es sich wie ein entsprechendes systemeigenes Microsoft Office Word- oder Microsoft Office Excel-Objekt mit zusätzlichen Funktionen verhält. Es gibt jedoch einige grundlegende Unterschiede zwischen dem Verhalten von Hostelementen und Hoststeuerelementen und systemeigenen Office-Objekten zur Laufzeit.

 Allgemeine Informationen zu Hostelementen und Hoststeuerelementen, finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md).

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="programmatically-create-host-items"></a>Programmgesteuertes Erstellen von Hostelementen
 Wenn Sie ein Dokument, eine Arbeitsmappe oder ein Arbeitsblatt mithilfe des Word- oder Excel-Objektmodells zur Laufzeit programmgesteuert erstellen, ist das Element kein Hostelement. Stattdessen ist das neue Objekt ein systemeigenes Office-Objekt. Wenn Sie z. B. die <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> -Methode zum Erstellen eines neuen Word-Dokuments zur Laufzeit verwenden, handelt es sich dabei um ein systemeigenes <xref:Microsoft.Office.Interop.Word.Document> -Objekt, anstatt um ein <xref:Microsoft.Office.Tools.Word.Document> -Hostelement. Beim Erstellen eines neuen Arbeitsblatts zur Laufzeit mithilfe der <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> -Methode erhalten Sie entsprechend ein systemeigenes <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt, anstatt ein <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelement.

 Sie können nicht in Projekten auf Dokumentebene Hostelemente zur Laufzeit erstellen. Hostelemente können in Projekten auf Dokumentebene nur zur Entwurfszeit erstellt werden. Weitere Informationen finden Sie unter [Dokumenthostelement](../vsto/document-host-item.md), [Arbeitsmappenhostelement](../vsto/workbook-host-item.md), und [Arbeitsblatt-Hostelement](../vsto/worksheet-host-item.md).

 Sie können in VSTO-Add-in-Projekte erstellen <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, oder <xref:Microsoft.Office.Tools.Excel.Worksheet> Hostelemente zur Laufzeit. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="programmatically-create-host-controls"></a>Programmgesteuertes Erstellen von Hoststeuerelementen
 Sie können programmgesteuert hinzufügen von Hoststeuerelementen an eine <xref:Microsoft.Office.Tools.Word.Document> oder <xref:Microsoft.Office.Tools.Excel.Worksheet> Hostelements zur Laufzeit. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Sie können Hoststeuerelemente nicht zu einem systemeigenen <xref:Microsoft.Office.Interop.Word.Document> oder <xref:Microsoft.Office.Interop.Excel.Worksheet>hinzufügen.

> [!NOTE]
> Die folgenden Hoststeuerelemente können nicht programmgesteuert zu Arbeitsblättern oder Dokumenten hinzugefügt werden: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>und <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="understand-type-differences-between-host-items-host-controls-and-native-office-objects"></a>Verstehen Sie Typunterschieden zwischen Hostelementen, Hoststeuerelementen und systemeigenen Office-Objekte
 Für jedes Hostelement und Hoststeuerelement gibt es ein zugrunde liegendes systemeigenes Microsoft Office Word- oder Microsoft Office Excel-Objekt. Sie können das zugrunde liegende Objekt zugreifen, mithilfe der InnerObject-Eigenschaft des Hostelements oder Hoststeuerelements. Allerdings besteht keine Möglichkeit, ein systemeigenes Office-Objekt in ein entsprechendes Hostelement oder Hoststeuerelement umzuwandeln. Wenn Sie versuchen, ein systemeigenes Office-Objekt in ein Hostelement oder Hoststeuerelement umzuwandeln, wird ein <xref:System.InvalidCastException> ausgelöst.

 Es gibt verschiedene Szenarien, in denen sich die Unterschiede zwischen den Typen von Hostelementen und Hoststeuerelementen sowie den zugrunde liegenden systemeigenen Office-Objekte auf den Code auswirken können.

### <a name="pass-host-controls-to-methods-and-properties"></a>Übergeben von Hoststeuerelementen an Methoden und Eigenschaften
 In Word können Sie ein Hoststeuerelement nicht an eine Methode oder Eigenschaft übergeben, die ein systemeigenes Word-Objekt als Parameter erfordert. Sie müssen die InnerObject-Eigenschaft des Hoststeuerelements verwenden, um die zugrunde liegende systemeigene Word-Objekt zurückzugeben. Sie können z. B. ein <xref:Microsoft.Office.Interop.Word.Bookmark> -Objekt an eine Methode übergeben, indem Sie die <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Word.Bookmark> -Hoststeuerelements an die Methode übergeben.

 In Excel müssen Sie die InnerObject-Eigenschaft des Hoststeuerelements verwenden, um das Hoststeuerelement an eine Methode oder Eigenschaft übergeben wird, wenn die Methode oder Eigenschaft das zugrunde liegende Excel-Objekt erwartet.

 Im folgenden Beispiel wird ein <xref:Microsoft.Office.Tools.Excel.NamedRange> -Steuerelement erstellt und an die <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> -Methode übergeben. Der Code verwendet die <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> -Eigenschaft des benannten Bereichs, um das zugrunde liegende Office- <xref:Microsoft.Office.Interop.Excel.Range> zurückzugeben, das von der <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> -Methode benötigt wird.

 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#28)]

### <a name="return-types-of-native-office-methods-and-properties"></a>Rückgabetypen von systemeigenen Office-Methoden und Eigenschaften
 Die meisten Methoden und Eigenschaften von Hostelementen geben das zugrunde liegende systemeigene Office-Objekt zurück, auf dem das Hostelement basiert. Die <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> -Eigenschaft des <xref:Microsoft.Office.Tools.Excel.NamedRange> -Hoststeuerelements in Excel gibt z. B. ein <xref:Microsoft.Office.Interop.Excel.Worksheet> -Objekt anstelle eines <xref:Microsoft.Office.Tools.Excel.Worksheet> -Hostelements zurück. Die <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> -Eigenschaft eines <xref:Microsoft.Office.Tools.Word.RichTextContentControl> -Hoststeuerelements in Word gibt entsprechend ein <xref:Microsoft.Office.Interop.Word.Document> -Objekt anstelle eines <xref:Microsoft.Office.Tools.Word.Document> -Hostelements zurück.

### <a name="access-collections-of-host-controls"></a>Access-Auflistungen von Hoststeuerelementen
 Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bietet für die einzelnen Hoststeuerelementtypen keine individuellen Auflistungen. Verwenden Sie stattdessen die "Controls"-Eigenschaft eines Hostelements zum Durchlaufen aller verwalteten Steuerelemente (sowohl Hoststeuerelemente und Windows Forms-Steuerelemente) im Dokument oder Arbeitsblatt, und suchen Sie nach Elementen, die den Typ des Hoststeuerelements entsprechen, die, denen Sie interessieren. Im folgenden Codebeispiel wird jedes Steuerelement in einem Word-Dokument untersucht und dann bestimmt, ob das Steuerelement ein <xref:Microsoft.Office.Tools.Word.Bookmark>ist.

 [!code-csharp[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#10)]

 Weitere Informationen zu den Steuerelementen-Eigenschaft von Hostelementen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Die Objektmodelle von Word und Excel enthalten Eigenschaften, die Auflistungen von systemeigenen Steuerelementen für Dokumente und Arbeitsblätter bereitstellen. Sie können mithilfe dieser Eigenschaften nicht auf verwaltete Steuerelemente zugreifen. Es ist z. B. nicht möglich, jedes <xref:Microsoft.Office.Tools.Word.Bookmark> -Hoststeuerelement in einem Dokument mithilfe der <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> -Eigenschaft einer <xref:Microsoft.Office.Interop.Word.Document> - oder <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> -Eigenschaft eines <xref:Microsoft.Office.Tools.Word.Document>aufzuzählen. Diese Eigenschaften beziehen nur die <xref:Microsoft.Office.Interop.Word.Bookmark> -Steuerelemente im Dokument ein. Sie enthalten nicht die <xref:Microsoft.Office.Tools.Word.Bookmark> -Hoststeuerelemente im Dokument.

## <a name="see-also"></a>Siehe auch
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)
- [Arbeitsblatthostelement](../vsto/worksheet-host-item.md)
- [Arbeitsmappenhostelement](../vsto/workbook-host-item.md)
- [Dokumenthostelement](../vsto/document-host-item.md)
