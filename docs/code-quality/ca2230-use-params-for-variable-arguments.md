---
title: 'CA2230: params für Variablenargumente verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3318a9f5bd65c6b9514519936cc52e037e0c215
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541782"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: params für Variablenargumente verwenden.

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält eine öffentliche oder geschützte Methode, verwendet der `VarArgs` Aufrufkonvention.

## <a name="rule-description"></a>Regelbeschreibung
 Die `VarArgs` -Aufrufkonvention bei bestimmten Methodendefinitionen, die eine Variable Anzahl von Parametern akzeptieren verwendet wird. Eine Methode mit dem `VarArgs` -Aufrufkonvention wird keine Common Language Specification (CLS) kompatibel und kann nicht in verschiedenen Programmiersprachen zugegriffen werden.

 In c# die `VarArgs` -Aufrufkonvention wird so lange verwendet, wenn die Parameterliste einer Methode endet die `__arglist` Schlüsselwort. Visual Basic unterstützt nicht die `VarArgs` Aufrufkonvention und Visual C++ können Sie die Verwendung nur in nicht verwaltetem Code, der die Ellipse verwendet `...` Notation.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel in C# -Code zu beheben, verwenden die [Params](/dotnet/csharp/language-reference/keywords/params) -Schlüsselwort anstelle von `__arglist`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden, die gegen die Regel verstößt und eine, die die Regel erfüllt.

 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Sprachunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)