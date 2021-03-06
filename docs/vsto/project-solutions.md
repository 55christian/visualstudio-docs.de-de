---
title: Projektmappen
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 84dfe7cf86df2139b06a320d1c6441665a08a1b1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985635"
---
# <a name="project-solutions"></a>Projektmappen
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office Project verwenden können. Mit VSTO-Add-Ins können Sie Project automatisieren, Project-Features erweitern oder die Project-Benutzeroberfläche anpassen.

 Weitere Informationen zu VSTO-Add-Ins finden Sie unter "Einstieg in die [Programmierung von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO](../vsto/architecture-of-vsto-add-ins.md)-Add-Ins". Wenn Sie noch nicht mit der Programmierung mit Microsoft Office vertraut sind, finden Sie weitere Informationen unter [ &#40;Office-Entwicklung in Visual&#41;Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Automatisieren von Projekten mithilfe des Project-Objektmodells
 Das Project-Objektmodell macht viele Typen verfügbar, die Sie zum Automatisieren von Project verwenden können. Mit diesen Typen können Sie Code zum Ausführen gebräuchlicher Aufgaben schreiben, beispielsweise für das programmgesteuerte Erstellen und Ändern von Aufgaben in einem Projekt.

 Wenn Sie von einem VSTO-Add-in aus auf das Project-Objektmodell zugreifen möchten, verwenden Sie das `Application`-Feld der `ThisAddIn`-Klasse in Ihrem Projekt. Das `Application` Feld gibt ein `Microsoft.Office.Interop.MsProject.Application` Objekt zurück, das die aktuelle Instanz des Projekts darstellt. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 Bei einem Aufruf des Project-Objektmodells verwenden Sie Typen, die in der primären Interopassembly für Project bereitgestellt werden. Die primäre Interopassembly dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in Project. Alle Typen in der primären Interopassembly für Project werden im `Microsoft.Office.Interop.MSProject`-Namespace definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht &#40;über die Entwicklung&#41; von Office](../vsto/office-solutions-development-overview-vsto.md) -Projektmappen VSTO und [Office Primary Interopassemblys](../vsto/office-primary-interop-assemblies.md)

## <a name="use-the-project-object-model-documentation"></a>Verwenden der Dokumentation zum Project-Objektmodell
 Ausführliche Informationen zum Project-Objektmodell finden Sie in der VBA-Objektmodellreferenz für Project. Die VBA-Objektmodellreferenz dokumentiert das Project-Objektmodell, das für VBA (Visual Basic for Applications) verfügbar gemacht wird. Weitere Informationen finden Sie unter [Project Object Model Reference](/office/vba/api/project.object).

 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der primären Interopassembly (PIA) für Project. Das Calendar-Objekt in der VBA-Objektmodell Referenz entspricht z. b. dem `Microsoft.Office.Interop.MSProject.Calendar`-Typ in der Projekt-PIA. Obwohl die VBA-Objektmodell Referenzcode Beispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder C# Visual übersetzen, wenn Sie ihn in einem Projekt-VSTO-Add-in-Projekt verwenden möchten, das Sie von erstellen. mithilfe von Visual Studio.

> [!NOTE]
> Derzeit ist keine Referenzdokumentation für die primäre Interopassembly für Project verfügbar.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Infrastruktur Typen in der primären Interopassembly des Projekts
 Wenn Sie Code schreiben, in dem die Project-PIA verwendet wird, werden Ihnen möglicherweise viele Typen begegnen, die nicht in der VBA-Referenz beschrieben sind. Diese zusätzlichen Typen helfen dabei, Objekte im COM-basierten Objektmodell von Project in verwalteten Code zu übersetzen. Sie sind nicht für die direkte Verwendung im Code vorgesehen.

 Weitere Informationen finden Sie unter [Übersicht über Klassen und Schnittstellen in den primären Interop-](/previous-versions/office/office-12/ms247299(v=office.12))Assemblys von Office.

## <a name="customize-the-user-interface-of-project"></a>Anpassen der Benutzeroberfläche von Project
 Sie können die Benutzeroberfläche von Project folgendermaßen anpassen:

|Aufgabe|Weitere Informationen|
|----------|--------------------------|
|Hinzufügen benutzerdefinierter Registerkarten zum Menüband in Project|[Übersicht über Menüband](../vsto/ribbon-overview.md)|

 Weitere Informationen zum Anpassen der Benutzeroberfläche von Project und anderen Microsoft Office Anwendungen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
- [Übersicht über &#40;die Entwicklung von Office-Lösungen VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Project 2010 und Project Server 2010 in der Office-Entwicklung](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
