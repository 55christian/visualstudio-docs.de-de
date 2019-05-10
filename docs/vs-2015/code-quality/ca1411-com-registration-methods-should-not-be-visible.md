---
title: 'CA1411: COM-Registrierungsmethoden dürfen nicht sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a332139caec707c593614c7cf1b07733d533ac87
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959466"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: Die COM-Registrierungsmethoden dürfen nicht sichtbar sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode, die mit der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> Attribut ist als extern sichtbar.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn eine Assembly mit Component Object Model (COM) registriert ist, werden die Einträge in der Registrierung für jede in der Assembly für COM sichtbarer Typ hinzugefügt. Mit markierte Methoden der <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> und <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> Attribute werden aufgerufen, während der Registrierung und Aufhebung der Registrierung, um bei der Ausführung von Benutzercode, der spezifisch für die Registrierung/Aufhebung der Registrierung dieser Typen ist. Dieser Code sollte nicht außerhalb dieser Prozesse aufgerufen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Zugriff auf die Methode, die `private` oder `internal` (`Friend` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden, die die Regel verletzen.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1410: COM-Registrierungsmethoden müssen übereinstimmen.](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Registrieren von Assemblys bei COM](http://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (Assembly Registration-Tool)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
