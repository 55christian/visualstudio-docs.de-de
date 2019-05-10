---
title: 'CA2134: Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67114c20a7fcf5e8ff01773d8777b23d3caf3d91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542323"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Methoden müssen beim Überschreiben von Basismethoden eine konsistente Transparenz wahren.

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Diese Regel wird ausgelöst, wenn eine Methode mit markiert die <xref:System.Security.SecurityCriticalAttribute> überschreibt eine Methode, die transparent oder mit der <xref:System.Security.SecuritySafeCriticalAttribute>. Die Regel wird auch ausgelöst, wenn eine Methode, die transparent oder mit der <xref:System.Security.SecuritySafeCriticalAttribute> überschreibt eine Methode, die mit einem <xref:System.Security.SecurityCriticalAttribute>.

 Die Regel wird angewendet, wenn eine virtuelle Methode überschrieben oder eine Schnittstelle implementiert wird.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird beim Versuch, ändern Sie den Security Zugriff auf eine Methode, die sich weiter entlang der Vererbungskette ausgelöst. Beispielsweise ist eine virtuelle Methode in einer Basisklasse transparenten oder sicherheitsrelevanten, muss dann die abgeleitete Klasse es mit einer transparenten oder sicherheitsrelevanten-Methode überschreiben. Im Gegensatz dazu ist das virtuelle sicherheitskritisch, muss die abgeleitete Klasse sie mit eine wichtige Methode überschreiben. Das gleiche gilt für die Schnittstellenmethoden implementieren.

 Transparenzregeln werden erzwungen, wenn der Code JIT-Kompilierung statt zur Laufzeit ist, damit, dass die transparenzberechnung keine dynamische Typinformationen. Aus diesem Grund muss das Ergebnis der Berechnung der Transparenz ausschließlich über den statischen Typen wird der JIT-kompiliert, unabhängig vom dynamischen Typ nicht bestimmt werden können.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Transparenz der Methode, die eine virtuelle Methode überschreiben oder Implementieren einer Schnittstelle, um die Transparenz des virtuellen oder Schnittstellenmethode entsprechen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnungen, die von dieser Regel. Verstöße gegen diese Regel führt in einer Laufzeit <xref:System.TypeLoadException> für Assemblys, die Transparenz der Ebene 2 zu verwenden.

## <a name="examples"></a>Beispiele

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>Siehe auch
 [Sicherheitstransparenter Code, Ebene 2](/dotnet/framework/misc/security-transparent-code-level-2)