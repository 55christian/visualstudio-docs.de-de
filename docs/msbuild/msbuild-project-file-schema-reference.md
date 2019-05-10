---
title: Referenz zum MSBuild-Projektdateischema | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c49c2198a4ecc40a40e3f5f6414bfd4af47279b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842291"
---
# <a name="msbuild-project-file-schema-reference"></a>Referenz zum MSBuild-Projektdateischema
Enthält eine Tabelle mit allen XML-Schemaelementen von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sowie ihren verfügbaren Attributen und untergeordneten Elementen.

 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] verwendet Projektdateien, um der Build-Engine anzuzeigen, was wie erstellt werden soll. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdateien sind XML-Dateien, für die das [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-XML-Schema gilt. Dieser Abschnitt beschreibt die XML-Schemadefinitionsdatei (*XSD*) für [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

## <a name="msbuild-xml-schema-elements"></a>XML-Schemaelemente von MSBuild
 Die folgende Tabelle enthält alle XML-Schemaelemente von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sowie die untergeordneten Elemente und Attribute.

|Element|Untergeordnete Elemente|Attribute|
|-------------|--------------------|----------------|
|[Choose-Element (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|
|[Import-Element (MSBuild)](../msbuild/import-element-msbuild.md)|--|Bedingung<br /><br /> Projekt|
|[ImportGroup-Element](../msbuild/importgroup-element.md)|Importieren|Bedingung|
|[Item-Element (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Bedingung<br /><br /> Ausschließen<br /><br /> Einschließen<br /><br /> Remove|
|[ItemDefinitionGroup-Element (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Bedingung|
|[ItemGroup-Element (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Bedingung|
|[ItemMetadata-Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Bedingung|
|[OnError-Element (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Bedingung<br /><br /> ExecuteTargets|
|[Otherwise-Element (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|
|[Output-Element (MSBuild)](../msbuild/output-element-msbuild.md)|--|Bedingung<br /><br /> ItemName<br /><br /> PropertyName<br /><br /> TaskParameter|
|[Parameter-Element](../msbuild/parameter-element.md)|--|Output<br /><br /> ParameterType<br /><br /> Erforderlich|
|[ParameterGroup-Element](../msbuild/parametergroup-element.md)|*Parameter*|--|
|[Project-Element (MSBuild)](../msbuild/project-element-msbuild.md)|Choose<br /><br /> Importieren<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Ziel<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|
|[ProjectExtensions-Element (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|
|[Property-Element (MSBuild)](../msbuild/property-element-msbuild.md)|--|Bedingung|
|[PropertyGroup-Element (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Property*|Bedingung|
|[SDK-Element (MSBuild)](../msbuild/sdk-element-msbuild.md)|--|name<br /><br /> Version|
|[Target-Element (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Task*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Bedingung<br /><br /> DependsOnTargets<br /><br /> Eingaben<br /><br /> KeepDuplicateOutputs<br /><br /> name<br /><br /> Ausgaben<br /><br /> Rückgabe|
|[Task-Element (MSBuild)](../msbuild/task-element-msbuild.md)|Output|Bedingung<br /><br /> ContinueOnError<br /><br /> *Parameter*|
|[TaskBody-Element (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Auswerten|
|[UsingTask-Element (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Bedingung<br /><br /> TaskFactory<br /><br /> TaskName|
|[When-Element (MSBuild)](../msbuild/when-element-msbuild.md)|Choose<br /><br /> ItemGroup<br /><br /> PropertyGroup|Bedingung|

## <a name="see-also"></a>Siehe auch
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
- [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen)
- [MSBuild-Referenz](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
