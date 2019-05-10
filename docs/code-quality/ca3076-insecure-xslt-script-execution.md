---
title: 'CA3076: Unsichere XSLT-Skriptausführung.'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f98b022aef49a4d98ad4864793aa55732f8de6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541089"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Unsichere XSLT-Skriptausführung.

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Wenn Sie Extensible Stylesheets Language Transformations (XSLT) ungesichert in .NET-Anwendungen ausführen, könnte der Prozessor möglicherweise nicht vertrauenswürdige URI-Verweise auflösen, wodurch Angreifern sensible Informationen offengelegt werden könnten, was wiederum zu Denial-of-Service- und Cross-Site-Angriffen führen kann. Weitere Informationen finden Sie unter [XSLT-Sicherheit Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Regelbeschreibung

**XSLT** ist ein W3C-Standard (World Wide Web Consortium) zum Transformieren von XML-Daten. XSLT wird normalerweise verwendet, um Stylesheets zum Transformieren von XML-Daten in andere Formate wie HTML, Text mit fester Länge, durch Trennzeichen getrennter Text oder ein anderes XML-Format zu schreiben. Dies ist zwar standardmäßig nicht zulässig, sie können die Option aber für Ihr Projekt aktivieren.

Um sicherzustellen, können Sie keine Angriffsfläche, mit dieser Regel wird ausgelöst, wenn die "XslCompiledTransform".<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Unsichere Kombinationen aus empfängt <xref:System.Xml.Xsl.XsltSettings> und <xref:System.Xml.XmlResolver>, wodurch die Verarbeitung von bösartigen Skripts.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

- Ersetzen Sie das unsichere XsltSettings-Argument durch XsltSettings an.<xref:System.Xml.Xsl.XsltSettings.Default%2A> oder mit einer Instanz, die Dokument-Funktion und Skript die Ausführung deaktiviert wurde.

- Ersetzen Sie das <xref:System.Xml.XmlResolver> -Argument durch „Null“ oder eine <xref:System.Xml.XmlSecureResolver> -Instanz.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Regel aus dieser Warnung niemals, es sei denn, Sie sind ganz sicher, dass die Eingabe von einer vertrauenswürdigen Quelle stammt.

## <a name="pseudo-code-examples"></a>Pseudocodebeispiele

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Verletzung, die XsltSettings.TrustedXslt verwendet.

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
}
```

### <a name="solution-that-uses-xsltsettingsdefault"></a>Lösung, die XsltSettings.Default verwendet.

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Verletzung&mdash;Dokumentieren der Dokumentfunktion und skriptausführung Ausführung nicht deaktiviert.

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Lösung&mdash;Dokument Dokumentfunktion und skriptausführung ausführen deaktivieren

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- [XSLT-Sicherheitsaspekte (Handbuch für die .NET)](/dotnet/standard/data/xml/xslt-security-considerations)