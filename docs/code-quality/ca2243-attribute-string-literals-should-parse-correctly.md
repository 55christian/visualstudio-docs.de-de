---
title: 'CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12007beaffab1e046ae7f359bf2988c02278fd91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541453"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Attribut des Zeichenfolgenliteral-Parameter wird für eine URL, GUID oder Version nicht ordnungsgemäß analysiert.

## <a name="rule-description"></a>Regelbeschreibung
 Da Attribute abgeleitet werden <xref:System.Attribute?displayProperty=fullName>, und Attribute werden zum Zeitpunkt der Kompilierung verwendet, nur konstante Werte, die an ihre Konstruktoren übergeben werden können. Zuordnen von Parametern, die URLs, GUIDs und -Versionen darstellen müssen, können nicht als eingegeben werden <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, und <xref:System.Version?displayProperty=fullName>, da diese Typen als Konstanten dargestellt werden können. Sie müssen stattdessen durch Zeichenfolgen dargestellt werden.

 Da der Parameter als Zeichenfolge typisiert ist, ist es möglich, dass zum Zeitpunkt der Kompilierung ein falsch formatierter Parameter übergeben werden kann.

 Mit dieser Regel wird eine Benennungskonvention Heuristik verwendet wird, um Parameter zu suchen, die einen uniform Resource Identifier (URI), eine GUID (GLOBALLY Unique Identifier) oder eine Version darstellen, und stellt sicher, dass der übergebene Wert richtig ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie die Zeichenfolge in eine ordnungsgemäß formatierte URL, GUID oder Version an.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn der Parameter keine URL, GUID oder Version darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt Code für die AssemblyFileVersionAttribute, die gegen diese Regel verstößt.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

 Die Regel wird ausgelöst, durch die folgenden Parameter:

- Parameter, 'Version' enthalten und können nicht analysiert werden, um System.Version.

- Parameter, "Guid" enthalten und können nicht analysiert werden, um System.Guid.

- Parameter, "Uri", "Urn" oder "Url" enthalten und können nicht analysiert werden, in System.Uri.

## <a name="see-also"></a>Siehe auch

- [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)