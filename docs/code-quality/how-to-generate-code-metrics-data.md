---
title: Generieren von codemetriken aus der IDE oder über die Befehlszeile
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4275e92b21289c5cf1e3243b2bc782a9e0821fde
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823581"
---
# <a name="how-to-generate-code-metrics-data"></a>Vorgehensweise: Generieren von Codemetrikdaten

Sie können Codemetrikdaten werden auf drei Arten generieren:

- Durch die Installation von [FxCop-Analysetools](#fxcop-analyzers-code-metrics-rules) und aktivieren die vier Code Metriken (Verwaltbarkeit)-Regeln, die sie enthält.

- Durch Auswahl der [ **analysieren** > **Berechnen der Codemetrik** ](#calculate-code-metrics-menu-command) Menübefehl in Visual Studio.

- Von der [Befehlszeile](#command-line-code-metrics) für C# und Visual Basic-Projekte.

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop Analysen Metriken Coderegeln

Die [FxCopAnalyzers-NuGet-Paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) enthält mehrere Codemetrik [Analyzer](roslyn-analyzers-overview.md) Regeln:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502-avoid-excessive-complexity.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506-avoid-excessive-class-coupling.md)

Diese Regeln sind standardmäßig deaktiviert, jedoch können sie aus [ **Projektmappen-Explorer** ](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) oder in einem [Regelsatz](using-rule-sets-to-group-code-analysis-rules.md) Datei. Um die Regel CA1502 als Warnung zu aktivieren, würde die RULESET-Datei z. B. den folgenden Eintrag enthalten:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Konfiguration

Sie können die Schwellenwerte konfigurieren, an denen die Regeln in die FxCop-Analysetools Metriken ausgelöst Paket.

1. Erstellen einer Textdatei Beispielsweise können Sie sie benennen *CodeMetricsConfig.txt*.

2. Fügen Sie die gewünschten Schwellenwerte in die Textdatei in folgendem Format ein:

   ```txt
   CA1502: 10
   ```

   In diesem Beispiel Regel [CA1502](ca1502-avoid-excessive-complexity.md) ausgelöst werden, wenn eine Methode, die zyklomatische Komplexität größer als 10 ist konfiguriert ist.

3. In der **Eigenschaften** Fenster von Visual Studio oder in der Projektdatei, markieren Sie die Buildaktion der Konfigurationsdatei als [ **AdditionalFiles**](../ide/build-actions.md#build-action-values). Zum Beispiel:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Kontextmenübefehl von "Code Metrics" berechnet

Codemetrik für eine oder alle der die geöffneten Projekte in der IDE generieren Sie mit der **analysieren** > **Berechnen der Codemetrik** Menü.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Codemetrikergebnisse für eine gesamte Projektmappe generieren

Sie können Codemetrikergebnisse für eine gesamte Projektmappe in einem der folgenden Arten generieren:

- Wählen Sie in der Menüleiste **analysieren** > **Berechnen der Codemetrik** > **für Projektmappe**.

- In **Projektmappen-Explorer**mit der rechten Maustaste auf die Projektmappe, und wählen Sie dann **Berechnen der Codemetrik**.

- In der **Codemetrikergebnisse** Fenster, wählen Sie die **Berechnen der Codemetrik für Projektmappe** Schaltfläche.

Die Ergebnisse werden generiert und die **Codemetrikergebnisse** Fenster wird angezeigt. Um die Ergebnisdetails anzuzeigen, erweitern Sie die Struktur in der **Hierarchie** Spalte.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generieren Sie Codemetrikergebnisse für ein oder mehrere Projekte

1. In **Projektmappen-Explorer**, wählen Sie ein oder mehrere Projekte.

1. Wählen Sie in der Menüleiste **analysieren** > **Berechnen der Codemetrik** > **für ausgewählte Projekte**.

Die Ergebnisse werden generiert und die **Codemetrikergebnisse** Fenster wird angezeigt. Um die Ergebnisdetails anzuzeigen, erweitern Sie die Struktur in der **Hierarchie**.

::: moniker range="vs-2017"

> [!NOTE]
> Die **Berechnen der Codemetrik** Befehl funktioniert nicht für .NET Core und .NET Standard-Projekte. Zum Berechnen der Codemetrik für ein Projekt für .NET Core oder .NET Standard können Sie folgende Aktionen ausführen:
>
> - Berechnen der Codemetrik aus der [Befehlszeile](#command-line-code-metrics) stattdessen
>
> - Upgrade auf [2019 für Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

::: moniker-end

## <a name="command-line-code-metrics"></a>Befehlszeile Codemetrik

Generieren von Codemetrikdaten werden über die Befehlszeile für C# und Visual Basic-Projekten für .NET Framework, .NET Core und .NET Standard-apps. Um codemetriken über die Befehlszeile auszuführen, installieren die [Microsoft.CodeAnalysis.Metrics NuGet-Paket](#microsoftcodeanalysismetrics-nuget-package) , oder erstellen Sie die [Metrics.exe](#metricsexe) ausführbare selbst.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Microsoft.CodeAnalysis.Metrics NuGet-Paket

Die einfachste Möglichkeit zum Generieren von Codemetrikdaten werden über die Befehlszeile wird durch die Installation der [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet-Paket. Nachdem Sie das Paket installiert haben, führen Sie `msbuild /t:Metrics` aus dem Verzeichnis, das die Projektdatei enthält. Zum Beispiel:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Sie können den Namen der Ausgabedatei überschreiben, indem Sie die Angabe `/p:MetricsOutputFile=<filename>`. Sie erhalten auch [herkömmlicher](#previous-versions) Metrikdaten von code durch die Angabe `/p:LEGACY_CODE_METRICS_MODE=true`. Zum Beispiel:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Ausgabe von Metriken

Die generierte XML-Ausgabe hat das folgende Format:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>Metrics.exe

Wenn Sie nicht das NuGet-Paket installieren möchten, können Sie generieren und verwenden Sie die *Metrics.exe* ausführbare Datei direkt. Zum Generieren der *Metrics.exe* ausführbare Datei:

1. Klonen der [Dotnet/Roslyn-Analyzers](https://github.com/dotnet/roslyn-analyzers) Repository.
2. Öffnen Sie Developer-Eingabeaufforderung für Visual Studio als Administrator an.
3. Ausgehend vom Stamm des der **Roslyn-Analyzers** Repository, führen Sie den folgenden Befehl: `Restore.cmd`
4. Wechseln Sie zum Verzeichnis *Src\Tools*.
5. Führen Sie den folgenden Befehl zum Erstellen der **Metrics.csproj** Projekt:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Eine ausführbare Datei namens *Metrics.exe* wird generiert, der *Artifacts\bin* Verzeichnis unter dem Stammverzeichnis des Repositorys.

#### <a name="metricsexe-usage"></a>Metrics.exe Nutzung

Auszuführende *Metrics.exe*, geben Sie ein Projekt oder Projektmappe und ein Ausgabe-XML-Datei als Argumente. Zum Beispiel:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Legacy-Modus

Sie können auch build *Metrics.exe* in *Legacymodus*. Die legacy-Modus-Version des Tools wird generiert, die metrischen Werte, die näher zu [ältere Versionen des Tools generierte](#previous-versions). Darüber hinaus im Legacymodus *Metrics.exe* Codemetrik generiert, der gleiche Satz von der Methode, vorherige Versionen von die Tool-erzeugte codemetriken für die Datentypen. Z. B. nicht es Codemetrikdaten für Feld "und"-Eigenschaft-Initialisierer generieren. Legacy-Modus eignet sich für Abwärtskompatibilität Kompatibilitäts- oder wenn Sie Code Einchecken Gates haben Codemetrik Zahlen basierend auf. Der Befehl zum Erstellen *Metrics.exe* im Legacymodus ist:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Weitere Informationen finden Sie unter [aktivieren, Generieren von Codemetrikdaten im Legacymodus](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Frühere Versionen

Visual Studio 2015 bietet ein Befehlszeilentool Metriken-Tool, das so genannte wurde *Metrics.exe*. Diese frühere Version des Tools wurde eine binäre Analyse, d. h. eine Assembly-basierte Analyse. Die neue *Metrics.exe* stattdessen Tool analysiert die Source-Code. Da die neue *Metrics.exe* Tool ist der Code basiert, Befehlszeilen Code datenquellenmetriken Ergebnisse, die von Visual Studio-IDE und früheren Versionen von generiert unterscheiden *Metrics.exe*.

Das neue Befehlszeilentool Metriken Tool berechnet Metriken auch bei der Quelle von Codefehlern, solange die Projektmappen- und Projektdateien geladen werden können.

#### <a name="metric-value-differences"></a>Metrikwert Unterschiede

Die `LinesOfCode` Metrik ist genauer und zuverlässiger, in das neue Befehlszeilentool Metriken-Tool. Dabei handelt es sich unabhängig von Codegen Unterschiede nicht geändert werden, wenn das Toolset oder Laufzeit ändert. Das neue Tool zählt, tatsächliche Zeilen von Code, einschließlich Leerzeilen und Kommentare.

Andere Metriken wie z. B. `CyclomaticComplexity` und `MaintainabilityIndex` verwenden die gleichen Formeln wie in früheren Versionen von *Metrics.exe*, aber das neue Tool zählt die Anzahl der `IOperations` (logische Quelle Anweisungen) anstelle von fortgeschrittene Language (IL)-Anweisungen. Die Zahlen unterscheiden sich geringfügig auf die von Visual Studio-IDE und früheren Versionen von generiert *Metrics.exe*.

## <a name="see-also"></a>Siehe auch

- [Verwenden Sie das Fenster Codemetrikergebnisse](../code-quality/working-with-code-metrics-data.md)
- [Codemetrikwerte](../code-quality/code-metrics-values.md)
