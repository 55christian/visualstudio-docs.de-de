---
title: 'CA2137: Transparente Methoden dürfen nur überprüfbare IL enthalten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2803e220cd38bc03efa464bbe857ab41fff1ea52
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696229"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Transparente Methoden dürfen nur überprüfbare IL enthalten.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode enthält nicht überprüfbaren Code oder gibt einen Typ nach Verweis zurück.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird für Versuche durch sicherheitstransparenten Code ausgelöst, nicht überprüfbare MSIL (Microsoft Intermediate Language) auszuführen. Die Regel enthält jedoch kein vollständiges IL-Prüfmodul und verwendet stattdessen Heuristik, um die meisten Verletzungen der MSIL-Überprüfung abzufangen.

 Um sicherzustellen, dass der Code nur überprüfbare MSIL enthält, führen Sie [Peverify.exe (PEVerify-Tool)](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) auf die Assembly. Führen Sie PEVerify mit der **/ transparent** Option aus, die die Ausgabe nur nicht überprüfbare transparente Methoden beschränkt, die einen Fehler verursachen würden. Wenn die / Option "transparent" nicht verwendet wird, überprüft PEVerify auch wichtige Methoden, die nicht überprüfbaren Code enthalten dürfen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode mit dem <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, oder entfernen Sie die nicht überprüfbaren Code.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die Methode in diesem Beispiel wird nicht überprüfbaren Code verwendet und sollte mit markiert werden die <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
