---
title: 'CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6eda1bc311c39d0ec1da9667ac078c22183e2bd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535748"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.ICollection?displayProperty=fullName> jedoch keine stark typisierte Methode für <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Die Version mit starker Typisierung von <xref:System.Collections.ICollection.CopyTo%2A> muss zwei Parameter annehmen und keine <xref:System.Array?displayProperty=fullName> oder ein Array von <xref:System.Object?displayProperty=fullName> als ersten Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel muss <xref:System.Collections.ICollection> Implementierungen angeben, stark typisierte Member, damit Benutzer nicht umwandeln müssen, Argumente, die die <xref:System.Object> eingeben, wenn sie die Funktionen verwenden, die bereitgestellt wird von der Schnittstelle. Mit dieser Regel wird davon ausgegangen, dass der Typ, der implementiert <xref:System.Collections.ICollection> wird zum Verwalten einer Auflistung von Instanzen eines Typs, der stärker ist als <xref:System.Object>.

 <xref:System.Collections.ICollection> implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName>-Schnittstelle. Wenn die Objekte in der Auflistung erweitern <xref:System.ValueType?displayProperty=fullName>, müssen Sie für einen stark typisierten Member angeben <xref:System.Collections.IEnumerable.GetEnumerator%2A> um Leistungseinbußen zu vermeiden, die durch Boxing verursacht wird. Dies ist nicht erforderlich, wenn die Objekte der Auflistung einen Verweistyp handelt.

 Um eine stark typisierte Version eines Schnittstellenmembers implementieren, implementieren Sie den Schnittstellenmember explizit mithilfe von Namen in der Form `InterfaceName.InterfaceMemberName`, z. B. <xref:System.Collections.ICollection.CopyTo%2A>. Die explizite Schnittstellenmember werden die Datentypen, die deklariert werden durch die Schnittstelle verwenden. Die stark typisierte Member implementieren, indem Sie den Namen des Schnittstellenmembers, wie <xref:System.Collections.ICollection.CopyTo%2A>. Die stark typisierte Member als öffentlich deklariert und deklarieren Sie die Parameter und Rückgabewerte, um den starken Typ aufweisen, der von der Sammlung verwaltet wird. Die starke Typen ersetzen schwächere Typen wie z. B. <xref:System.Object> und <xref:System.Array> , die von der Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Schnittstellenmember explizit (deklarieren Sie sie als <xref:System.Collections.ICollection.CopyTo%2A>). Fügen Sie den öffentlichen stark typisierten Member, die als deklariert `CopyTo`, und lassen Sie sie ein stark typisiertes Array als ersten Parameter annehmen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie eine neue objektbasierte Sammlung, z. B. eine binäre Struktur implementieren, in dem der Typen, die die neue Auflistung erweitern den starken Typ bestimmen. Diese Typen sollten mit dieser Regel entsprechen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht die richtige Methode zum Implementieren <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listen sind stark typisiert.](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
