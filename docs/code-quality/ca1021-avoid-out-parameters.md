---
title: 'CA1021: out-Parameter vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea570ff50ea48286bcb52b56acdd108516b02022
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779395"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: out-Parameter vermeiden.

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ hat einen `out` Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Übergabe von Typen als Verweis (mit `out` oder `ref`) erfordert Erfahrung mit Zeigern, Kenntnisse der Unterschiede zwischen Werttypen und Verweistypen und Umgang mit Methoden mit mehreren Rückgabewerten. Außerdem ist der Unterschied zwischen `out` und `ref` Parameter kann häufig nicht interpretiert werden.

 Wenn ein Verweistyp "by Reference" übergeben wird, soll die Methode ab, den Parameter zu verwenden, um eine andere Instanz des Objekts zurückzugeben. Übergabe eines Verweistyps als Verweis wird auch als mithilfe eines Zeigers, double, Zeiger auf einen Zeiger oder doppelte Dereferenzierung bezeichnet. Unter Verwendung des standardmäßigen Aufrufkonvention, die "als Wert" übergeben wird, erhält ein Parameter, der einen Verweistyp bereits akzeptiert einen Zeiger auf das Objekt. Der Zeiger ist, nicht auf das Objekt aus, die auf den er verweist, wird als Wert übergeben. Übergeben Sie als Wert bedeutet, die die Methode nicht den Zeiger, damit diese auf eine neue Instanz des Verweistyps ändern kann. Allerdings können sie den Inhalt des Objekts ändern, auf den er verweist. Für die meisten Anwendungen müssen dies ist ausreichend, und das gewünschte Verhalten zeigt.

 Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie der Rückgabewert der Methode, um dies zu erreichen. Finden Sie unter den <xref:System.String?displayProperty=fullName> -Klasse für eine Vielzahl von Methoden, die für Zeichenfolgen verwendet werden, und geben Sie eine neue Instanz einer Zeichenfolge zurück. Wenn dieses Modell verwendet wird, muss der Aufrufer entscheiden, ob das ursprüngliche Objekt beibehalten wird.

 Zwar sind in aller Munde und häufig verwendet, die richtige Anwendung der Rückgabewerte `out` und `ref` Parameter erfordert, mittlere Design- und Fertigkeiten im coding. Entwurf für eine Breite Zielgruppe master arbeiten mit Benutzern nicht erwarten sollten Entwickler von Bibliotheken `out` oder `ref` Parameter.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, die von einem Werttyp verursacht wird, müssen Sie die Methode, die das Objekt als ihren Rückgabewert zurück. Wenn die Methode mehrere Werte zurückgeben muss, Umgestalten Sie, um eine einzelne Instanz eines Objekts zurück, der die Werte enthält.

 Um einen Verstoß gegen diese Regel zu beheben, die von einem Verweistyp verursacht wird, stellen Sie sicher, dass das gewünschte Verhalten ist, um eine neue Instanz des Verweises zurückzugeben. Wenn es sich handelt, sollte die Methode den Rückgabewert verwenden, hierzu.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel. Dieser Entwurf könnte jedoch Probleme hinsichtlich der Verwendbarkeit führen.

## <a name="example"></a>Beispiel
 Die folgende Bibliotheken zeigt zwei Implementierungen von eine Klasse, die Antworten auf das Feedback der Benutzer wird generiert. Die erste Implementierung (`BadRefAndOut`) erzwingt, dass Benutzer der Bibliothek, die drei Rückgabewerte zu verwalten. Die zweite Implementierung (`RedesignedRefAndOut`) vereinfacht die benutzererfahrung durch Rückgabe einer Instanz einer Container-Klasse (`ReplyData`), die die Daten als einzelne Einheit verwaltet.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung zeigt die Erfahrung des Benutzers. Der Aufruf der umgestalteten Bibliothek (`UseTheSimplifiedClass` Methode) ist einfacher, und die von der Methode zurückgegebenen Informationen ist einfach zu verwalten. Die Ausgabe der beiden Methoden ist identisch.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Beispiel
 Die folgende Beispielbibliothek wird veranschaulicht, wie `ref` Parameter für Referenztypen verwendet werden, und eine bessere Möglichkeit zur Implementierung dieser Funktionalität.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung ruft jede Methode in der Bibliothek, um das Verhalten zu veranschaulichen.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="try-pattern-methods"></a>Probieren Sie Mustermethoden

### <a name="description"></a>Beschreibung
 Methoden, implementieren die **versuchen\<etwas >** Muster, wie z. B. <xref:System.Int32.TryParse%2A?displayProperty=fullName>, lösen keine diese Verletzung. Das folgende Beispiel zeigt eine Struktur (Werttyp), implementiert die <xref:System.Int32.TryParse%2A?displayProperty=fullName> Methode.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1045: Typen nicht als Verweis übergeben](../code-quality/ca1045-do-not-pass-types-by-reference.md)