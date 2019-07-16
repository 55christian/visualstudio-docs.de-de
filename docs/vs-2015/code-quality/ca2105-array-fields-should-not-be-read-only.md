---
title: 'CA2105: Arrayfelder nicht nur lesen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4741b30d1429a1a179328c8fb4b150fc4f920612
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154387"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Arrayfelder dürfen nicht schreibgeschützt sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentliches oder geschütztes Feld, das ein Array enthält, ist schreibgeschützt deklariert.

## <a name="rule-description"></a>Regelbeschreibung
 Beim Anwenden der `readonly` (`ReadOnly` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) Modifizierer, um ein Feld, das ein, das Feld Array kann nicht geändert werden, um auf ein anderes Array zu verweisen. Allerdings können die in einem schreibgeschützten Feld des Arrays gespeicherten Elemente geändert werden. Code, der Entscheidungen trifft oder führt Vorgänge, die für die Elemente eines Arrays von nur-Lese basieren, die öffentlich zugegriffen werden kann, kann ein ausnutzbaren Sicherheitsrisiko enthalten.

 Beachten Sie, dass ein öffentliches Feld mit verstößt auch gegen die Entwurfsregel [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um das Sicherheitsrisiko zu beheben, das von dieser Regel identifiziert wird, verlassen Sie sich nicht auf dem Inhalt eines nur-Lese Arrays, die öffentlich zugegriffen werden kann. Es wird dringend empfohlen, dass Sie eine der folgenden Verfahren verwenden:

- Ersetzen Sie das Array, durch eine stark typisierte Auflistung, die nicht geändert werden kann. Weitere Informationen finden Sie unter <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Ersetzen Sie das öffentliche Feld mit einer Methode, die einen Klon der ein privates Array zurückgibt. Da Ihr Code nicht auf dem Klon abhängig ist, besteht keine Gefahr, wenn die Elemente geändert werden.

  Wenn Sie den zweiten Ansatz gewählt haben, ersetzen Sie das Feld nicht mit einer Eigenschaft. Eigenschaften, die Arrays zurückgeben, sich negativ auf die Leistung beeinträchtigen. Weitere Informationen finden Sie unter [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Eine Warnung dieser Regel wird dringend abgeraten. Fast kein Szenario auftreten, in denen der Inhalt eines schreibgeschützten Felds nicht von Bedeutung sind. Wenn dies Ihr Szenario zutrifft, entfernen Sie die `readonly` Modifizierer anstelle der Meldung auszuschließen.

## <a name="example"></a>Beispiel
 Dieses Beispiel veranschaulicht die Gefahren des Verstoßes gegen diese Regel. Im ersten Teil wird eine Beispielbibliothek, deren Typ, `MyClassWithReadOnlyArrayField`, zwei Felder (`grades` und `privateGrades`), die nicht sicher sind. Das Feld `grades` ist öffentlich und daher anfällig für jeden Aufrufer. Das Feld `privateGrades` ist privat, aber nach wie vor anfällig ist, da es sich bei Rückgabe an den Aufrufer von der `GetPrivateGrades` Methode. Die `securePrivateGrades` -Feld verfügbar gemacht wird, auf sichere Weise durch die `GetSecurePrivateGrades` Methode. Es ist für gute designmethoden führen als privat deklariert. Der zweite Teil enthält Code, der in gespeicherten Werte ändert die `grades` und `privateGrades` Member.

 Im folgenden Beispiel wird die Beispiel-Klassenbibliothek angezeigt.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Beispiel
 Der folgende Code verwendet die Beispiel-Klassenbibliothek, um schreibgeschütztes Array von Sicherheitsproblemen zu veranschaulichen.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 Die Ausgabe dieses Beispielcodes ist:

 **Vor Manipulationen: Klassen: 90, 90, 90 Private Grade: 90, 90, 90 sichere Grade, 90, 90, 90**
**nach Manipulationen: Klassen: 90, 555, 90 Private Grade: 90, 555, 90 secure Grade, 90, 90, 90**
## <a name="see-also"></a>Siehe auch
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
