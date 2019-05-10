---
title: '&lt;Dokument&gt; -Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000029"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Dokument&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `document` Element der `vstov4` Namespace werden anpassungsspezifische Informationen für Anpassungen auf Dokumentebene gespeichert.

## <a name="syntax"></a>Syntax

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Nur für Anpassungen auf Dokumentebene erforderlich. Das `document` -Element befindet sich im `vstov4` Namespace. Das `document` -Element weist folgende Attribute auf.

|Attribut|Beschreibung|
|---------------|-----------------|
|`solutionId`|Erforderlich. Die GUID, die von der Visual Studio-Tools für Office-Laufzeit zur eindeutigen Identifizierung eine Projektmappe auf Dokumentebene verwendet wird. Dieser Wert wird als benutzerdefinierte Dokumenteigenschaften _AssemblyLocation-Eigenschaft gespeichert. Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](../vsto/custom-document-properties-overview.md).|

 `document` hat keine untergeordneten Elemente.

## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht die `document` Element in einer auf Dokumentebene Office-Projektmappe mithilfe von bereitgestellt [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)