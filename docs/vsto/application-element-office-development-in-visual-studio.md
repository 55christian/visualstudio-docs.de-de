---
title: '&lt;Anwendung&gt; -Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80652f6752b87cf0413b0b3166b0cf3292231c25
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942910"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;Anwendung&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `application` -Element des `vstav3` -Namespace umschließt die Beschreibung von Office-Projektmappen Die untergeordneten Elemente sind für Anpassungen auf Dokumentebene und für VSTO-Add-Ins unterschiedlich.

## <a name="syntax-for-document-level-customizations"></a>Syntax für Anpassungen auf Dokumentebene

```xml
<application>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</application>
```

## <a name="syntax-for-application-level-add-ins"></a>Syntax für Add-Ins auf Anwendungsebene

```xml
<application>
  <customization
    id
    <appAddin
      application
      loadBehavior
      keyName>
    <friendlyName></friendlyName>
    <description></description>
    <formRegions></formRegions>
  </customization>
</application>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `application` -Element des `vstav3` -Namespace ist der Knoten, der alle anpassungsspezifischen Informationen umschließt, die im `vstov4` -Namespace enthalten sind.

 Das `application` -Element weist keine Attribute auf.

 Das `application` -Element hat das folgende Element.

### <a name="customization"></a>Anpassung
 Die Rolle der `customization` Element in der `vstov3` Namespace definiert ist, [ &#60;Anpassung&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht ein `application` -Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellten Office-Projektmappe auf Dokumentebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:document
        solutionId="73e" />
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht ein `application` -Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellten Office-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:appAddIn
        application="Outlook"
        loadBehavior="3"
        keyName="ContosoOutlookAddIn">
        <vstov4:friendlyName>
          ContosoOutlookAddIn
        </vstov4:friendlyName>
        <vstov4:description>
          ContosoOutlookAddIn - Outlook VSTO Add-in
          created with Visual Studio Tools for Office
        </vstov4:description>
        <vstov4:formRegions>
          <vstov4:formRegion
              name="OutlookAddIn1.FormRegion1">
            <vstov4:messageClass name="IPM.Note" />
            <vstov4:messageClass name="IPM.Contact" />
            <vstov4:messageClass name="IPM.Appointment" />
          </vstov4:formRegion>
        </vstov4:formRegions>
      </vstov4:appAddIn>
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)