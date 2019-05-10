---
title: Code Maps sind langsam.
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12ba03ab97da3295a93b54dfc012d10fc012fd30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423926"
---
# <a name="improve-performance-for-code-maps"></a>Verbessern der Leistung für Code maps

Wenn Sie eine Code Map zum ersten Mal generieren, werden von Visual Studio alle gefundenen Abhängigkeiten indiziert. Dieser Vorgang kann einige Zeit dauern, insbesondere bei großen Projektmappen, aber die höhere Leistung verbessert. Wenn Ihr Code geändert wird, wird von Visual Studio nur der aktualisierte Code neu indiziert. Um den Zeitaufwand für die Karte, um das Rendern zu minimieren, sollten Sie die folgenden Vorschläge aus:

- Stellen Sie nur die Abhängigkeiten in der Code Map dar, die Sie interessieren.

- Bevor Sie die Code Map für eine gesamte Projektmappe generieren, reduzieren Sie den Umfang der Projektmappe.

- Deaktivieren der automatischen Erstellung der Projektmappe durch Auswahl **Skip Build** auf der Symbolleiste der Codeübersicht.

- Deaktivieren Sie Automatisches Hinzufügen von übergeordneten Elementen dazu **übergeordnete Elemente einschließen** auf der Symbolleiste der Codeübersicht.

   ![Schaltflächen "Build überspringen" und "Übergeordnete Elemente einschließen"](../modeling/media/codemapsfilterskipbuildicons.png)

- Bearbeiten Sie die Code Map direkt, um Knoten und Links zu entfernen, die Sie nicht benötigen. Das Ändern der Code Map wirkt sich nicht auf den zugrunde liegenden Code aus. Siehe [Anpassen von Code Maps durch Bearbeiten der DGML-Dateien](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Möglicherweise dauert länger Maps zu erstellen oder Hinzufügen von Elementen zu einer Zuordnung von **Projektmappen-Explorer** beim eines Projektelements **in Ausgabeverzeichnis kopieren** -Eigenschaftensatz auf **immer kopieren**. Ändern Sie diese Eigenschaft in **Kopieren, wenn neuer** oder `PreserveNewest`, um die Leistung zu erhöhen. Finden Sie unter [inkrementelle Builds](../msbuild/incremental-builds.md).

Die fertige Zuordnung zeigt die Abhängigkeiten nur für erfolgreich erstellte Code. Wenn für bestimmte Komponenten Buildfehler auftreten, werden diese Fehler auf der Code Map angezeigt. Vergewissern Sie sich, dass eine Komponente tatsächlich erstellt wird und über Abhängigkeiten verfügt, bevor Sie auf Grundlage der Code Map architekturbezogene Entscheidungen treffen.