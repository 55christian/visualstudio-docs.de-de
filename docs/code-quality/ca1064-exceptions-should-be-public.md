---
title: 'CA1064: Ausnahmen sollten öffentlich sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8196d4c48bfb93735b62c6f24cb08ec462e64c91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788580"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Ausnahmen sollten öffentlich sein.

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine nicht öffentliche Ausnahme leitet sich direkt von <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>.

## <a name="rule-description"></a>Regelbeschreibung
 Eine interne Ausnahme ist nur innerhalb ihres eigenen internen Bereichs sichtbar. Nachdem die Ausnahme den internen Bereich verlassen hat, kann nur die Basisausnahme zum Abfangen der Ausnahme verwendet werden. Wenn die interne Ausnahme von geerbt wird <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>, der externe Code müssen nicht über genügend Informationen zur Vorgehensweise mit der Ausnahme.

 Aber wenn der Code eine öffentliche Ausnahme, die später als Grundlage für eine interne Ausnahme verwendet wird aufweist, ist es sinnvoll, wird davon ausgegangen, dass der Code noch weiter, etwas intelligent mit der Basis-Ausnahme kann. Die öffentliche Ausnahme müssen mehr Informationen als die vom bereitgestellten <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wandeln Sie die Ausnahme oder die interne Ausnahme von einer öffentlichen Ausnahme, die nicht ableiten <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Meldung von dieser Regel, wenn Sie in allen Fällen sicher sind, dass die private Ausnahme innerhalb ihres eigenen internen Bereichs abgefangen wird.

## <a name="example"></a>Beispiel
 Mit dieser Regel wird für das erste Beispielmethode, ausgelöst (FirstCustomException) ausgelöst, daran, dass die Exception-Klasse wird direkt von einer Ausnahme abgeleitet und interne. Die Regel wird nicht für die SecondCustomException-Klasse ausgelöst werden, da auch die Klasse auch direkt aus einer Ausnahme abgeleitet wird, die Klasse als öffentlich deklariert ist. Die dritte Klasse auch löst nicht die Regel, da er nicht direkt von abgeleitet ist <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, oder <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
