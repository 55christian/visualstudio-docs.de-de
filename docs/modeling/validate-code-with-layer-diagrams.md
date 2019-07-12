---
title: Überprüfen von Code mit Abhängigkeitsdiagrammen
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e21c3699d796d6037d3b8ca0e744e792b9810b6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824538"
---
# <a name="validate-code-with-dependency-diagrams"></a>Überprüfen von Code mit Abhängigkeitsdiagrammen

## <a name="why-use-dependency-diagrams"></a>Gründe für die Verwendung von Abhängigkeitsdiagrammen

Um sicherzustellen, dass der Code dem Entwurf nicht widerspricht ist, können überprüfen Sie Ihren Code mit Abhängigkeitsdiagrammen in Visual Studio. Dadurch wird Folgendes ermöglicht:

- Finden Sie Konflikte zwischen Abhängigkeiten im Code und Abhängigkeiten im Diagramm der Abhängigkeit an.

- Ermitteln von Abhängigkeiten, die möglicherweise von vorgeschlagenen Änderungen betroffen sind

   Beispielsweise können Sie durch Bearbeiten des Dependency-Diagramms, um potenzielle architekturänderungen darzustellen, und überprüfen Sie anschließend den Code, um die betroffenen Abhängigkeiten zu ermitteln.

- Umgestalten oder Migrieren von Code in einen anderen Entwurf

   Ermitteln von Code oder Abhängigkeiten, die bei der Umstellung des Codes auf eine andere Architektur noch bearbeitet werden müssen

**Anforderungen**

- Visual Studio

- Eine Lösung, die ein Modellierungsprojekt mit einem Abhängigkeitsdiagramm enthält. In diesem Abhängigkeitsdiagramm muss mit Artefakten in c# oder Visual Basic-Projekten verknüpft sein, die Sie überprüfen möchten. Finden Sie unter [Erstellen von Abhängigkeitsdiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md).

> [!NOTE]
> Abhängigkeitsdiagramme werden für .NET Core-Projekte in Visual Studio nicht unterstützt.

Welche Editionen von Visual Studio dieses Feature unterstützen, finden Sie unter [Edition-Unterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Sie können den Code manuell aus einer open Abhängigkeitsdiagramm in Visual Studio oder über eine Eingabeaufforderung überprüfen. Sie können Code auch automatisch überprüfen, wenn das Ausführen von lokalen Builds oder Azure-Pipelines erstellt. Finden Sie unter [Channel 9-Video: Entwerfen und Überprüfen der Architektur, die mithilfe von Abhängigkeitsdiagrammen](http://go.microsoft.com/fwlink/?LinkID=252073).

> [!IMPORTANT]
> Wenn Sie die ebenenvalidierung mit Team Foundation Server (TFS) ausführen möchten, müssen Sie auch die gleiche Version von Visual Studio auf dem Buildserver installieren.

## <a name="live-dependency-validation"></a>Liveüberprüfung von Abhängigkeiten

Abhängigkeit von Überprüfungen in Echtzeit und Fehler werden sofort angezeigt, der **Fehlerliste**.

* Live-Überprüfung wird für c# und Visual Basic unterstützt.

* Öffnen Sie die optionseinstellungen aus der goldenen Leiste, die in angezeigt, um vollständige projektmappenanalyse aktivieren bei Verwendung von live-abhängigkeitsüberprüfung der **Fehlerliste**.

  - Sie können die goldenen Leiste dauerhaft schließen, wenn Sie nicht alle Architektur Probleme, die in der Projektmappe interessiert sind.
  - Wenn Sie nicht vollständige projektmappenanalyse aktivieren, erfolgt die Analyse nur für die Dateien, die bearbeitet wird.

* Wenn Sie Projekte zum Aktivieren von live-Überprüfung zu aktualisieren, zeigt ein Dialogfeld den Status der Konvertierung.

* Wenn Sie ein Projekt für die liveüberprüfung von Abhängigkeiten zu aktualisieren, wird die Version des NuGet-Pakets wird aktualisiert, sodass für alle Projekte gleich sein, und ist die höchste Version verwendet.

* Eine neue Abhängigkeit Überprüfung Projekt Trigger wird ein Projektupdate hinzugefügt.

## <a name="see-if-an-item-supports-validation"></a>Sehen, ob ein Element die Validierung unterstützt

Sie können Ebenen verknüpfen, auf Websites, Office-Dokumente, nur-Text-Dateien und Dateien in Projekten, die für mehrere apps freigegeben werden, aber bei der Prüfung nicht enthalten sind. Für Verweise auf Projekte oder Assemblys, die mit separaten Ebenen verknüpft sind, treten keine Validierungsfehler auf, wenn keine Abhängigkeiten zwischen diesen Ebenen angezeigt werden. Solche Verweise werden nur dann als Abhängigkeiten betrachtet, wenn sie im Code verwendet werden.

1. Wählen Sie auf das Abhängigkeitsdiagramm, eine oder mehrere Ebenen, mit der rechten Maustaste in der Auswahl, und klicken Sie dann auf **Links anzeigen**.

2. In **Ebenen-Explorer**, sehen Sie sich die **unterstützt die Validierung** Spalte. Wenn der Wert „false“ ist, wird die Validierung vom Element nicht unterstützt.

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>Andere .NET-Assemblys und Projekte zur Validierung einschließen

Beim Ziehen von Elementen zum Abhängigkeitsdiagramm werden automatisch Verweise auf die entsprechenden .NET-Assemblys oder Projekte hinzugefügt der **Ebenenverweise** Ordner im Modellierungsprojekt. Dieser Ordner enthält Verweise auf die Assemblys und Projekte, die bei der Validierung analysiert werden. Sie können weitere .NET-Assemblys und-Projekte zur Validierung einschließen, ohne manuell mit dem Dependency-Diagramm ziehen.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Modellierungsprojekts oder **Ebenenverweise** Ordner, und klicken Sie dann auf **Verweis hinzufügen**.

2. In der **Verweis hinzufügen** Dialogfeld Wählen Sie die Assemblys oder Projekte, und klicken Sie dann auf **OK**.

## <a name="validate-code-manually"></a>Code manuell überprüfen

Wenn Sie ein Abhängigkeitsdiagramm öffnen-, das mit Projektmappenelementen verknüpft ist verfügen, können Sie Ausführen den **überprüfen** Kurzbefehl aus dem Diagramm. Sie können auch die Eingabeaufforderung verwenden, zum Ausführen der **Msbuild** -Befehl mit der **ValidateArchitecture** benutzerdefinierte Eigenschaft, die auf **"true"** . Bei Codeänderungen sollten Sie beispielsweise regelmäßig eine Ebenenvalidierung durchführen, um Abhängigkeitskonflikte frühzeitig lösen zu können.

### <a name="validate-code-from-an-open-dependency-diagram"></a>Überprüfen von Code aus einem Abhängigkeitsdiagramm öffnen

1. Mit der rechten Maustaste in der Diagrammoberfläche, und klicken Sie dann auf **Architektur überprüfen**.

    > [!NOTE]
    > In der Standardeinstellung die **Buildvorgang** auf die Ebenendiagrammdatei (.layerdiagram)-Abhängigkeitsdatei-Eigenschaftensatz auf **überprüfen** , damit das Diagramm in den Validierungsprozess eingeschlossen wird.

     Die **Fehlerliste** Fenster zeigt alle auftretenden Fehler. Weitere Informationen zu Validierungsfehlern finden Sie unter [Ebenenvalidierungsprobleme](#troubleshoot-layer-validation-issues).

2. Um die Quelle der einzelnen Fehler anzuzeigen, doppelklicken Sie auf den Fehler in der **Fehlerliste** Fenster.

    > [!NOTE]
    > Visual Studio, möglicherweise anstelle der Quelle des Fehlers eine Code Map angezeigt. Dies tritt auf, wenn der Code weist eine Abhängigkeit einer Assembly, die im Diagramm für die Abhängigkeit nicht angegeben ist oder der Code fehlt eine Abhängigkeit, die durch das Abhängigkeitsdiagramm angegeben wird. Überprüfen Sie die Code Map oder den Code, um festzustellen, ob die Abhängigkeit vorhanden sein sollte. Weitere Informationen zu codezuordnungen finden Sie unter [projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md).

3. Verwalten von Fehlern finden Sie unter [Lösen von Ebenenvalidierungsfehlern](#resolve-layer-validation-errors).

### <a name="validate-code-at-the-command-prompt"></a>Überprüfen von Code an der Eingabeaufforderung

1. Öffnen Sie die Visual Studio-Eingabeaufforderung.

2. Wählen Sie eine der folgenden Optionen aus:

   - Wenn Sie um Code anhand eines bestimmten Modellierungsprojekts in der Lösung zu überprüfen, führen Sie MSBuild mit der folgenden benutzerdefinierten Eigenschaft aus.

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - ODER

       Navigieren Sie zu dem Ordner, der das Modellierungsprojekt (.modelproj) enthält Datei- und die Abhängigkeit, und führen Sie MSBuild mit der folgenden benutzerdefinierten Eigenschaft:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - Um den Code anhand aller Modellierungsprojekte in der Projektmappe überprüfen möchten, führen Sie MSBuild mit der folgenden benutzerdefinierten Eigenschaft aus:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - ODER

       Navigieren Sie in den Projektmappenordner, der ein Modellierungsprojekt, das ein Abhängigkeitsdiagramm enthält, und führen Sie MSBuild mit der folgenden benutzerdefinierten Eigenschaft:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     Alle aufgetretenen Fehler werden aufgelistet. Weitere Informationen zu MSBuild finden Sie unter [MSBuild](../msbuild/msbuild.md) und [MSBuild-Aufgabe](../msbuild/msbuild-task.md).

   Weitere Informationen zu Validierungsfehlern finden Sie unter [Ebenenvalidierungsprobleme](#troubleshoot-layer-validation-issues).

### <a name="manage-validation-errors"></a>Validierungsfehler verwalten

Während des Entwicklungsprozesses können Sie ggf. einige der Konflikte unterdrücken, die während der Validierung gemeldet werden. Beispielsweise können Sie Fehler unterdrücken, die Sie bereits behandeln oder die für das spezifische Szenario nicht relevant sind. Wenn Sie Fehler unterdrücken, ist es sich bewährt, melden Sie sich eine Arbeitsaufgabe in Team Foundation.

> [!WARNING]
> Sie müssen bereits mit der TFS-Quellcodeverwaltung verbunden sein, um ein Arbeitselement zu erstellen oder zu verknüpfen. Wenn Sie versuchen, eine Verbindung mit einer anderen TFS-Quellcodeverwaltung herzustellen, schließt Visual Studio automatisch die aktuelle Projektmappe. Stellen Sie sicher, dass Sie bereits mit der richtigen Quellcodeverwaltung verbunden sind, bevor Sie versuchen, ein Arbeitselement zu erstellen oder zu verknüpfen. In höheren Versionen von Visual Studio stehen die Menübefehle nicht zur Verfügung, wenn Sie mit keiner Quellcodeverwaltung verbunden sind.

#### <a name="create-a-work-item-for-a-validation-error"></a>Erstellen eines Arbeitselements für einen Validierungsfehler

- In der **Fehlerliste** Fenster mit der rechten Maustaste in des Fehlers, zeigen Sie auf **Arbeitsaufgabe erstellen**, und klicken Sie dann auf den Typ der Arbeitsaufgabe, die Sie erstellen möchten.

Mit diesen Tasks können Validierungsfehler im der **Fehlerliste** Fenster:

|**Aktion**|**Gehen Sie folgendermaßen vor**|
|-|-|
|Unterdrücken von ausgewählten Fehlern während der Validierung|Mit der rechten Maustaste in die eine oder mehrere ausgewählte Fehler, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Fehler unterdrücken**.<br /><br /> Die unterdrückten Fehler werden durchgestrichen dargestellt. Beim nächsten Ausführen der Validierung werden diese Fehler nicht mehr angezeigt.<br /><br /> Unterdrückten Fehler werden in einer suppressions-Datei für die entsprechende Abhängigkeitseigenschaft Diagrammdatei nachverfolgt.|
|Beenden der Unterdrückung von ausgewählten Fehlern|Mit der rechten Maustaste den oder die ausgewählten unterdrückten Fehler, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Fehler nicht mehr unterdrücken**.<br /><br /> Beim nächsten Ausführen der Validierung werden die ausgewählten unterdrückten Fehler wieder angezeigt.|
|Wiederherstellen aller unterdrückten Fehler in der **Fehlerliste** Fenster|Mit der rechten Maustaste an einer beliebigen Stelle der **Fehlerliste** Fenster, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Unterdrückte Fehler anzeigen**.|
|Ausblenden aller unterdrückten Fehler aus der **Fehlerliste** Fenster|Mit der rechten Maustaste an einer beliebigen Stelle der **Fehlerliste** Fenster, zeigen Sie auf **Validierungsfehler**, und klicken Sie dann auf **Unterdrückte Fehler ausblenden**.|

## <a name="validate-code-automatically"></a>Code automatisch überprüfen

Sie können eine Ebenenvalidierung bei jeder Ausführung eines lokalen Builds durchführen. Wenn Ihr Team Azure DevOps verwendet, können Sie ebenenvalidierung mit gated-Check-ins, die Sie angeben können, indem Sie eine benutzerdefinierte MSBuild-Aufgabe und mithilfe von Buildberichten werden Validierungsfehler erfasst erstellen, ausführen. Erstellen von abgegrenzten Eincheckbuilds finden Sie [TFVC-gated-Check-in](/azure/devops/pipelines/build/triggers#gated).

### <a name="to-validate-code-automatically-during-a-local-build"></a>So überprüfen Sie Code automatisch während eines lokalen Builds

Öffnen Sie die Modellierungsprojektdatei (.modelproj) mithilfe eines Text-Editors, und fügen Sie dann die folgende Eigenschaft ein:

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- oder –

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Modellierungsprojekt, das Abhängigkeitsdiagramm oder Diagramme enthält, und klicken Sie dann auf **Eigenschaften**.

2. In der **Eigenschaften** legen des Modellierungsprojekts **Architektur überprüfen** Eigenschaft **"true"** .

    Dadurch wird das Modellierungsprojekt in den Validierungsprozess eingeschlossen.

3. In **Projektmappen-Explorer**, klicken Sie auf die Ebenendiagrammdatei (.layerdiagram)-Abhängigkeitsdatei, die Sie für die Validierung verwenden möchten.

4. In der **Eigenschaften** Fenster, stellen Sie sicher, dass des Diagramms **Buildvorgang** -Eigenschaftensatz auf **überprüfen**.

    Dies schließt das Abhängigkeitsdiagramm in den Validierungsprozess.

Verwalten von Fehlern in das Fenster "Fehlerliste" finden Sie unter [Lösen von Ebenenvalidierungsfehlern](#resolve-layer-validation-errors).

## <a name="troubleshoot-layer-validation-issues"></a>Ebenenvalidierungsprobleme beheben

In der folgenden Tabelle sind Ebenenvalidierungsprobleme und entsprechende Lösungen aufgeführt. Diese Probleme unterscheiden sich von Fehlern, die das Ergebnis von Konflikten zwischen Code und Entwurf sind. Weitere Informationen zu diesen Fehlern finden Sie unter [Ebenenvalidierungsprobleme](#troubleshoot-layer-validation-issues).

|**Problem**|**Mögliche Ursache**|**Auflösung**|
|-|-|-|
|Validierungsfehler treten nicht wie erwartet auf.|Validierung funktioniert in von Abhängigkeitsdiagrammen, die aus anderen Abhängigkeitsdiagramme im Projektmappen-Explorer kopiert werden und, nicht, die sich im gleichen Modellierungsprojekt. Abhängigkeitsdiagramme, die auf diese Weise kopiert werden, enthalten die gleichen Verweise wie das ursprüngliche Abhängigkeitsdiagramm.|Fügen Sie dem Modellierungsprojekt ein neues Abhängigkeitsdiagramm hinzu.<br /><br /> Kopieren Sie die Elemente aus dem Dependency-Quelldiagramm in das neue Diagramm ein.|

## <a name="resolve-layer-validation-errors"></a>Lösen von Ebenenvalidierungsfehlern

Beim Überprüfen von Code für ein Abhängigkeitsdiagramm treten Validierungsfehler auf, wenn der Code mit dem Entwurf in Konflikt steht. Validierungsfehler können beispielsweise unter folgenden Bedingungen auftreten:

- Ein Artefakt wurde der falschen Ebene zugewiesen. Verschieben Sie in diesem Fall das Artefakt.

- Von einem Artefakt (beispielsweise einer Klasse) wird eine andere Klasse auf eine Weise verwendet, die einen Konflikt mit der Architektur zur Folge hat. Gestalten Sie in diesem Fall den Code um, um die Abhängigkeit zu entfernen.

Aktualisieren Sie zum Beheben dieser Fehler den Code, bis bei der Validierung keine Fehler mehr angezeigt werden. Diese Aufgabe kann iterativ ausgeführt werden.

Im folgenden Abschnitt wird die Syntax beschrieben, die in diesen Fehlern verwendet wird. Außerdem wird die Bedeutung dieser Fehler erläutert, und es werden Vorschläge zur deren Behebung bzw. Verwaltung gegeben.

|**Syntax**|**Beschreibung**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN* ist ein Artefakt, das einer Ebene im Diagramm für die Abhängigkeitseigenschaft zugeordnet ist.<br /><br /> *ArtifactTypeN* ist der Typ des *ArtifactN*, z. B. eine **Klasse** oder **Methode**, z.B.:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|Der Name eines Namespace.|
|*LayerNameN*|Der Name einer Ebene im Diagramm der Abhängigkeit.|
|*DependencyType*|Der Typ der abhängigkeitsbeziehung zwischen *"Element1"* und *"Element2"* . Z. B. *"Element1"* verfügt über eine **Aufrufe** Beziehung mit *"Element2"* .|

| **Fehlersyntax** | **Fehlerbeschreibung** |
|-|-|
| DV0001: **Ungültige Abhängigkeit** | Dieses Problem wird gemeldet, wenn ein Codeelement (Namespace-, Typ-, Memberbereich) eine Ebenenverweise ein Codeelement in eine andere Ebene zugeordnet zugeordnet, aber es keine Abhängigkeitspfeil zwischen diesen Schichten in der abhängigkeitsvalidierungsdiagramm gibt, die diese Ebenen enthält. Dies ist eine einschränkungsverletzung Abhängigkeit. |
| DV1001: **Ungültiger Namespacename** | Dieses Problem wird gemeldet, auf ein Codeelement zugeordnete eine Ebene der "Darf der Namespace-Namen"-Eigenschaft nicht den Namespace enthält, in dem dieses Codeelement definiert ist. Dies ist eine Einschränkung namensverletzung. Beachten Sie, dass die Syntax des "Darf der Namespace-Namen" eine durch Semikolons Liste von Namespaces, in denen Elemente, die zu Ebene sind, sein dürfen definiert werden. |
| DV1002: **Abhängigkeit von unreferenceable namespace** | Dieses Problem wird gemeldet, auf ein Codeelement einer Ebene zugeordnete und verweisen auf ein anderes Codeelement definiert, die in einem Namespace das in der Eigenschaft "Unreferenceable Namespace" die Ebene definiert wird. Dies ist eine Einschränkung namensverletzung. Beachten Sie, dass die Eigenschaft "Unreferenceable Namespaces" als eine durch Semikolons getrennte Liste der Namespaces definiert ist, die in dieser Ebene zugeordnete Codeelemente nicht verwiesen werden soll. |
| DV1003: **Unzulässige Namespacename** | Dieses Problem wird gemeldet, auf ein Codeelement zugeordnete eine Ebene die "Namespace-Namen nicht zulässig"-Eigenschaft den Namespace enthält, in dem dieses Codeelement definiert ist. Dies ist eine Einschränkung namensverletzung. Beachten Sie, dass die Eigenschaft "Nicht erlaubt-Namespace-Name" als eine durch Semikolons getrennte Liste der Namespaces definiert ist, in denen dieser Ebene zugeordneten Elemente nicht definiert werden soll. |
| DV3001: **Fehlender Link** | Ebene '*LayerName*"enthält links zu"*Artefakt*", der nicht gefunden werden. Möglicherweise fehlt ein Assemblyverweis. |
| DV9001: **Architektur Analyse interner Fehler gefunden** | Die Ergebnisse sind möglicherweise nicht vollständig. Weitere Informationen finden Sie im ausführlichen Buildereignisprotokoll oder im Ausgabefenster. |

## <a name="see-also"></a>Siehe auch

- [Live-abhängigkeitsüberprüfung in Visual Studio](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [Überprüfen des Systems während der Entwicklung](../modeling/validate-your-system-during-development.md)
- [Video: Überprüfen Sie Ihre architekturabhängigkeiten in Echtzeit](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
