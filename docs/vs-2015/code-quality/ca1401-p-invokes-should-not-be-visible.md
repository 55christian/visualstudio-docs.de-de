---
title: 'CA1401: P-Invokes sollten nicht sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee4afd777f46087a7497dbdf4734e4ced52f47d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200328"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes dürfen nicht sichtbar sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ hat die <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut (auch durch implementiert die `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Regelbeschreibung
 Mit markierte Methoden der <xref:System.Runtime.InteropServices.DllImportAttribute> Attribut (oder mithilfe von definierten Methoden den `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) Platform Invocation Services den Zugriff auf nicht verwalteten Code verwenden. Solche Methoden sollten nicht verfügbar gemacht werden. Halten diese Methoden, private oder interne, stellen Sie sicher, dass die Bibliothek verwendet werden kann, um Sicherheitsrichtlinien zu umgehen, dass der Aufrufer den Zugriff auf nicht verwalteten APIs, die sie andernfalls nicht aufrufen konnte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene der Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel deklariert eine Methode, die gegen diese Regel verstößt.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
