---
title: 'CA1309: Ordinal-StringComparison verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7b491cf06528b67c96f90f314210e61800e0cab1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200337"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Ordinal-StringComparison verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Wenn Sie angeben, entweder **StringComparison.Ordinal** oder **StringComparison.OrdinalIgnoreCase**, einen nicht linguistischen Zeichenfolgenvergleich werden. Beim Vergleich Entscheidungen getroffen werden, werden, also die Funktionen, die spezifisch für die natürliche Sprache sind ignoriert. Dies bedeutet, dass die Entscheidungen basieren auf einfache bytevergleiche und ignorieren von Groß-/Kleinschreibung oder Äquivalenz Tabellen, die nach Kultur parametrisierten entsprechungstabellen. Daher durch Festlegen von den Parameter explizit auf die **StringComparison.Ordinal** oder **StringComparison.OrdinalIgnoreCase**, Ihren Code häufig beschleunigt, erhöht der Richtigkeit und wird zuverlässiger.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Methode zum Zeichenfolgenvergleich an eine Überladung, die akzeptiert die <xref:System.StringComparison?displayProperty=fullName> -Enumeration als Parameter, und geben Sie entweder **Ordnungszahl** oder **OrdinalIgnoreCase**. Ändern Sie beispielsweise `String.Compare(str1, str2)` zu `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel aus, wenn die Bibliothek oder Anwendung vorgesehen ist, für eine begrenzte lokale Zielgruppe oder wenn die Semantik der aktuellen Kultur verwendet werden soll.

## <a name="see-also"></a>Siehe auch
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md) [CA1307: StringComparison angeben](../code-quality/ca1307-specify-stringcomparison.md)
