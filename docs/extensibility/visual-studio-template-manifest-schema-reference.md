---
title: Visual Studio-Vorlage Manifest Schemareferenz | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b447225580505959697e14f0c85855452906aa18
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108853"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio-Vorlage manifest Schemareferenz
Dieses Schema beschreibt das Format des Manifests Visual Studio-Vorlage (*vstman*) Dateien, die generiert werden, die für Visual Studio Projekt- oder Elementvorlagen. Das Schema beschreibt auch den Speicherort und andere relevante Informationen zur Vorlage.

 : Da separate Element und den Projektverzeichnissen-Vorlage vorhanden sind, müssen ein Manifest noch nie eine Kombination von Element- und Projektvorlagen.

> [!IMPORTANT]
>  Dieses Manifest ist ab Visual Studio 2017 verfügbar.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest-element
 Das Stammelement des Manifests.

### <a name="attributes"></a>Attribute

- **Version**: Eine Zeichenfolge, die die Version des Manifests Vorlage darstellt. Erforderlich.

- **Locale**: Eine Zeichenfolge, die dem Gebietsschema oder Gebietsschemas des Manifests Vorlage darstellt. Die Gebietsschemawert gilt für alle Vorlagen. Sie müssen ein eigenes Manifest für jedes Gebietsschema verwenden. Dies ist optional.

### <a name="child-elements"></a>Untergeordnete Elemente

- **VSTemplateContainer** Optional.

- **VSTemplateDir** Optional.

### <a name="parent-element"></a>Übergeordnetes Element
 Keine

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Der Container der Vorlage manifest Elemente. Ein Manifest verfügt über eine Vorlagencontainers für jede Vorlage, die sie definiert.

### <a name="attributes"></a>Attribute
 **VSTemplateType**: Ein Zeichenfolgenwert, der angibt, den Typ der Vorlage (`"Project"`, `"Item"`, oder `"ProjectGroup"`). Erforderlich

### <a name="child-elements"></a>Untergeordnete Elemente

- **RelativePathOnDisk**:  Der relative Pfad der Vorlagendatei auf dem Datenträger. Hier definiert die Platzierung der Vorlage auch in der Struktur der Vorlage angezeigt, der **neues Projekt** oder **neues Element** Dialogfeld. Für Vorlagen, die als ein Verzeichnis und die einzelnen Dateien bereitgestellt werden bezieht sich dieser Pfad zu dem Verzeichnis, das die Vorlagendateien enthält. Vorlagen als "bereitgestellt" eine *ZIP* -Datei in diesen Pfad muss der Pfad zu der *ZIP* Datei.

- **VSTemplateHeader: Ein [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) Element, das den Header beschreibt.

### <a name="parent-element"></a>Übergeordnetes Element
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Beschreibt das Verzeichnis, in dem die Vorlage befindet. Ein Manifest kann mehrere enthalten **VSTemplateDir** Einträgen zum Bereitstellen von lokalisierten und die Sortierreihenfolge für Verzeichnisse Reihenfolge ihrer Darstellung in der Struktur der Vorlage Kategorie-steuern.

 Aufgrund ihrer Konstruktion **VSTemplateDir** Einträge sollten nur in der angegebenen Manifeste nicht um ein Gebietsschema angezeigt werden.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

- **RelativePath**: Der Pfad der Vorlage. Es können nur einen Eintrag pro Pfad vorhanden sein, damit die erste Bedingung für alle Manifeste gewinnen wird.

- **LocalizedName**: Ein **NameDescriptionIcon** Element, das den lokalisierten Namen angibt. Dies ist optional.

- **SortOrder**: Eine Zeichenfolge, die Sortierreihenfolge angibt. Dies ist optional.

- **ParentFolderOverrideName**: Die außer Kraft gesetzten Namen des übergeordneten Ordners. Dies ist optional. Dieses Element verfügt über eine **Namen** Attribut, das einen Zeichenfolgenwert, der den Namen angibt.

### <a name="parent-element"></a>Übergeordnetes Element
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Gibt den Namen und Beschreibung, die möglicherweise für lokalisierte Vorlagen. Finden Sie unter **LocalizedName** oben.

### <a name="attributes"></a>Attribute

- **Paket**: Ein Zeichenfolgenwert, der angibt, das Paket. Dies ist optional.

- **ID**: Ein Zeichenfolgenwert, der angibt, die-ID. Dies ist optional.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-element"></a>Übergeordnetes Element
 **LocalizedName**

## <a name="examples"></a>Beispiele
 Der folgende Code ist ein Beispiel für eine Projektvorlage *vstman* Datei.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Der folgende Code ist ein Beispiel für eine Elementvorlage *vstman* Datei.

```xml
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```