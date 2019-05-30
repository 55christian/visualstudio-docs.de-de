---
title: In der Kern-Editor | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d400e8b122ae43424bea55c7a1d6f4bc21708707
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344329"
---
# <a name="inside-the-core-editor"></a>In der Kern-editor
Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Kern-Editor ist ein Satz von mehreren Komponenten, mit denen Sie ändern und Abfragen von Textinformationen. Wenn Sie die Kern-Editor mit der legacy-API angepasst haben, können Sie weiterhin diesen Anpassungen verwenden, die über den Editor für Adapter weitergeleitet werden. Es wird jedoch empfohlen, dass Sie Ihre Anpassungen an den neuen Editor API anpassen.

 Die folgenden Bereiche sind einige wichtige Aspekte bei der die Kern-Editor:

- Textpuffer

- Textansicht

- Codefenster

- Textmarkierungen

- Text-manager

- Integration mit Sprachdienste

## <a name="in-this-section"></a>In diesem Abschnitt
- [Instanziieren Sie die Kern-Editor, indem Sie die legacy-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md) enthält schrittweise Anleitungen zur Verwendung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> So erstellen eine Instanz von der Kern-Editor.

- [Zugriff auf den Textpuffer mithilfe der legacy-API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md) erläutert den Textpuffer-Rolle in der Kern-Editor, wird erläutert, die zugehörigen Systeme, die werden verwendet, um Zugriff auf den Puffer und enthält eine Liste der von den TextBuffer-Objekt, implementierten Schnittstellen <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.

- [Text-Puffer-Ereignisse in der legacy-API](../extensibility/text-buffer-events-in-the-legacy-api.md) enthält eine Liste der Schnittstellen, die für die Benachrichtigung über Ereignisse für Text-Puffer verwendet werden.

- [Vorgehensweise: Registrieren Sie sich für Text-Puffer-Ereignisse mit der legacy-API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md) wird beschrieben, wie Text Puffern von Ereignissen zu empfehlen.

- [Verwenden Sie den TextManager zum Überwachen von globaler Einstellungen](../extensibility/using-the-text-manager-to-monitor-global-settings.md) wird erläutert, wie TextManager verwendet wird, für die Editor-Kernkomponenten globale Einstellung Informationen freigeben und Empfangen von Benachrichtigungen über Text-Manager-Ereignisse.

- [TheText-Ansicht mit der legacy-API Aufrufen](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) wird die Textansicht-Rolle in der Kern-Editor, und listet die von implementierten Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.

- [Anpassen von Fenstern des Code mit der legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md) enthält Informationen wie ein Code-Fenster wird verwendet, um die Textansicht zu schließen, wird erläutert, wie der Codefenster-Manager verwendet ist, Ergänzungen zum Code-Fenster zu und ermöglicht die Benachrichtigung über neue Ansichten .

- [Ändern Sie Anzeigeeinstellungen, indem Sie mithilfe der legacy-API](../extensibility/changing-view-settings-by-using-the-legacy-api.md) enthält detaillierte Anweisungen zum Erzwingen der Einstellungen und erzwungene Einstellungen zu entfernen.

- [Sprachdienste und dem kerneditor](../extensibility/language-services-and-the-core-editor.md) beschreibt die Instanziierung von einem Sprachdienst, Ergänzungen der Steuerelement-Code.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Exemplarische Vorgehensweise: Erstellen Sie einen Kern-Editor, und registrieren Sie einen Dateityp-Editor-](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md) enthält detaillierte Anweisungen zum Starten der Kern-Editor von verwaltetem Code.

- [Dropdownleiste](../extensibility/drop-down-bar.md) erläutert, wie die Dropdownleiste im Codefenster verwendet wird, und beschreibt die Schnittstellen, die verwendet werden, wenn Sie eine Dropdownleiste implementieren.

- [Verwenden von Textmarkierungen mit der legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md) erklärt das Konzept von Textmarkierungen und wie sie in der Kern-Editor verwendet werden, und listet die Schnittstellen, die zum Zugreifen auf und Verwalten von Textmarkierungen verwendet werden.

- [Vorgehensweise: Hinzufügen von standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md) enthält schrittweise Anleitungen zum Erstellen ein textmarkers und So fügen Sie einen benutzerdefinierten Befehl in einem Kontextmenü Menüelemente hinzu.

- [Vorgehensweise: Erstellen von benutzerdefinierten Textmarkierungen](../extensibility/how-to-create-custom-text-markers.md) enthält detaillierte Anweisungen zum Erstellen ein benutzerdefinierten textmarkers und den Typ des Markers als Dienst bereitstellen.