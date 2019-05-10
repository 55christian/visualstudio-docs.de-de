---
title: Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f03b23076b1eea203166bb0322f05927480a278
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417170"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>Abrufen von Informationen von Schriftart- und farbanbieters für die farbliche Kennzeichnung von text
Der Prozess, der gerendert wird, oder zeigt farbige Text in die Elemente der Benutzeroberfläche (UI) hängt von den Typ des Projekts, die Technologie und Developer-Einstellungen. Die **Schriftarten und Farben** auf der Seite werden die Einstellungen gespeichert.

 Die meisten Implementierungen, die farbige Text anzeigen müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> und die zugehörigen Schnittstellen, für die darstellen, abgerufen und das Speichern von Text Einstellungen anzuzeigen.

> [!NOTE]
> Beim Anpassen der Kern-Editor (welche unterstützt die **Text EditorCategory**), es wird empfohlen, die Farbgebung-Technologie in den Sprachdienst zu verwenden. Weitere Informationen finden Sie unter [Übersicht über die Schriftart- und farbeinstellungen](../extensibility/font-and-color-overview.md).

## <a name="get-default-font-and-color-information"></a>Schriftart und Farbe Standardinformationen zu erhalten
 Alle der **Schriftarten und Farben** Einstellungen von einem beliebigen Fenster, das Anzeigen von Text sollte angegeben werden, der **Anzeigeelemente** eines **Kategorie**. Weitere Informationen finden Sie unter [Schriftarten und Farben, Umgebung, Dialogfeld "Optionen" im Feld](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Eine VSPackage benötigen zum farbigen Anzeigen von, aktuelle **Schriftarten und Farben** Einstellungen. Eine VSPackage kann die aktuelle Einstellungen in der folgenden Methoden, nach Bedarf abrufen:

- Verwenden Sie den Schriftart- und farbeinstellungen Dauerhaftigkeitsmechanismus zum Abrufen des gespeicherten oder der aktuellen Status. Weitere Informationen finden Sie unter [gespeicherte Schriftart-und farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md).

- Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> ein Dienst, bietet Schriftart und Farbe Daten rufen Sie eine Instanz der, Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, wenn das VSPackage auch nicht den Schriftart- und farbeinstellungen-Anbieter ist.

- Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>-Schnittstelle.

Um sicherzustellen, dass die Ergebnisse der Abfrage werden auf dem neuesten Stand, es kann hilfreich sein, verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Schnittstelle, um zu bestimmen, ob ein Update erforderlich ist, vor dem Aufrufen der Abrufmethoden, der die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Schnittstelle.

Nachdem Sie Schriftart und Farbinformationen abgerufen haben, analysiert des Texts, der angezeigt werden, um Elemente zu identifizieren, für die farbliche Kennzeichnung erforderlich. Zeigen Sie den Text im Fenster mit der entsprechenden Schriftarten und Farben.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Verwenden von Schriftarten und text](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Arbeiten mit Farben](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (Graphics Device Interface)](https://msdn.microsoft.com/library/7e1d4540-bb2e-4257-8eee-eee376acba83)