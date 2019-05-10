---
title: Testtools
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7bcb75da8a21090450c18080240f76ae17c10281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820995"
---
# <a name="testing-tools-in-visual-studio"></a>Testtools in Visual Studio

Die Visual Studio-Testtools können Sie und Ihr Team dabei unterstützen, hochwertigen Code zu entwickeln und diesen Standard einzuhalten.

- Das Fenster **Test-Explorer** vereinfacht die Integration von [Komponententests](../test/unit-test-your-code.md) in die Entwicklungspraxis. Sie können entweder das Microsoft-Komponententest-Framework oder ein Drittanbieter- oder Open-Source-Framework verwenden.

- [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) generiert automatisch Komponententests und Testdaten für verwalteten Code.

- Die [Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) ermittelt, wie groß der Anteil des Projektcodes ist, der in codierten Tests wie Komponententests tatsächlich getestet wird.

- Mit [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) isolieren Sie den zu testenden Code, indem Sie andere Teile der Anwendung durch Stubs oder Shims ersetzen.

- [Live Unit Testing](../test/live-unit-testing.md) führt automatisch Komponententests im Hintergrund aus und stellt die Code Coverage und die Testergebnisse im Code-Editor von Visual Studio grafisch dar.

- Die Anwendung kann mit [Tests der programmierten UI](../test/use-ui-automation-to-test-your-code.md) über die Benutzeroberfläche getestet werden.

- [Auslastungstests](../test/quickstart-create-a-load-test-project.md) simulieren die Auslastung einer Serveranwendung durch Ausführen von Komponententests und Webleistungstests.

> [!NOTE]
> Komponententests sind in allen Editionen von Visual Studio verfügbar. Andere Testtools wie Live Unit Testing, IntelliTest und Tests der programmierten UI sind nur in Visual Studio Enterprise verfügbar. Weitere Informationen zu den Editionen finden Sie unter [Visual Studio 2017-IDEs im Vergleich](https://visualstudio.microsoft.com/vs/compare/).

## <a name="related-scenarios"></a>Ähnliche Szenarios

* [Exploratory & Manual Testing (Azure Test Plans) (Explorative und manuelle Tests (Azure Test Plans))](/azure/devops/test/index?view=vsts)
* [Load testing (Azure Test Plans) (Auslastungstest (Azure Test Plans))](/azure/devops/test/load-test/index?view=vsts)
* [Continuous testing (Azure Test Plans) (Fortlaufende Tests (Azure Test Plans))](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Codeanalysetools](../code-quality/code-analysis-for-managed-code-overview.md)
