---
title: Der Support-Website | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9f6e287a2cd91b0a5eb0d04130627faa787ccac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323186"
---
# <a name="web-site-support"></a>Websiteunterstützung
Ein Website-Projektsystem ist ein Projektsystem, das Webprojekte erstellt. Webprojekte erstellen wiederum die Webanwendungen. Ein Websiteprojekt generiert eine ausführbare Datei für jede Webseite, die Code verknüpft ist. Weitere ausführbare Dateien werden aus der Quellcodedateien im Ordner "kann" generiert.

 Website-Projektsystemen sind durch Hinzufügen von Vorlagen und die Registrierungsattribute auf einem vorhandenen Projektsystem erstellt. Eines dieser Attribute wählt den IntelliSense-Anbieter für die Sprache aus. Die IntelliSense-anbieterimplementierung Verweise verarbeitet und Sprachcompilers, die aufgerufen, wenn eine intelligente Webseite, die nicht zwischengespeichert werden angefordert wird.

 Der Language-Compiler zum Kompilieren von Webseiten verwendet muss registriert werden, mit [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Sie können die [ \<Compiler > Element](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) in einer Datei "Web.config", um den Compiler an, wie im folgenden Beispiel zu registrieren:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>In diesem Abschnitt
- [Vorlagen für die Websiteunterstützung](../../extensibility/internals/web-site-support-templates.md)

 Listet die Vorlagen, die Sie verwenden können, um neue Websiteprojekte und zugehörige Elemente zu erstellen.

- [Attribute der Websiteunterstützung](../../extensibility/internals/web-site-support-attributes.md)

 Stellt die Registrierungsattribute, die ein Websiteprojekt zu verbinden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].

## <a name="related-sections"></a>Verwandte Abschnitte
- [Webprojekte](../../extensibility/internals/web-projects.md)

 Bietet eine Übersicht über die zwei Arten von Webprojekten, von Websiteprojekten und Webanwendungsprojekten an.