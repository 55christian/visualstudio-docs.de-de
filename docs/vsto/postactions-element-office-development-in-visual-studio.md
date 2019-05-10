---
title: '&lt;PostActions&gt; -Element (Office-Entwicklung in Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 548396e6393720824c93c07e55046ec2d91797a2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561465"
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;PostActions&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `postActions` -Element des `vstav3` -Namespace enthält alle `postAction` -Elemente, die Aktionen nach der Bereitstellung beschreiben, die ausgeführt werden, nachdem Office-Projektmappen installiert sind.

## <a name="syntax"></a>Syntax

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `postActions` -Element ist optional und befindet sich im `vstav3` -Namespace. In einem Anwendungsmanifest ist nur ein `postActions` -Element definiert.

 Das `postActions` -Element weist keine Attribute auf.

 `postActions` weist das folgende Element auf:

### <a name="postaction"></a>postAction
 Dies ist optional. Die Rolle der `postAction` Element in der `vstav3` Namespace definiert ist, [ &#60;PostAction&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Beispiel für die Aktion nach der Bereitstellung

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht das `postActions` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstav3:postActions>
  <vstav3:postAction>
    <vstav3:entryPoint
      class="PostDeploymentAction.PostDeploymentActionSample">
      <assemblyIdentity
        name="PostDeploymentAction"
        version="1.0.0.0"
        language="neutral"
        processorArchitecture="msil" />
    </vstav3:entryPoint>
    <vstav3:postActionData>
    </vstav3:postActionData>
  </vstav3:postAction>
</vstav3:postActions>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
