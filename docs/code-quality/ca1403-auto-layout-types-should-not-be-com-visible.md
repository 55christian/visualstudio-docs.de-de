---
title: 'CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef7b693a881aaa1457004c84968ebc80936fc2b2
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714848"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein.

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Werttyp der Component Object Model (COM) sichtbar ist mit markiert die <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> -Attributsatz auf <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung

<xref:System.Runtime.InteropServices.LayoutKind> Layouttypen werden von der common Language Runtime verwaltet. Das Layout dieser Typen kann zwischen den Versionen von .NET ändern, der COM-Clients unterbricht, die ein bestimmtes Layout erwarten. Wenn die <xref:System.Runtime.InteropServices.StructLayoutAttribute> Attribut nicht angegeben ist, geben Sie die C#-, Visual Basic und C++-Compiler [LayoutKind.Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) für Werttypen.

Sofern nicht anders markiert ist, werden alle öffentliche, nicht generischen Typen für COM sichtbar, und alle nicht öffentliche und generische Typen sind für COM nicht sichtbar Um falsch positive Ergebnisse zu reduzieren, erfordert mit dieser Regel jedoch die COM-Sichtbarkeit des Typs explizit angegeben werden. Die übergeordnete Assembly muss markiert sein, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> festgelegt `false` und der Typ markiert werden muss, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt `true`.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert von der <xref:System.Runtime.InteropServices.StructLayoutAttribute> Attribut [mich LayoutKind.explizit zuwenden musste](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) oder [LayoutKind.Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), oder ändern Sie den Typ für COM nicht sichtbar

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein Typ, der gegen die Regel verstößt und ein Typ, der die Regel erfüllt.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Siehe auch

- [Qualifizieren von .NET Datentypen für die interoperation](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilität mit nicht verwaltetem code](/dotnet/framework/interop/index)