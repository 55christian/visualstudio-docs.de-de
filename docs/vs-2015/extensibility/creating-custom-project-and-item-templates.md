---
title: Erstellen von benutzerdefinierten Projekt- und Elementvorlagen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197396"
---
# <a name="creating-custom-project-and-item-templates"></a>Erstellen von benutzerdefinierten Projekt- und Elementvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK umfasst Projektvorlagen, die eine benutzerdefinierte Projektvorlage und eine benutzerdefinierte Elementvorlage zu erstellen. Diese Vorlagen enthalten einige allgemeine Ersetzen von Parametern, und erstellen als Zip-Dateien. Sie werden nicht automatisch bereitgestellt, und sie sind nicht verfügbar, in der experimentellen Instanz. Kopieren Sie die ZIP-Datei auf den Speicherort Datei

Die Vorlage erstellen Vorlagen können Sie die Vorlagen in größeren Erweiterungen enthalten. Einschließlich der Vorlagen in Erweiterungen können Sie die Versionskontrolle für die Quelldateien implementieren, und erstellen eine Gruppe von Vorlagenprojekten in einem VSIX-Paket.

Für Szenarien für einfache Vorlage erstellen, sollten Sie verwenden die **Vorlage exportieren** -Assistenten, der in eine komprimierte Datei ausgibt. Weitere Informationen zum Erstellen von grundlegenden Vorlage finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

Ab Visual Studio 2017, Überprüfung von benutzerdefinierten Projekt- und Elementvorlagen wird nicht mehr ausgeführt. Stattdessen muss die Erweiterung vorlagenmanifestdateien bereitstellen, die den Installationsspeicherort der diese Vorlagen zu beschreiben. Sie können die Installation der Preview 2 verwenden, Ihre VSIX-Erweiterungen zu aktualisieren. Wenn Sie die Erweiterung, die mit MSI bereitstellen, müssen Sie die vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Das manifest Vorlagenschema finden Sie unter [Visual Studio-Manifest Schemareferenz zu Vorlagen](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Erstellen einer Projektvorlage

1. Erstellen Sie ein Projekt für die Projektvorlage aus. Finden Sie die Projektvorlage in das **neues Projekt** Dialogfeld in Visual Basic oder Visual C#- **Erweiterbarkeit** Ordner.

     Die Vorlage generiert eine Klassendatei, ein Symbol, eine VSTEMPLATE-Datei, einer bearbeitbaren Projektdatei mit dem Namen ProjectTemplate.vbproj oder ProjectTemplate.csproj und einige Dateien, die in der Regel von anderen Projekttypen, eine solche "Resources.resx" Datei, ein "AssemblyInfo" generiert werden Datei und eine Einstellungsdatei. Jede Codedatei enthält allgemeine Ersetzen von Parametern an, falls zutreffend.

2. Hinzufügen und Entfernen von Elementen aus dem Projekt als für Ihr Projekt erforderlich. Entfernen Sie die Datei bearbeitet werden, der AssemblyInfo-Datei oder der VSTEMPLATE-Datei nicht.

3. Aktualisieren Sie die VSTEMPLATE-Datei entsprechend alle Hinzufügungen und löschungen. Die [Projekt](../extensibility/project-element-visual-studio-templates.md) -Element muss enthalten eine [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei, die in der Vorlage enthalten sein.

4. Ändern Sie Ihre Codedateien und anderem benutzerseitigen Inhalt, und fügen Sie entsprechende parameterersetzungen.

5. Ändern Sie den generierten Inhalt nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine ZIP-Datei, die Ihre Vorlage enthält. Es wird nicht bereitgestellt, und es ist nicht verfügbar, in der experimentellen Instanz.

## <a name="create-an-item-template"></a>Erstellen Sie eine Elementvorlage

1. Erstellen Sie eine Elementvorlage-Projekt.

     Die Vorlage generiert eine Klassendatei, ein Symbol, eine VSTEMPLATE-Datei und ein AssemblyInfo-Datei. Die Klassendatei enthält einige allgemeine Ersetzen von Parametern.

2. Hinzufügen und Entfernen von Elementen aus dem Projekt als für Ihr Projekt erforderlich.

3. Aktualisieren Sie die VSTEMPLATE-Datei entsprechend alle Hinzufügungen und löschungen. Die [Projekt](../extensibility/project-element-visual-studio-templates.md) -Element muss enthalten eine [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei, die in der Vorlage enthalten sein.

4. Ändern Sie Ihre Codedateien und anderem benutzerseitigen Inhalt, und fügen Sie entsprechende parameterersetzungen.

5. Generierten Inhalt nach Bedarf zu ändern.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine komprimierte Datei, die Ihre Vorlage enthält. Es wird nicht bereitgestellt, und es ist nicht verfügbar, in der experimentellen Instanz.

## <a name="deploy-the-project-or-item-template"></a>Bereitstellen der Vorlage für Projekt oder Element

1. Erstellen eines VSIX-Projekts Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

2. Festlegen Sie das VSIX-Projekt als Startprojekt. In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projektknoten, mit der rechten Maustaste und wählen Sie **als Startprojekt festlegen**.

3. Legen Sie das Projektvorlagenprojekt als Medienobjekt des VSIX-Projekts. Öffnen Sie die vsixmanifest-Datei. Wechseln Sie zu der **Assets** Registerkarte, und klicken Sie auf **neu**.

    1. Legen Sie die **Typ** Feld **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate**.

    2. Wählen Sie für Quelle und das **ein Projekt in der aktuellen Projektmappe** aus, und wählen Sie dann auf das Projekt, das die Vorlage enthält.

4. Erstellen Sie die Projektmappe, und drücken Sie F5. Die experimentelle Instanz angezeigt wird.

5. Für ein Projektvorlagenprojekt, sollte Ihre Projektvorlage aufgeführt, die der **neues Projekt** Dialogfeld (**Datei / neu / Projekt**) in den Visual c# oder Visual Basic-Knoten. Für ein Elementvorlagenprojekt, sollte die Elementvorlage, die in das Dialogfeld "Neues Element hinzufügen" aufgeführt (in der **Projektmappen-Explorer**, wählen Sie den Projektknoten, und klicken Sie auf **hinzufügen / neues Element**).

## <a name="see-also"></a>Siehe auch

- [Referenz zu Visual Studio-Vorlagen](../ide/visual-studio-template-reference.md)