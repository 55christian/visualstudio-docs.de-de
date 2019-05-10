---
title: FeatureProperty-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20d24192d8613a4f41d9cdfc04371fb9c9d02076
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967304"
---
# <a name="featureproperty-element"></a>FeatureProperty-Element
  Stellt eine benutzerdefinierte Eigenschaft, die mit einer Funktion enthalten ist, wenn sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wird, können Sie die Eigenschaft in Ihrem Code zugreifen.

## <a name="syntax"></a>Syntax

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|**Key**|Erforderliche **xs: String** Attribut.<br /><br /> Der Schlüssel, der zum Speichern und Abrufen von den Wert der Eigenschaft verwendet wird. Jede Eigenschaft muss es sich um einen Schlüssel verfügen, der innerhalb der Funktion eindeutig ist.|
|**Wert**|Erforderliche **xs: String** Attribut.<br /><br /> Der Eigenschaftswert.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschaftswerten, die mit einer Funktion enthalten sind, wenn sie in SharePoint bereitgestellt wird.|

## <a name="remarks"></a>Hinweise
 Weitere Informationen zu Feature-Eigenschaften finden Sie unter [darauf einzugehen Paket und die Bereitstellung in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

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
