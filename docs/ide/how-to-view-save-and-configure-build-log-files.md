---
title: 'Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e40f414b3b3ea6bc151ef036deb0b5d80464ba46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62429144"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Vorgehensweise: Anzeigen, Speichern und Konfigurieren von Buildprotokolldateien

Nachdem Sie ein Projekt in der Visual Studio-IDE erstellt haben, werden Informationen zu diesem Build im Fenster **Ausgabe** angezeigt. Anhand dieser Informationen können Sie beispielsweise einen Buildfehler beheben. 

- Bei C++-Projekten werden die gleichen Informationen auch in einer *TXT*-Datei angezeigt, die automatisch erstellt und gespeichert wird. 

- Bei Projekten mit verwaltetem Code können Sie in das Buildausgabefenster klicken und **STRG**+**S** drücken. Visual Studio fordert Sie auf, einen Speicherort auszuwählen, an dem die Informationen aus dem **Ausgabefenster** in einer *.txt*-Datei gespeichert werden sollen. 

Sie können die IDE ebenfalls verwenden, um anzugeben, welche Informationen zu jedem Build angezeigt werden sollen.

Wenn Sie ein Projekt mithilfe von MSBuild erstellen, können Sie eine *TXT*-Datei erstellen, um Informationen zum Build zu speichern. Weitere Informationen finden Sie unter [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Anzeigen der Buildprotokolldatei für ein C++-Projekt

1. Öffnen Sie im **Windows-Explorer** oder im **Datei-Explorer** folgende Datei: *\\...\Visual Studio \<Version\>\Projects\\<ProjectName\>\\<ProjectName\>\Debug\\<ProjectName\>.txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Erstellen einer Buildprotokolldatei für ein Projekt mit verwaltetem Code

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

2. Klicken Sie im **Ausgabefenster** auf eine beliebige Stelle im Text.

3. Drücken Sie **STRG**+**S**.

   Visual Studio fordert Sie auf, einen Speicherort auszuwählen, an dem die Buildausgabe gespeichert werden soll.

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Ändern der Informationsmenge im Buildprotokoll

1. Wählen Sie in der Menüleiste **Extras** > **Optionen** aus.

2. Klicken Sie auf der Seite **Projekte und Projektmappen** auf **Erstellen und Ausführen**.

3. Wählen Sie einen der folgenden Werte aus der Liste **Ausführlichkeit der MSBuild-Projektbuildausgabe** aus, und klicken Sie dann auf die Schaltfläche **OK**.

    |Ausführlichkeitsgrad|Beschreibung|
    | - |-----------------|
    |**Still**|Zeigt ausschließlich eine Zusammenfassung des Builds an.|
    |**Minimal**|Zeigt eine Zusammenfassung des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden.|
    |**Normal**|Zeigt eine Zusammenfassung des Builds, die wichtigsten Schritte des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden. Diese Detailebene verwenden Sie am häufigsten.|
    |**Detailliert**|Zeigt eine Zusammenfassung des Builds, alle Schritte des Builds sowie Fehler, Warnungen und Meldungen an, die als äußerst wichtig eingestuft werden. Außerdem werden Meldungen von normaler Wichtigkeit angezeigt.|
    |**Diagnose**|Zeigt alle Daten an, die für den Build verfügbar sind. Sie können diese Detailebene für das Debuggen von Fehlern bei benutzerdefinierten Buildskripts und anderen Buildfehlern verwenden.|

     Weitere Informationen finden Sie unter [Optionen (Dialogfeld), Projekte und Projektmappen, Erstellen und Ausführen](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) und <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Sie müssen das Projekt neu erstellen, damit Ihre Änderungen im Fenster **Ausgabe** (alle Projekte) und in der Datei *\<Projektname>.txt* (nur C++-Projekte) wirksam werden.

## <a name="see-also"></a>Siehe auch

- [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)
