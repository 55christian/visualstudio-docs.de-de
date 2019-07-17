---
title: 'CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 11bd1668e4ab599461d3619c63cd3c9732a05b4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142689"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode erfordert eine <xref:System.Security.Permissions.SecurityAction> oder andere sicherheitsanforderung.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird für transparente Methoden ausgelöst, die einen Zugriff durch LinkDemands erfordern. Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Da sind transparente Methoden, die Sicherheit neutral sein sollen, sollten sie keine sicherheitsentscheidungen vornehmen. Darüber hinaus sollten sichere Kritischer Code, der sicherheitsentscheidungen zu treffen, nicht auf transparentem Code bereits eine solche Entscheidung getroffen haben verlassen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Linkaufruf für die transparente Methode aus, oder markieren Sie die Methode mit <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, wenn sie Sicherheit ausgeführt werden überprüft, wie z. B. sicherheitsanforderungen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel die Regel für die Methode wird ausgelöst, da die Methode transparent ist und durch LinkDemand gekennzeichnet ist <xref:System.Security.PermissionSet> , enthält ein <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 Unterdrücken Sie keine Warnung dieser Regel.
