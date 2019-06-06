---
title: 'CA1813: Nicht versiegelte Attribute vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a17c5bdc9e21bdf877206b1dc28596c251049455
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714751"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Nicht versiegelte Attribute vermeiden.

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein öffentlicher Typ erbt von <xref:System.Attribute?displayProperty=fullName>ist nicht abstrakt und ist nicht versiegelt (`NotInheritable` in Visual Basic).

## <a name="rule-description"></a>Regelbeschreibung

.NET bietet Methoden zum Abrufen von benutzerdefinierten Attributen. Standardmäßig wird mit diesen Methoden die Attributvererbungshierarchie durchsucht. Z. B. <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> sucht nach dem Typ des angegebenen Attributs oder jeder Typ des Attributs, das den Typ des angegebenen Attributs erweitert. Versiegeln das Attribut wird das Durchsuchen der Vererbungshierarchie befindet und kann die Leistung verbessern.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, versiegeln Sie den Typ des Attributs oder abstract.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, unterdrücken Sie eine Warnung dieser Regel. Unterdrücken Sie nur dann, wenn Sie eine Attributhierarchie definieren und können nicht versiegeln das Attribut oder abstract.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein benutzerdefiniertes Attribut, das diese Regel erfüllt.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1019: Accessors für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018: Attribute mit AttributeUsageAttribute markieren](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Siehe auch

- [Attribute](/dotnet/standard/design-guidelines/attributes)