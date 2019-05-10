---
title: 'CA1038: Enumeratoren sollten starke Typisierung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 84b6ae6ef0c63870ad9dc593fd0cf2e166e65397
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559831"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Enumeratoren sollten eine starke Typisierung aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.IEnumerator?displayProperty=fullName> jedoch nicht über eine stark typisierte Version von bietet die <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> Eigenschaft. Typen, die aus den folgenden Typen abgeleitet werden, sind von dieser Regel ausgenommen:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel muss <xref:System.Collections.IEnumerator> Implementierungen stark typisierte Version des auch angeben, die <xref:System.Collections.IEnumerator.Current%2A> Eigenschaft, damit Benutzer nicht erforderlich, die den Rückgabewert in den starken Typ umwandeln, wenn sie die Funktionen verwenden, die bereitgestellt wird von der Schnittstelle. Mit dieser Regel wird davon ausgegangen, dass der Typ, der implementiert <xref:System.Collections.IEnumerator> enthält eine Auflistung von Instanzen eines Typs, der stärker ist als <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, explizit die Schnittstelleneigenschaft implementieren (deklarieren Sie sie als `IEnumerator.Current`). Hinzufügen einer öffentliche stark typisierte Version der Eigenschaft, die als deklariert `Current`, und geben Sie ein stark typisiertes Objekt zurück.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie einen objektbasierten Enumerator für die Verwendung mit einer Auflistung von objektbasierten, z. B. einer binären Struktur implementieren. Typen, die erweitern die neue Sammlung, definieren den stark typisierten Enumerator und stark typisierte Eigenschaft verfügbar machen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht die richtige Vorgehensweise zum Implementieren Sie eine stark typisierte <xref:System.Collections.IEnumerator> Typ.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listen sind stark typisiert.](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
