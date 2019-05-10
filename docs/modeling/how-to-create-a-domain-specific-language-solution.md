---
title: 'Vorgehensweise: Erstellen einer domänenspezifischen Sprachlösung'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ac8a47aeca8875dabe3fdf388e9a73d68ec514e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445209"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Vorgehensweise: Erstellen einer domänenspezifischen Sprachlösung
Eine domänenspezifische Sprache (DSL) wird mit speziellen Visual Studio-Projektmappe erstellt.

## <a name="prerequisites"></a>Vorraussetzungen

Bevor Sie dieses Verfahren starten können, werden installieren Sie diese Komponenten:

- Visual Studio
- Visual Studio SDK (als Teil der **Visual Studio-extensionentwicklung** arbeitsauslastung)
- Modellierungs-SDK (als Visual Studio-Komponente installiert)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>Erstellen einer Lösung einer domänenspezifischen Sprache

1. Die DSL-Assistenten starten, indem Sie beim Erstellen eines neuen **domänenspezifischen Sprachdesigner** Projekt.

   > [!NOTE]
   > Idealerweise sollte der Name, den Sie für das Projekt auswählen ein gültiger Visual C# Bezeichner, weil sie zum Generieren von Code verwendet werden kann.

   ::: moniker range="vs-2017"

   ![Dialogfeld "DSL erstellen"](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. Wählen Sie eine DSL-Vorlage.

    Auf der **domänenspezifische Sprachoptionen auswählen** Seite, wählen Sie eine der Lösungsvorlagen wie z. B. **minimale Sprache**. Wählen Sie eine Vorlage, die die DSL ähnelt, die Sie erstellen möchten.

    Weitere Informationen zu Vorlagen finden Sie unter [Auswählen einer Lösungsvorlage für Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Geben Sie eine Dateinamenerweiterung auf die **Dateierweiterung** Seite. Es muss auf dem Computer eindeutig sein und in jeder Computer, auf denen Sie die DSL installieren möchten. Daraufhin sollte die Nachricht **keine Anwendungen oder Visual Studio-Editoren mithilfe dieser Erweiterung**.

   - Wenn Sie die Dateinamenerweiterung in vorherigen experimentelle DSLs verwendet haben, die nicht vollständig installiert wurden, Sie können diese out durch Löschen mit der **Zurücksetzen der experimentellen Instanz** -Tool, das in das Menü "Visual Studio SDK" gefunden werden kann.

   - Wenn eine andere Visual Studio-Erweiterung, die diese Dateierweiterung verwendet vollständig auf dem Computer installiert wurde, sollten Sie es deinstallieren. Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.

4. Überprüfen Sie und bei Bedarf passen Sie an, die Felder in den verbleibenden Seiten des Assistenten. Wenn Sie mit den Einstellungen zufrieden sind, klicken Sie auf **Fertig stellen**. Weitere Informationen zu den Einstellungen finden Sie unter [DSL-Designer-Assistentenseiten](#settings).

    Der Assistent erstellt eine Projektmappe mit zwei Projekten, die benannt werden **Dsl** und **DslPackage**.

   > [!NOTE]
   > Wenn Sie eine Meldung, die Sie benachrichtigt werden, nicht zum Ausführen von Textvorlagen aus nicht vertrauenswürdigen Quellen auf **OK**. Sie können diese Meldung nicht wieder angezeigt werden, festlegen.

## <a name="settings"></a> Die DSL-Designer-Assistent-Seiten
 Sie können einige Felder die Standardwerte unverändert lassen. Allerdings stellen Sie sicher, dass Sie das Feld für die Erweiterung festlegen.

### <a name="solution-settings-page"></a>Seite "Lösung-Einstellungen"
 **Welcher Vorlage soll auf Ihrer domänenspezifischen Sprache basieren?**
Wählen Sie eine Vorlage, die die DSL ähnelt, die Sie erstellen möchten. Die anderen Vorlagen bieten praktische Ausgangspunkte. Wenn Sie eine Vorlage auswählen, zeigt der Assistent eine Beschreibung an. Weitere Informationen zu Vorlagen finden Sie unter [Auswählen einer Lösungsvorlage für Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Was möchten Sie zum Benennen Ihrer domänenspezifischen Sprache?**
Der Standardwert ist der Projektmappenname. Von diesem Wert wird Code generiert. Es muss als C#-Klassenname gültig sein.

### <a name="file-extension-page"></a>Seite "Dateierweiterung"-Datei
 **Welche Erweiterung sollen Modelldateien verwenden?**
Geben Sie eine neue Dateierweiterung ein.

 Stellen Sie sicher, dass diese Erweiterung nicht bereits für die Verwendung in diesem Computer wie folgt registriert wurde:

 Suchen Sie unter **anderen Tools und Anwendungen registriert werden, um diese Erweiterung behandeln**. Wenn die Meldung **keine Anwendungen oder Visual Studio-Editoren mithilfe dieser Erweiterung**, können Sie diese Erweiterung verwenden.

 Wenn Sie eine Liste der Tools oder Pakete angezeigt wird, sollten Sie eine der folgenden tun:

- Geben Sie eine andere Dateinamenerweiterung.

     \- oder –

- Zurücksetzen der experimentellen Instanz von Visual Studio. Dadurch werden alle der DSLs Aufheben der Registrierung, die Sie zuvor erstellt haben. Auf der **starten** Menü klicken Sie auf **Programme**, **Microsoft Visual Studio 2010 SDK**, **Tools**, und klicken Sie dann **Zurücksetzen der Microsoft Visual Studio 2010 experimentelle Instanz**. Sie können eine beliebige andere DSLs neu erstellen, die Sie erneut verwenden möchten.

     \- oder –

- Wenn Sie eine Visual Studio-Erweiterung, die diese Dateierweiterung verwendet vollständig auf dem Computer installiert wurde, deinstallieren Sie es aus. Auf der **Tools** Menü klicken Sie auf **Erweiterungs-Manager**.

### <a name="product-settings-page"></a>Settings-Produktseite
 **Was ist der Name des Produkts, das die neue domänenspezifische Sprache gehört?**
Der Standardwert ist der Name der DSL.

 Dieser Wert wird verwendet, in Windows Explorer (oder Datei-Explorer), um Dateien zu beschreiben, die dieser Dateierweiterung.

 **Was ist der Name des Unternehmens, das das Produkt gehört?**
Den Namen Ihres Unternehmens.

 Dieser Wert wird in die AssemblyInfo-Eigenschaften der Ihr DSL-Paket integriert.

 **Was ist der Stammnamespace für Projekte in dieser Lösung?**
Dies ist standardmäßig auf einen Namen, die von Ihrem Unternehmen besteht und aus Produktnamen besteht.

### <a name="signing-page"></a>Seite "Signierung"
 **Erstellen Sie eine Schlüsseldatei mit starkem Namen** die Standardoption ist, um einen neuen Schlüssel zum Signieren Ihrer DSL-Assembly zu erstellen.

 **Verwenden Sie die vorhandenen Schlüssel mit starkem Namen** verwenden Sie diese Option aus, wenn Sie Ihre DSL in einer anderen Assembly integrieren möchten.

 Weitere Informationen zu starken Namen finden Sie unter [erstellen und Assemblys mit starkem Namen](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Siehe auch

- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
