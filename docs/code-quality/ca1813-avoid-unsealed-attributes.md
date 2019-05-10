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
ms.openlocfilehash: 4d7236b77a7dd0a81f8a7846c0eba28e3b520cdd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545588"
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

Die .NET Framework-Klassenbibliothek stellt Methoden zum Abrufen von benutzerdefinierten Attributen bereit. Standardmäßig wird mit diesen Methoden die Attributvererbungshierarchie durchsucht. Z. B. <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> sucht nach dem Typ des angegebenen Attributs oder jeder Typ des Attributs, das den Typ des angegebenen Attributs erweitert. Versiegeln das Attribut wird das Durchsuchen der Vererbungshierarchie befindet und kann die Leistung verbessern.

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