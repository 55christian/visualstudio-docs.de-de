---
title: 'CA2225: Operator Überladungen weisen benannte Alternativen auf | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 212abc1fa5e2debfaf7ca81d82c8d94e9ddb0879
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658873"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Operatorüberladungen weisen benannte Alternativen auf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden.

## <a name="rule-description"></a>Regelbeschreibung
 Die Operator Überladung ermöglicht die Verwendung von Symbolen zur Darstellung von Berechnungen für einen Typ. Beispielsweise würde ein Typ, der das Pluszeichen (+) zusätzlich über lädt, in der Regel einen alternativen Member mit dem Namen "Add" aufweisen. Der benannte Alternative Member bietet Zugriff auf die gleiche Funktionalität wie der-Operator und wird für Entwickler bereitgestellt, die in Sprachen programmieren, die überladene Operatoren nicht unterstützen.

 Diese Regel überprüft die in der folgenden Tabelle aufgeführten Operatoren.

|C#|Visual Basic|C++|Alternativer Name|
|---------|------------------|-----------|--------------------|
|+ (binär)|+|+ (binär)|Hinzufügen|
|+=|+=|+=|Hinzufügen|
|&|And|&|BitwiseAnd|
|&=|Und =|&=|BitwiseAnd|
|&#124;|Or|&#124;|BitwiseOr|
|&#124;=|Oder =|&#124;=|BitwiseOr|
|--|Nicht zutreffend|--|Dekrement|
|/|/|/|Teilen|
|/=|/=|/=|Teilen|
|==|=|==|gleich|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Vergleichen|
|>=|>=|>=|Vergleichen|
|++|Nicht zutreffend|++|Inkrement|
|<>|!=|gleich|
|<<|<<|<<|Linke UMSCHALTTASTE|
|<<=|<<=|<<=|Linke UMSCHALTTASTE|
|<|<|<|Vergleichen|
|<=|<=|\<=|Vergleichen|
|&&|Nicht zutreffend|&&|LogicalAnd|
||||Nicht zutreffend||||Logicalor|
|!|Nicht zutreffend|!|LogicalNot|
|%|Mod|%|Mod oder Restwert|
|%=|Nicht zutreffend|%=|Mod|
|* (binär)|*|*|Multiplizieren|
|*=|Nicht zutreffend|*=|Multiplizieren|
|~|not|~|Oneskomplement|
|>>|>>|>>|Lesefolge wechseln|
=|Nicht zutreffend|>>=|Lesefolge wechseln|
|-(binär)|-(binär)|-(binär)|Subtrahieren|
|-=|Nicht zutreffend|-=|Subtrahieren|
|true|IsTrue|Nicht zutreffend|IsTrue (Eigenschaft)|
|- (unary)|Nicht zutreffend|-|Negation|
|+ (unär)|Nicht zutreffend|+|ZZ|
|False|IsFalse|False|IsTrue (Eigenschaft)|

 N/A = = kann nicht in der ausgewählten Sprache überladen werden.

 Die Regel überprüft auch implizite und explizite Umwandlungs Operatoren in einem Typ (`SomeType`), indem Sie auf Methoden mit dem Namen `ToSomeType` und `FromSomeType` prüft.

 Wenn C#in ein binärer Operator überladen wird, wird der entsprechende Zuweisungs Operator (sofern vorhanden) ebenfalls implizit überladen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die alternative-Methode für den-Operator. nennen Sie Sie mithilfe des empfohlenen alternativen namens.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, wenn Sie eine freigegebene Bibliothek implementieren. Anwendungen können eine Warnung aus dieser Regel ignorieren.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine Struktur definiert, die gegen diese Regel verstößt. Um das Beispiel zu korrigieren, fügen Sie der-Struktur eine öffentliche `Add(int x, int y)`-Methode hinzu.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
