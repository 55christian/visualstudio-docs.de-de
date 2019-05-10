---
title: 'Vorgehensweise: Definieren einer Methodeninstanz | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method instance
- BDC [SharePoint development in Visual Studio], method
- Business Data Connectivity service [SharePoint development in Visual Studio], method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 318744ec1a1a9214ce0385fc56fb1c0cf340339b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814110"
---
# <a name="how-to-define-a-method-instance"></a>Vorgehensweise: Definieren einer Methodeninstanz
  Sie müssen mindestens eine Methodeninstanz für jede Methode in Ihrem Modell definieren.

 Methodeninstanz hinzufügen, mit der **BDC-Methodendetails** Fenster. Wenn Sie die Methodeninstanz hinzufügen, fügt Visual Studio eine `<MethodInstance>` Element auf das XML-Datei des Modells in Ihrem Projekt. Weitere Informationen zu den Attributen von einem `<MethodInstance>` Element finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

### <a name="to-define-a-method-instance"></a>Zum Definieren einer Methodeninstanz

1. In der **BDC-Methodendetails** , erweitern Sie den Knoten einer Methode, und erweitern Sie dann die **Instanzen** Knoten.

2. In der **Methodeninstanz hinzufügen** wählen **Finder-Instanz erstellen**.

     Eine neue Methodeninstanz angezeigt wird, unter dem **Instanzen** Knoten.

3. Wählen Sie auf der Menüleiste **Ansicht** > **Fenster "Eigenschaften"**.

4. In der **Eigenschaften** legen die Eigenschaften der Instanz. Weitere Informationen zu den einzelnen Eigenschaften finden Sie unter [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).

## <a name="see-also"></a>Siehe auch
- [Übersicht über Entwurfstools für BDC-Modell](../sharepoint/bdc-model-design-tools-overview.md)
- [Vorgehensweise: Hinzufügen einer Entitätstyps zu einem Modell](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Vorgehensweise: Fügen Sie einen Parameter einer Methode](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Vorgehensweise: Definieren des Typdeskriptors für einen parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Entwerfen eines Business Data Connectivity-Modells](../sharepoint/designing-a-business-data-connectivity-model.md)
