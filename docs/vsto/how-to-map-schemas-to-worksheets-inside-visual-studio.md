---
title: 'Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80a19924aaf4fa0afe8e809006ada7fada0288f3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428119"
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Vorgehensweise: Zuordnen von Schemas zu Arbeitsblättern in Visual Studio
  Sie können ein XML-Schema zu einem Arbeitsblatt zuordnen, während das Arbeitsblatt in Visual Studio geöffnet ist. Sie verwenden den gleichen Microsoft Office Excel-Tools, die Sie verwenden, wenn die Arbeitsmappe außerhalb von Visual Studio geöffnet ist. Das Office-Projekt erstellt die gleichen Objekte, ob Sie das Schema der Tabelle vor dem zuordnen oder nach der Erstellung der Excel-Projektmappe.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Sie können keine mehrteiligen XML-Schemas in Excel-Projektmappen verwenden.

## <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Ordnen Sie eine XML-Schema in ein Excel-Arbeitsblatt in Visual Studio

1. Öffnen Sie die Excel-Arbeitsmappe oder Vorlage-Projekt in Visual Studio.

2. Klicken Sie in das Arbeitsblatt, das den Fokus auf den Designer.

3. Klicken Sie im Menüband auf die Registerkarte **Entwickler** .

    > [!NOTE]
    > Wenn die Registerkarte **Entwickler** nicht sichtbar ist, müssen Sie diese zuerst anzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. In der **XML** auf **Quelle**.

     Die **XML-Quelle** Fenster wird geöffnet.

5. In der **XML-Quelle** Fenster, klicken Sie auf **XML-Zuordnungen**.

     Die **XML-Zuordnungen** Dialogfeld wird geöffnet.

6. In der **XML-Zuordnungen** Dialogfeld klicken Sie auf **hinzufügen**.

7. Navigieren Sie zu der Schemadatei, wählen Sie ihn, und klicken Sie dann auf **öffnen**.

8. Klicken Sie auf **OK**.

     Das Schema wird dargestellt, der **XML-Quelle** Fenster. In Ihrem Projekt ein typisiertes <xref:System.Data.DataSet> wird basierend auf dem Schema generiert und ein <xref:System.Windows.Forms.BindingSource> erstellt wird.

9. Ziehen Sie Elemente aus der **XML-Quelle** Fenster an die Orte im Arbeitsblatt, in denen die entsprechenden Steuerelemente erstellt werden sollen.

     Wenn Sie ein nicht wiederholendes Schemaelement ziehen, generiert das Office-Projekt ein <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> -Steuerelement, das automatisch an die gebunden wird die <xref:System.Windows.Forms.BindingSource>.

     Wenn Sie ein sich wiederholendes Schemaelement ziehen, generiert das Office-Projekt eine <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement, das nicht automatisch an eine Datenquelle gebunden ist. Weitere Informationen finden Sie unter [XML-Schemas und-Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Zuordnen von Schemas zu Word-Dokumenten in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [XML-Schemas und Daten in Anpassungen auf Dokumentebene](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
