---
title: 'CA1023: Indexer sollten nicht mehrdimensional sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef3afd9dda70d02698abec5459b36e6acc2c5ed0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779615"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Indexer sollten nicht mehrdimensional sein.

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält, einen öffentlichen oder geschützten Indexer, der mehr als einen Index verwendet wird.

## <a name="rule-description"></a>Regelbeschreibung
 Indexer, d. h. indizierte Eigenschaften, sollte es sich um einen einzelnen Index verwenden. Mehrdimensionale Indexer können die Verwendbarkeit der Bibliothek deutlich reduzieren. Wenn der Entwurf mehrere Indizes erfordert, überdenken Sie, ob der Typ einen logischen Datenspeicher darstellt. Wenn dies nicht der Fall ist, verwenden Sie eine Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das Design ein Ganzzahl- oder Zeichenfolgenindex verwenden, oder verwenden Sie eine Methode anstelle des Indexers.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel erst nach den Bedarf für den Indexer nicht dem Standard entsprechende sorgfältig geprüft.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `DayOfWeek03`, mit einem mehrdimensionalen Indexer, die die Regel verletzen. Der Indexer kann als eine Art der Konvertierung betrachtet werden und daher besser als verfügbar gemacht wird eine Methode. Der Typ wird umgestaltet `RedesignedDayOfWeek03` um die Regel zu erfüllen.

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Verwenden Sie Eigenschaften](../code-quality/ca1024-use-properties-where-appropriate.md)