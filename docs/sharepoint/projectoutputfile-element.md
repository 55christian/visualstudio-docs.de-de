---
title: ProjectOutputFile-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2673b22bf502f019f0a10361c9d0cef9d5ac1b8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816836"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile-Element
  Zeigt die Ausgabe von einem separaten Projekt mit dem Projektelement eingeschlossen werden soll, wenn sie in SharePoint bereitgestellt wird.

## <a name="syntax"></a>Syntax

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Typ
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|**ProjectId**|Erforderliche **xs: String** Attribut.<br /><br /> Die GUID des abhängigen Projekts, das die Ausgabe enthält, die Sie einschließen möchten. Dies entspricht der **ProjectGuid** Element in der abhängige-Projektdatei.|
|**ProjectPath**|Erforderliche **xs: String** Attribut.<br /><br /> Der relative Pfad, einschließlich der Projektdateiname, des abhängigen Projekts, das die Ausgabe enthält, die Sie einschließen möchten. Dieser Pfad ist relativ zum Stammordner des SharePoint-Projekts, das die SharePoint-Projektelement enthält.|
|**Target**|Optionale **xs: String** Attribut.<br /><br /> Der Pfad, in dem die Ausgabe des abhängigen Projekts ist, auf dem SharePoint-Server, relativ zum Stammordner Bereitstellung bereitgestellt werden. Bereitstellungsstammordner richtet sich nach der Bereitstellungstyp anhand der **Typ** Attribut.<br /><br /> Weitere Informationen finden Sie in den Beschreibungen der **Bereitstellungspfad** und **Deployment Root** Eigenschaften von SharePoint-Projektelemente in [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Erforderliche **xs: String** Attribut.<br /><br /> Die Art der Bereitstellung, die für die Ausgabe des abhängigen Projekts verwendet werden soll. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung für die **Bereitstellungstyp** Eigenschaft des SharePoint-Projektelemente in [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien mit SharePoint-Projektelements eingeschlossen werden soll, wenn sie in SharePoint bereitgestellt wird.|

## <a name="remarks"></a>Hinweise
 Verwenden der **ProjectOutputFile** Element, um die Ausgabe eines Projekts in der Bereitstellung von SharePoint-Projektelements einzuschließen. Sie können angeben, ein anderes Projekt oder die gleichen Projekt, das das Projektelement enthält. Weitere Informationen finden Sie unter [Angaben zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Elementinformationen

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Name des Schemas**|SharePoint-Projektelementschema|
|**Validierungsdatei**|ProjectItemModelSchema.xsd|
|**Kann leer sein.**|Nein|

## <a name="see-also"></a>Siehe auch
- [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Angaben Sie zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
