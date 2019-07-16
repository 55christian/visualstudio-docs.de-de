---
title: WizardExtension-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cde4c98b1b8ba51205cb2d198eacaaf468a7e872
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350783"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension-Element (Visual Studio-Vorlagen)
Enthält die Registrierungselemente für die Anpassung von des Vorlagen-Assistenten.

 \<VSTemplate >... \<WizardExtension>

## <a name="syntax"></a>Syntax

```
<WizardExtension>
    <Assembly>... </Assembly>
    <FullClassName>... </FullClassName>
</WizardExtension>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Erforderliches Element.<br /><br /> Gibt den Namen oder den starken Namen einer Assembly, die im globalen Assemblycache angezeigt. Es muss mindestens eine `Assembly` Element in einem `WizardExtension` Element.|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Erforderliches Element.<br /><br /> Der vollqualifizierte Name der Klasse, die implementiert die `IWizard` Schnittstelle. Es muss mindestens eine `FullClassName` Element in einem `WizardExtension` Element.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Enthält alle Metadaten für die Projektvorlage, Item-Vorlage oder Starterkits.|

## <a name="remarks"></a>Hinweise
 `WizardExtension` ist ein optionales untergeordnetes Element von `VSTemplate`.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Metadaten für die standard-Projektvorlage für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows-Anwendung.

```
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)