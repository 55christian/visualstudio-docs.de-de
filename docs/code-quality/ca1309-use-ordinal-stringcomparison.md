---
title: 'CA1309: Ordinal-StringComparison verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b00accdbdb08e4267bbca2b7e5fab8002f539f1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546478"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Ordinal-StringComparison verwenden.

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Die durch einen nicht linguistischen Zeichenfolgenvergleich wird nicht festgelegt. die <xref:System.StringComparison> Parameter entweder **Ordnungszahl** oder **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Regelbeschreibung
 Viele Zeichenfolgenoperationen, vor allem die <xref:System.String.Compare%2A?displayProperty=fullName> und <xref:System.String.Equals%2A?displayProperty=fullName> Methoden bieten jetzt eine Überladung, die akzeptiert eine <xref:System.StringComparison?displayProperty=fullName> Enumerationswert als Parameter.

 Wenn Sie angeben, entweder **StringComparison.Ordinal** oder **StringComparison.OrdinalIgnoreCase**, beim Vergleich der Zeichenfolgen nicht linguistisch ist. Beim Vergleich Entscheidungen getroffen werden, werden, also die Funktionen, die spezifisch für die natürliche Sprache sind ignoriert. Features der natürlichen Sprache wird ignoriert, bedeutet, dass es sich bei basieren die Entscheidungen, die auf einfache bytevergleiche und nicht auf Groß-und Kleinschreibung oder Äquivalenz-Tabellen, die nach Kultur parametrisierten entsprechungstabellen. Daher durch Festlegen von den Parameter explizit auf die **StringComparison.Ordinal** oder **StringComparison.OrdinalIgnoreCase**, Ihren Code häufig beschleunigt, erhöht der Richtigkeit und wird zuverlässiger.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Methode zum Zeichenfolgenvergleich an eine Überladung, die akzeptiert die <xref:System.StringComparison?displayProperty=fullName> -Enumeration als Parameter, und geben Sie entweder **Ordnungszahl** oder **OrdinalIgnoreCase**. Ändern Sie beispielsweise `String.Compare(str1, str2)` zu `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe vorgesehen ist, oder wenn die Semantik der aktuellen Kultur verwendet werden soll.

## <a name="see-also"></a>Siehe auch

- [Globalisierungswarnungen](../code-quality/globalization-warnings.md)
- [CA1307: StringComparison angeben](../code-quality/ca1307-specify-stringcomparison.md)