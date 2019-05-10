---
title: XML-Editor und Schema-designer
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8854aee047fa961c4f0973397cfc2fe6ac6e6ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808170"
---
# <a name="xml-tools-in-visual-studio"></a>XML-Tools in Visual Studio

*Extensible Markup Language (XML)* ist eine Markupsprache, die ein Format zum Beschreiben von Daten bereitstellt. XML trennt die Daten und deren Präsentation mit verknüpften Stylesheets wie Extensible Stylesheet Language (XSL) und cascading Stylesheets (CSS). Visual Studio enthält Tools und Funktionen, die das Arbeiten mit XML, XSLT und XML-Schemas vereinfachen.

## <a name="xml-editor"></a>XML-Editor

Die [XML-Editor](xml-editor.md) wird zum Bearbeiten von XML-Dokumenten verwendet. Es bietet vollständige XML-Syntax überprüfen "," Schema-Validierung während der Eingabe, farbcodierung und IntelliSense. Wenn ein Schema oder eine DTD (Dokumenttypdefinition) bereitgestellt wird, werden von IntelliSense damit die zulässigen Elemente und Attribute aufgelistet.

Folgende zusätzlichen Funktionen sind verfügbar:

- Unterstützung für XML-Codeausschnitte, einschließlich schemagenerierter Ausschnitte

- Dokumentieren Sie Gliederungen, sodass Elemente erweitert und reduziert werden können

- Die Möglichkeit zum Ausführen von XSLT-Transformationen und Anzeigen der Ergebnisse als Text, XML oder HTML

- Die Möglichkeit zum Generieren von Schemas für XML Schema Definition Language (XSD) aus dem XML-Instanzdokument

- Unterstützung für das Bearbeiten von XSLT-Stylesheets, einschließlich IntelliSense-Unterstützung

- XML-Schema-Explorer

## <a name="xml-schema-designer"></a>XML-Schema-Designer

Die [XML-Schema-Designer](xml-schema-designer.md) integriert ist, mit Visual Studio und dem XML-Editor, um mit Schemas für XML Schema Definition Language (XSD) arbeiten können.

## <a name="xslt-debugging"></a>Debuggen von XSLT-Code

Visual Studio unterstützt [Debuggen von XSLT-Stylesheets](../xml-tools/debugging-xslt.md). Mithilfe des Debuggers können Sie Haltepunkte in einem XSLT-Stylesheet festlegen, den Code in einem XSLT-Stylesheet schrittweise ausführen usw.

> [!NOTE]
> Der XSLT-Debugger ist nur verfügbar, in der Enterprise Edition von Visual Studio.

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml?displayProperty=fullName>
- [XSLT-Transformationen](/dotnet/standard/data/xml/xslt-transformations)
- [Verarbeiten von XML-Daten mithilfe des XPath-Datenmodells](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [XML-Dokumentobjektmodell (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [XML Schema Object Model (SOM) (XML-Schemaobjektmodell (SOM))](/dotnet/standard/data/xml/xml-schema-object-model-som)