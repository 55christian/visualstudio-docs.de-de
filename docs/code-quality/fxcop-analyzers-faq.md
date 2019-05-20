---
title: FxCop-Codeanalyse und FxCop-Analysetools
ms.date: 09/06/2018
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ab7816e7e1472101f0e84c05a4975f19e3902e27
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613553"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Häufig gestellte Fragen zu FxCop und FxCop-Analysetools

Die Unterschiede zwischen Legacy-FxCop und FxCop-Analysetools können verwirrend sein. Deshalb werden in diesem Artikel einige Fragen behandelt, die Sie möglicherweise haben.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>Was ist der Unterschied zwischen Legacy-FxCop und FxCop-Analysetools?

Legacy-FxCop führt die Analyse einer kompilierten Assembly nach dem Erstellen aus. Eine separate ausführbare Datei namens **FxCopCmd.exe** wird ausgeführt. Die Datei „FxCopCmd.exe“ lädt die kompilierte Assembly, führt die Codeanalyse aus und meldet dann die Ergebnisse (bzw. *Diagnose*).

FxCop-Analysetools basieren auf der .NET Compiler Platform („Roslyn“). Sie [installieren sie als NuGet-Pakete](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package), auf die von dem Projekt oder der Projektmappe verwiesen wird. FxCop-Analysetools führen während der Ausführung des Compilers Analysen aus, die auf dem Quellcode basieren. FxCop-Analysetools werden im Compilerprozess gehostet, entweder **csc.exe** oder **vbc.exe**, und führen die Analyse bei der Erstellung des Projekts aus. Die Analyseergebnisse werden zusammen mit den Ergebnissen der Kompilierung gemeldet.

> [!NOTE]
> Sie können [FxCop-Analysetools auch als Visual Studio-Erweiterung installieren](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). In diesem Fall werden die Analysetools ausgeführt, während Sie in den Code-Editor schreiben. Allerdings werden Sie nicht zum Zeitpunkt der Erstellung ausgeführt. Wenn Sie FxCop-Analysetools als Teil der CI (Continuous Integration) ausführen möchten, installieren Sie sie stattdessen als NuGet-Pakete.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>Werden FxCop-Analysetools mit dem Befehl „Codeanalyse ausführen“ ausgeführt?

Nein. Wenn Sie auf **Analyse** > **Codeanalyse ausführen** klicken, wird die statische Codeanalyse oder Legacy-FxCop ausgeführt. **Codeanalyse ausführen** wirkt sich nicht auf Analysetools aus, die auf Roslyn basieren, einschließlich der auf Roslyn basierenden FxCop-Analysetools.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>Werden Analysetools von der MSBuild-Projekteigenschaft „RunCodeAnalysis“ ausgeführt?

Nein. Die Eigenschaft **RunCodeAnalysis** in einer Projektdatei (z.B. *.csproj*) wird nur zum Ausführen von Legacy-FxCop verwendet. Sie führt eine MSBuild-Postbuildaufgabe aus, die **FxCopCmd.exe** aufruft. Dies gleicht der Auswahl der Option **Analyse** > **Codeanalyse ausführen** in Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>Wie kann ich FxCop-Analysetools ausführen?

Zum Ausführen von FxCop-Analysetools müssen Sie zunächst die entsprechenden [NuGet-Pakete installieren](install-fxcop-analyzers.md). Dann erstellen Sie Ihr Projekt oder Ihre Projektmappe mit Visual Studio oder MSBuild. Die Warnungen und Fehlermeldungen von FxCop-Analysetools werden in der **Fehlerliste** oder im Befehlsfenster angezeigt.

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>Nach der Installation des NuGet-Pakets für das FxCop-Analysetool erhalte ich die Warnung „CA0507“.

Wenn Sie FxCop-Analysetools installiert haben, aber weiterhin eine Warnung erhalten CA0507 **"Run Code Analysis" ist zugunsten von FxCop-Analysetools, die während des Build ausgeführt werden, veraltet**, müssen Sie möglicherweise die msbuild-Eigenschaft **RunCodeAnalysis** in Ihrer Projektdatei auf **false** setzen. Andernfalls wird die statische Codeanalyse nach jedem Build ausgeführt.

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="see-also"></a>Siehe auch

- [Overview of .NET Compiler Platform analyzers (Übersicht über .NET Compiler Platform-Analysetools)](roslyn-analyzers-overview.md)
- [Get started with analyzers (Erste Schritte mit Analysetools)](fxcop-analyzers.yml)
- [Install FxCop analyzers (Installieren von FxCop-Analysetools)](install-fxcop-analyzers.md)
