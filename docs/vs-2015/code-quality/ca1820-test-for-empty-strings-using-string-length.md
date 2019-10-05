---
title: 'CA1820: Test mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bebd3b78881f9e1a2f4908ea667f80cbd7b98dd6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201718"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Zeichenfolge ist eine leere Zeichenfolge verglichen, mit <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 Vergleichen von Zeichenfolgen mithilfe der <xref:System.String.Length%2A?displayProperty=fullName> Eigenschaft oder die <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> Methode ist deutlich schneller als die Verwendung von <xref:System.Object.Equals%2A>. Grund hierfür ist, <xref:System.Object.Equals%2A> führt die erheblich mehr MSIL-Anweisungen als <xref:System.String.IsNullOrEmpty%2A> oder die Anzahl von Anweisungen ausgeführt, um die <xref:System.String.Length%2A> Eigenschaft Wert ein, und vergleichen Sie ihn auf 0 (null).

 Sie sollten sich bewusst sein, die <xref:System.Object.Equals%2A> und <xref:System.String.Length%2A> == 0 bei null-Zeichenfolgen anders verhalten. Wenn Sie versuchen, den Wert der Abrufen der <xref:System.String.Length%2A> Eigenschaft eine null-Zeichenfolge, die common Language Runtime löst eine <xref:System.NullReferenceException?displayProperty=fullName>. Wenn Sie einen Vergleich zwischen einem null-Zeichenfolge und die leere Zeichenfolge ausführen, löst die common Language Runtime keine Ausnahme aus; Gibt zurück, der Vergleich `false`. Testen auf Null erheblich wirkt die relative Leistung der beiden Ansätze sich nicht. Wenn [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], verwenden Sie die <xref:System.String.IsNullOrEmpty%2A> Methode. Verwenden Sie andernfalls die <xref:System.String.Length%2A> == Vergleich, wann immer möglich.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Vergleich so um die <xref:System.String.Length%2A> -Eigenschaft und der Test für die null-Zeichenfolge. Wenn [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], verwenden Sie die <xref:System.String.IsNullOrEmpty%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die Leistung kein Problem darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht die verschiedenen Methoden, die verwendet werden, um eine leere Zeichenfolge zu suchen.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
