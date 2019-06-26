---
title: Live Unit Testing – häufig gestellte Fragen
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 1ed80454f6a87047de9e338d26c749d3c27a98ea
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67258130"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing – FAQ (Häufig gestellte Fragen)

## <a name="latest-features"></a>Neueste Funktionen

**Live Unit Testing wird regelmäßig verbessert und erweitert. Wie finde ich Informationen zu den neuesten Features und Verbesserungen?**

Weitere Informationen zu neuen Features und Verbesserungen für Live Unit Testing finden Sie unter [Neuerungen in Live Unit Testing](live-unit-testing-whats-new.md).

## <a name="supported-frameworks-and-versions"></a>Unterstützte Frameworks und Versionen

**Welche Testframeworks werden von Live Unit Testing unterstützt, und wie lauten die unterstützten Mindestversionen?**

Live Unit Testing kann mit den drei gängigen Frameworks für Komponententests verwendet werden, die in der folgenden Tabelle aufgeführt sind. Die unterstützte Mindestversion der Adapter und Frameworks ist ebenfalls in der Tabelle aufgeführt. Die Frameworks für Komponententests sind auf „NuGet.org“ verfügbar.

|Testframework  |Mindestversion des Visual Studio-Adapters  |Mindestversion des Frameworks  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio, Version 2.2.0-beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter, Version 3.7.0 |NUnit, Version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Wenn Sie ältere auf MSTest-basierende Testprojekte haben, die sich auf `Microsoft.VisualStudio.QualityTools.UnitTestFramework` beziehen, und Sie nicht auf die neueren MSTest-NuGet-Pakete umsteigen möchten, sollten Sie auf Visual Studio 2017 Version 15.4 oder höher upgraden.

In einigen Fällen müssen Sie explizit die NuGet-Pakete wiederherstellen, auf die die Projekte in der Projektmappe verweisen, damit Live Unit Testing funktioniert. Erstellen Sie zum Wiederherstellen der Pakete entweder explizit die Projektmappe (wählen Sie im obersten Visual Studio-Menü **Erstellen** und dann **Projektmappe neu erstellen** aus), oder klicken Sie mit der rechten Maustaste auf die Projektmappe, und wählen Sie **NuGet-Pakete wiederherstellen** aus, bevor Sie Live Unit Testing aktivieren.

## <a name="net-core-support"></a>.NET Core-Unterstützung

**Kann Live Unit Testing mit .NET Core verwendet werden?**

Ja. Live Unit Testing funktioniert mit .NET Core und .NET Frameworks. Die Unterstützung für .NET Core wurde in Visual Studio 2017 Version 15.3 hinzugefügt. Führen Sie ein Upgrade auf diese oder eine höhere Version von Visual Studio aus, wenn Sie die Live Unit Testing-Unterstützung für .NET Core möchten.

## <a name="configuration"></a>Konfiguration

**Warum funktioniert Live Unit Testing nicht, wenn ich diese Funktion aktiviere?**

Das **Ausgabefenster** (wenn das Live Unit Testing-Dropdownmenü ausgewählt ist) sollte Ihnen sagen, warum Live Unit Testing nicht funktioniert. Live Unit Testing funktioniert möglicherweise aus einem der folgenden Gründe nicht:

- Wenn die NuGet-Pakete, auf die von Projekten in der Projektmappe verwiesen wird, nicht wiederhergestellt wurden, funktioniert Live Unit Testing nicht. Eine explizite Erstellung der Projektmappe oder das Wiederherstellen von NuGet-Paketen in der Projektmappe vor dem Aktivieren von Live Unit Testing sollte dieses Problem beheben.

- Wenn Sie MSTest-basierte Tests in den Projekten verwenden, stellen Sie sicher, dass Sie den Verweis auf `Microsoft.VisualStudio.QualityTools.UnitTestFramework` entfernen und Verweise auf die neuesten MSTest-NuGet-Pakete `MSTest.TestAdapter` (Mindestversion 1.1.11 ist erforderlich) und `MSTest.TestFramework` (Mindestversion 1.1.11 ist erforderlich) hinzufügen. Weitere Informationen finden Sie im Abschnitt „Unterstützte Testframeworks“ im Artikel [Verwenden von Live Unit Testing in Visual Studio](live-unit-testing.md#supported-test-frameworks).

- Mindestens ein Projekt in der Projektmappe muss einen NuGet-Verweis oder einen direkten Verweis auf das xUnit-, NUnit- oder MSTest-Testframework aufweisen. Dieses Projekt sollte auch auf ein entsprechendes NuGet-Paket mit Visual Studio-Testadaptern verweisen. Auf den Visual Studio-Testadapter kann auch über eine *.runsettings*-Datei verwiesen werden. Die *.runsettings*-Datei muss einen Eintrag wie im folgenden Beispiel enthalten:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Falsche Coverage nach Upgrade

**Warum wird beim Live Unit Testing eine falsche Coverage angezeigt, nachdem Sie ein Upgrade auf den in Ihren Visual Studio-Projekten verwiesenen Testadapter auf die unterstützte Version durchgeführt haben?**

- Wenn mehrere Projekte in der Projektmappe auf das NuGet-Testadapterpaket verweisen, muss jedes auf die unterstützte Version upgegradet werden.

- Stellen Sie sicher, dass die Datei „MSBuild *.props*“, die aus dem Testadapterpaket importiert wurde, ebenfalls ordnungsgemäß aktualisiert wird. Überprüfen Sie die NuGet-Paket Version bzw. den Pfad des Imports, der sich in der Regel am Anfang der Datei befindet, z.B.:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Anpassen von Builds

**Kann ich meine Live Unit Testing-Builds anpassen?**

Wenn Ihre Projektmappe benutzerdefinierte Schritte für einen Buildvorgang zur Instrumentierung erfordert (Live Unit Testing), die für den „normalen“, nicht instrumentierten Build, nicht erforderlich sind, dann können Sie Code zum Projekt oder zu *.targets*-Dateien hinzufügen, der auf die Eigenschaft `BuildingForLiveUnitTesting` prüft und vorab oder anschließend benutzerdefinierte Buildschritte ausführt. Sie können basierend auf dieser Eigenschaft auch bestimmte Buildschritte entfernen (z.B. Veröffentlichen oder Generieren von Paketen) oder einem Live Unit Testing-Build Buildschritte hinzuzufügen (z.B. Kopieren der erforderlichen Komponenten). Das Anpassen Ihres Builds basierend auf dieser Eigenschaft verändert Ihren „normalen“ Build in keinster Weise und hat nur Auswirkungen auf Live Unit Testing-Builds.

Möglicherweise gibt es z.B. ein Ziel, das NuGet-Pakete während eines regulären Buildvorgangs erzeugt. Sie möchten wahrscheinlich nicht, dass NuGet-Pakete nach jeder Änderung generiert werden. Also können Sie dieses Ziel im Live Unit Testing-Build deaktivieren, indem Sie z.B. Folgendes ausführen:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Fehlermeldungen mit &lt;OutputPath&gt; oder &lt;OutDir&gt;

**Wenn Live Unit Testing versucht, meine Projektmappe zu erstellen, warum wird dann folgende Fehlermeldung angezeigt: „`<OutputPath>` oder `<OutDir>` werden scheinbar ohne Bedingungen festgelegt, und Live Unit Testing führt keine Tests der Ausgabeassembly aus“?**

Dieser Fehler kann auftreten, wenn der Buildvorgang für Ihre Projektmappe bedingungslos `<OutputPath>` oder `<OutDir>` überschreibt, sodass diese Elemente kein Unterverzeichnis von `<BaseOutputPath>` sind. In solchen Fällen funktioniert Live Unit Testing nicht, da von der Funktion diese Werte auch überschrieben werden, um sicherzustellen, dass Buildartefakte in einem Ordner unter `<BaseOutputPath>` abgelegt werden. Wenn Sie den Speicherort überschreiben müssen, in dem Ihre Buildartefakte in einem regulären Build abgelegt werden, überschreiben Sie `<OutputPath>` bedingt basierend auf `<BaseOutputPath>`.

Beispiel: Ihr Build überschreibt `<OutputPath>`, wie unten dargestellt:

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

Dann können Sie ihn durch folgende XML ersetzen:

```xml 
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Dadurch wird sichergestellt, dass sich `<OutputPath>` im Ordner `<BaseOutputPath>` befindet.

Überschreiben Sie `<OutDir>` nicht direkt im Buildvorgang. Überschreiben Sie stattdessen `<OutputPath>`, um Buildartefakte an einem bestimmten Speicherort abzulegen.

## <a name="set-the-location-of-build-artifacts"></a>Festlegen des Speicherorts für Buildartefakte

**Ich möchte die Artefakte eines Live Unit Testing-Builds an einem bestimmten Speicherort ablegen, statt den Standardspeicherort im Ordner *.vs* zu verwenden. Wie kann ich ihn ändern?**

Legen Sie die `LiveUnitTesting_BuildRoot`-Umgebungsvariable auf Benutzerebene auf den Pfad fest, in dem die Live Unit Testing-Buildartefakte abgelegt werden sollen. 

## <a name="test-explorer-vs-live-unit-testing-test-runs"></a>Test-Explorer- und Live Unit Testing-Testläufe im Vergleich

**Wie unterscheidet sich das Ausführen von Tests im Test-Explorer-Fenster vom Ausführen von Tests in Live Unit Testing?**

Es gibt mehrere Unterschiede:

- Beim Ausführen oder Debuggen von Tests im Fenster **Test-Explorer** werden reguläre Binärdateien ausgeführt. Live Unit Testing führt dagegen instrumentierte Binärdateien aus. Wenn Sie instrumentierte Binärdateien debuggen möchten, wird durch das Hinzufügen eines [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) -Methodenaufrufs in der Testmethode der Debugger bei jeder Ausführung der Methode gestartet (auch bei der Ausführung durch Live Unit Testing), und Sie können dann die instrumentierte Binärdatei anfügen und debuggen. Wir hoffen jedoch, dass die Instrumentierung der meisten Benutzerszenarien für Sie transparent ist und Sie instrumentierte Binärdateien nicht debuggen müssen.

- Live Unit Testing erstellt keine neue Anwendungsdomäne zum Ausführen von Tests. Tests, die im Fenster **Test-Explorer** ausgeführt werden, erstellen dagegen eine neue Anwendungsdomäne.

- Live Unit Testing testet jede Testassembly sequenziell. Wenn Sie jedoch mehrere Tests im Fenster **Test-Explorer** ausführen und die Schaltfläche **Tests parallel ausführen** ausgewählt haben, werden sie parallel ausgeführt.

- Für die Ermittlung und Ausführung von Tests in Live Unit Testing wird Version 2 von `TestPlatform` verwendet, während im Fenster **Test-Explorer** Version 1 verwendet wird. In den meisten Fällen sollten Sie allerdings keinen Unterschied feststellen.

- **Test-Explorer** führt Tests derzeit standardmäßig in einem Singlethread-Apartment (STA) aus, während Live Unit Testing Tests in einem Multithread-Apartment (MTA) ausführt. Um MSTest-Tests in STA in Live Unit Testing auszuführen, versehen Sie die Testmethode oder die enthaltende Klasse mit dem `<STATestMethod>`- oder dem `<STATestClass>`-Attribut, das im NuGet-Paket `MSTest.STAExtensions 1.0.3-beta` enthalten ist. Ergänzen Sie für NUnit die Testmethode mit dem `<RequiresThread(ApartmentState.STA)>`-Attribut, und für xUnit mit dem `<STAFact>`-Attribut.

## <a name="exclude-tests"></a>Ausschließen von Tests

**Wie schließe ich Tests von Live Unit Testing aus?**

Die benutzerspezifische Einstellung finden Sie im Abschnitt „Einschließen und Ausschließen von Testprojekten und Testmethoden“ im Artikel [Verwenden von Live Unit Testing in Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods). Das Ein- und Ausschließen von Tests ist nützlich, wenn Sie eine bestimmte Reihe von Tests für eine bestimmte Bearbeitungssitzung ausführen möchten oder Ihre eigenen persönlichen Einstellungen beibehalten möchten.

Bei spezifischen Einstellungen von Projektmappen können Sie das <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName>-Attribut programmgesteuert anwenden, um Methoden, Eigenschaften, Klassen oder Strukturen von der Instrumentierung durch Live Unit Testing auszuschließen. Darüber hinaus können Sie auch die `<ExcludeFromCodeCoverage>`-Eigenschaft in der Projektdatei auf `true` festlegen, um zu verhindern, dass das gesamte Projekt instrumentiert wird. Live Unit Testing führt die Tests dennoch aus, die nicht instrumentiert wurden, aber deren Abdeckung wird nicht visuell dargestellt.

Sie können auch überprüfen, ob `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` in der aktuellen Anwendungsdomäne geladen wird und auf dieser Grundlage Tests deaktivieren. Beispielsweise können Sie mit xUnit Folgendes ausführen:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

## <a name="win32-pe-headers"></a>Win32 PE-Header

**Warum sind Win32 PE-Header in von Live Unit Testing erstellten instrumentierten Assemblys anders?**

Dieses Problem wurde behoben und besteht ab Visual Studio 2017 Version 15.3 nicht mehr.

Für ältere Versionen von Visual Studio 2017 gibt es ein bekanntes Problem, das dazu führen kann, dass Live Unit Testing-Builds die folgenden Win32 PE-Headerdaten nicht einbetten:

- Dateiversion (angegeben durch @System.Reflection.AssemblyFileVersionAttribute im Code).

- Win32-Symbol (angegeben durch `/win32icon:` an der Befehlszeile).

- Win32-Manifest (angegeben durch `/win32manifest:` an der Befehlszeile).

Tests, die auf diesen Werten basieren, können fehlschlagen, wenn sie von Live Unit Testing ausgeführt werden.

## <a name="continuous-builds"></a>Fortlaufende Builds

**Warum erstellt Live Unit Testing meine Projektmappe immer wieder, auch wenn ich keine Änderungen vornehme?**

Ihre Projektmappe kann sogar erstellt werden, wenn Sie keine Änderungen vornehmen, wenn der Buildvorgang der Projektmappe Quellcode generiert, der Teil der Projektmappe selbst ist, und in den Zieldateien des Builds keine entsprechenden Eingaben und Ausgaben angegeben sind. Zielen sollte eine Liste von Eingaben und Ausgaben bereitgestellt werden, damit MSBuild die entsprechenden aktuellen Überprüfungen vornehmen kann und bestimmen kann, ob ein neuer Build erforderlich ist.

Live Unit Testing startet einen Buildvorgang, wenn erkannt wird, dass Quelldateien geändert wurden. Da der Buildvorgang Ihrer Projektmappe Quelldateien generiert, gerät Live Unit Testing in eine unendliche Buildschleife. Wenn die Eingaben und Ausgaben des Ziels jedoch überprüft werden, wenn Live Unit Testing den zweiten Buildvorgang startet (nach der Ermittlung neu generierter Quelldateien aus dem vorherigen Build), wird die Buildschleife unterbrochen, da die Überprüfungen der Eingaben und Ausgaben darauf hinweisen, dass alles auf dem neuesten Stand ist.  

## <a name="new-process-coverage"></a>Coverage für neue Prozesse

**Warum erfasst Live Unit Testing die Coverage eines neuen Prozesses nicht, der über einen Test erstellt wurde?**

Dies ist ein bekanntes Problem und sollte in einem späteren Release behoben werden.

## <a name="including-or-excluding-tests-doesnt-work"></a>Ein- oder Ausschließen von Tests funktioniert nicht

**Warum geschieht nichts, nachdem ich Tests in den Satz von Livetests eingeschlossen bzw. davon ausgeschlossen habe?**

Dieses Problem wurde behoben und besteht ab Visual Studio 2017 Version 15.3 nicht mehr.

Für ältere Versionen von Visual Studio 2017 ist dies ein bekanntes Problem. Um dieses Problem zu umgehen, müssen Sie in einer beliebigen Datei eine Änderung vornehmen, nachdem Sie Tests eingeschlossen oder ausgeschlossen haben.

## <a name="editor-icons"></a>Editorsymbole

**Warum werden keine Symbole im Editor angezeigt, obwohl Live Unit Testing basierend auf den Meldungen im Ausgabefenster Tests auszuführen scheint?**

Es werden möglicherweise keine Symbole im Editor angezeigt, wenn die Assemblys, die von Live Unit Testing verarbeitet werden, nicht instrumentiert werden. Beispielsweise ist Live Unit Testing nicht kompatibel mit Projekten, die `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` festlegen. In diesem Fall muss der Buildvorgang aktualisiert werden, um diese Einstellung zu entfernen oder in `true` zu ändern, damit Live Unit Testing funktioniert. 

## <a name="capture-logs"></a>Erfassen von Protokollen

**Wie kann ich ausführlichere Protokolle für Dateifehlerberichte erfassen?**

Sie haben mehrere Möglichkeiten, um ausführlichere Protokolle zu sammeln:

- Wechseln Sie zu **Extras** > **Optionen** > **Live Unit Testing**, und ändern Sie die Protokollierungsoption in **Ausführlich**. Durch die ausführliche Protokollierung werden detailliertere Protokolle im **Ausgabefenster** angezeigt.

- Legen Sie die `LiveUnitTesting_BuildLog`-Benutzerumgebungsvariable auf den Namen der Datei fest, die Sie verwenden möchten, um das MSBuild-Protokoll zu erfassen. Detaillierte MSBuild-Protokollmeldungen von Live Unit Testing-Builds können dann aus dieser Datei abgerufen werden.

- Legen Sie die Umgebungsvariable`LiveUnitTesting_TestPlatformLog` auf `1` fest, um das Protokoll der Testplattform zu erfassen. Detaillierte Testplattform-Protokollmeldungen zu Live Unit Testing-Ausführungen können dann aus `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` abgerufen werden.

- Erstellen Sie eine Umgebungsvariable auf Benutzerebene mit dem Namen `VS_UTE_DIAGNOSTICS`, legen Sie sie auf 1 (oder einen beliebigen Wert) fest, und starten Sie Visual Studio neu. Jetzt sollten Sie eine umfangreiche Protokollierung auf der Registerkarte **Ausgabe – Tests** in Visual Studio sehen.

## <a name="see-also"></a>Siehe auch

- [Live-Komponententests](live-unit-testing.md)
