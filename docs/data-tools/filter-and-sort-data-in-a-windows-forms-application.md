---
title: Filtern und Sortieren von Daten in einer Windows Forms-Anwendung
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 17416a3b64d6cbb5f01192440a9df735f0b9fb94
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566728"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Filtern und Sortieren von Daten in einer Windows Forms-Anwendung

Daten können gefiltert werden, indem die <xref:System.Windows.Forms.BindingSource.Filter%2A>-Eigenschaft auf einen Zeichenfolgenausdruck festlegt wird, der die gewünschten Datensätze zurückgibt.

Sortieren von Daten durch Festlegen der <xref:System.Windows.Forms.BindingSource.Sort%2A> Eigenschaft, um den Namen der Spalte auf dem Sie sortieren möchten, fügen Sie `DESC` in absteigender Reihenfolge zu sortieren, oder fügen Sie `ASC` in aufsteigender Reihenfolge sortiert.

> [!NOTE]
> Wenn Ihre Anwendung nicht verwendet <xref:System.Windows.Forms.BindingSource> -Komponenten, die Sie filtern und Sortieren von Daten mithilfe von <xref:System.Data.DataView> Objekte. Weitere Informationen finden Sie unter ["DataViews"](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Zum Filtern von Daten mithilfe einer BindingSource-Komponente

- Legen Sie die <xref:System.Windows.Forms.BindingSource.Filter%2A>-Eigenschaft auf den zurückzugebenden Ausdruck fest. Im folgenden Code werden beispielsweise Kunden mit einem `CompanyName` zurückgegeben, der mit "B" beginnt:

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>So sortieren Sie Daten mithilfe einer BindingSource-Komponente

- Legen Sie die <xref:System.Windows.Forms.BindingSource.Sort%2A>-Eigenschaft auf die Spalte fest, nach der sortiert werden soll. Im folgenden Code werden beispielsweise Kunden in der Spalte `CompanyName` in absteigender Reihenfolge sortiert:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>Siehe auch

- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)