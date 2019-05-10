---
title: 'CA1011: Basistypen als Parameter übergeben.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 644c581757a559311b6660a77c4d9190a7361314
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779546"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Basistypen als Parameter übergeben.

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methodendeklaration enthält einen formalen Parameter, der ein abgeleiteter Typ ist, und die Methode ruft nur Member der Basisklasse des Parameters.

## <a name="rule-description"></a>Regelbeschreibung

Wenn in einer Methodendeklaration ein Basistyp als Parameter angegeben wird, kann jeder Typ, der von diesem Basistyp abgeleitet ist, als entsprechendes Argument an die Methode übergeben werden. Wenn das Argument innerhalb des Methodentexts verwendet wird, hängt die spezifische Methode, die ausgeführt wird, der den Typ des Arguments. Wenn die zusätzliche Funktionalität, die vom abgeleiteten Typ bereitgestellt wird, nicht erforderlich ist, ermöglicht die Verwendung des Basistyps allgemeinere Nutzung der Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ des Parameters in den Basistyp.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicherer, unterdrücken Sie eine Warnung dieser Regel

- Wenn die Methode, die bestimmte Funktionen erfordert, die vom abgeleiteten Typ bereitgestellt wird

     \- oder –

- um zu erzwingen, dass nur der abgeleitete Typ oder einen stärker abgeleiteten Typ, an die Methode übergeben wird.

In diesen Fällen wird der Code sein stabiler aufgrund der starken typüberprüfung, die vom Compiler und Laufzeit bereitgestellt wird.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, `ManipulateFileStream`, die verwendet werden kann, nur mit einem <xref:System.IO.FileStream> -Objekt, das gegen diese Regel verstößt. Eine zweite Methode, `ManipulateAnyStream`, verstößt die Regel, und Ersetzen Sie dabei die <xref:System.IO.FileStream> Parameter, indem eine <xref:System.IO.Stream>.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1059: Member sollten bestimmte konkreten Typen nicht verfügbar machen](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)