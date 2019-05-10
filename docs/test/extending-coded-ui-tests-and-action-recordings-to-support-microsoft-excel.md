---
title: Erweitern von Tests der programmierten UI und Aktionsaufzeichnungen
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 07cdc27cb47a6de46585f573d78b5af00631c2a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002392"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Erweitern von Tests der programmierten UI und Aktionsaufzeichnungen

Das Testframework für Tests der programmierten UI und Aktionsaufzeichnungen unterstützen nicht jede mögliche Benutzeroberfläche. Es kann vorkommen, dass die zu testende Benutzeroberfläche nicht unterstützt wird. Es ist z.B. nicht möglich, direkt einen Test der programmierten UI oder eine Aktionsaufzeichnung für ein Microsoft Excel-Arbeitsblatt zu erstellen. Die Erweiterbarkeit des Frameworks für Tests der programmierten UI bietet Ihnen jedoch die Möglichkeit, eine eigene Erweiterung des Frameworks zu erstellen, die die spezifische Benutzeroberfläche unterstützt.

![Laden der UI-Testarchitektur](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Beispielerweiterung für Tests in Microsoft Excel

Dieser [Blogbeitrag](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) enthält einen Link zu einer [Beispielerweiterung](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) für das Framework für Tests der programmierten UI. Sie können ebenfalls die gesamte [Reihe von Blogbeiträgen für die Erweiterbarkeit von Tests der programmierten UI](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/) anzeigen.

> [!NOTE]
> Das Beispiel ist zur Verwendung mit Microsoft Excel 2010 gedacht. Es ist ungewiss, ob es mit anderen Excel-Versionen funktioniert.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
- [Bewährte Methoden für Tests der programmierten UI](../test/best-practices-for-coded-ui-tests.md)
- [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)