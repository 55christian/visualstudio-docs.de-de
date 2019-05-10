---
title: Automatisieren von Excel mithilfe von erweiterten Objekten
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8a08b58871652cea6332f4239e9da98b28f28e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939579"
---
# <a name="automate-excel-by-using-extended-objects"></a>Automatisieren von Excel mithilfe von erweiterten Objekten
  Wenn Sie Excel-Projektmappen in Visual Studio entwickeln, können Sie auch *Hostelemente* und *Hoststeuerelemente*in den Projektmappen verwenden. Dies sind Objekte, die bestimmte häufig verwendete Objekte im Excel-Objektmodell (das von der primären Interopassembly für Excel verfügbar gemacht wird) erweitern. Dazu gehören z. B. die Objekte <xref:Microsoft.Office.Interop.Excel.Worksheet> und <xref:Microsoft.Office.Interop.Excel.Range> . Die erweiterten Objekte verhalten sich wie die Excel-Objekte, auf denen sie basieren, fügen den Objekten jedoch zusätzliche Ereignis- und Datenbindungsfunktionen hinzu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Hostelemente und Hoststeuerelemente sind sowohl in VSTO-Add-Ins als auch in Anpassungen auf Dokumentebene verfügbar, obwohl der Kontext, in dem diese verwendet werden können, für jeden Projektmappentyp anders ist. Weitere Informationen finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Excel-Hostelemente
 Excel-Projekte ermöglichen Ihnen den Zugriff auf mehrere Hostelemente:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Dieses Hostelement enthält, und stellt ein Arbeitsblatt in Ihrem Projekt dar. Es dient auch als Container für verwaltete Steuerelemente, einschließlich Hoststeuerelementen und Windows Forms-Steuerelementen, und es enthält Informationen über die Steuerelemente auf seiner Oberfläche. Weitere Informationen finden Sie unter [Arbeitsblatt-Hostelement](../vsto/worksheet-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Dieses Hostelement stellt die Arbeitsmappe im Projekt dar und dient als Container für Komponenten, die von allen Arbeitsblättern in der Arbeitsmappe gemeinsam verwendet werden. Weitere Informationen finden Sie unter [Arbeitsmappenhostelement](../vsto/workbook-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Dieses Hostelement entspricht einem Excel-Arbeitsblatt, das nur ein Diagramm enthält und Ereignisse verfügbar macht.

     Wenn Sie ein Diagrammblatt zur Entwurfszeit als neues Blatt in Ihrem Microsoft Office Excel-Anpassungsprojekt auf Dokumentebene hinzufügen, erstellt Visual Studio automatisch ein <xref:Microsoft.Office.Tools.Excel.ChartSheet> -Hostelement.

     Obwohl ein <xref:Microsoft.Office.Tools.Excel.ChartSheet> -Hostelement ein Arbeitsblatt in Excel ist, können Sie dem Diagrammblatt keine Steuerelemente hinzufügen. Wenn Sie andere Steuerelemente in einem Arbeitsblatt mit Diagramm verwenden möchten, verwenden Sie kein Diagrammblatt. Platzieren Sie stattdessen ein Diagramm mithilfe des <xref:Microsoft.Office.Tools.Excel.Chart> -Hoststeuerelements als eingebettetes Objekt in einem Arbeitsblatt. Weitere Informationen finden Sie unter [Diagramm-Steuerelement](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>Excel-Hoststeuerelemente
 Es gibt mehrere Hoststeuerelemente für Excel, mit denen Sie Arbeitsmappen und Arbeitsblätter erstellen, organisieren und automatisieren können. Diese Hoststeuerelemente stellen Ereignisse und Datenbindungsfunktionen bereit, über die ihre Äquivalente im systemeigenen Excel-Objektmodell nicht verfügen.

 Weitere Informationen zu den Hoststeuerelementen, die Sie in Excel-Projekten verwenden können, finden Sie unter den folgenden Themen:

- [Chart-Steuerelement](../vsto/chart-control.md)

- [ListObject-Steuerelement](../vsto/listobject-control.md)

- [NamedRange-Steuerelement](../vsto/namedrange-control.md)

- [XmlMappedRange-Steuerelement](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Füllen Sie ListObject-Steuerelementen mit Daten.](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Vorgehensweise: Hinzufügen von Diagrammsteuerelementen zu Arbeitsblättern](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Vorgehensweise: Hinzufügen von XMLMappedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Vorgehensweise: Ändern der Größe von NamedRange-Steuerelementen](../vsto/how-to-resize-namedrange-controls.md)
- [Vorgehensweise: Größe von ListObject-Steuerelementen](../vsto/how-to-resize-listobject-controls.md)
- [Vorgehensweise: Überprüfen Sie Daten aus, wenn einem ListObject-Steuerelement eine neue Zeile hinzugefügt wird](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Vorgehensweise: Zuordnung von ListObject-Spalten zu Daten](../vsto/how-to-map-listobject-columns-to-data.md)
- [Exemplarische Vorgehensweise: Programmieren in Abhängigkeit von Ereignissen eines NamedRange-Steuerelements](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
