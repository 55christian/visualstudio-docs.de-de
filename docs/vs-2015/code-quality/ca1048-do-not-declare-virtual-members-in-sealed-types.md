---
title: 'CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 36ee787ca9762766f8c563ab4b5081ee47355a56
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535354"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ ist versiegelt und deklariert eine Methode, die sowohl `virtual` (`Overridable` in Visual Basic) und nicht. Diese Regel meldet keine Verstöße für Delegattypen, die diesem Muster folgen müssen.

## <a name="rule-description"></a>Regelbeschreibung
 Typen deklarieren Methoden als virtuell, damit erbende Typen die Implementierung der virtuellen Methode überschreiben können. Sie können nicht per Definition aus einem versiegelten Typ eine virtuelle Methode für einen versiegelten Typ bedeutungslos erben.

 Die Visual Basic .NET und c#-Compiler gestatten keine Typen, die gegen diese Regel verstoßen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die Methode nicht virtuell, oder ändern Sie den Typ geerbt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Verlassen den Typ im aktuellen Zustand kann dazu führen, dass Wartungsprobleme und bietet keine Vorteile.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual/cpp/FxCop.Design.SealedVirtual.cpp#1)]
