---
title: 'CA1051: sichtbare Instanzfelder nicht deklarieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 41332ab7d729f7b2187ccace6b05fe2d17763a0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672517"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Sichtbare Instanzfelder nicht deklarieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ verfügt über ein extern sichtbares Instanzfeld.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Feld sollte primär als Implementierungsdetail verwendet werden. Felder sollten `private` oder `internal` sein und mithilfe von Eigenschaften verfügbar gemacht werden. Es ist so einfach, auf eine Eigenschaft zuzugreifen, da Sie auf ein Feld zugreifen kann. der Code in den Accessoren einer Eigenschaft kann sich ändern, wenn die Funktionen des Typs erweitert werden, ohne dass wichtige Änderungen eingeführt werden. Eigenschaften, die nur den Wert eines privaten oder internen Felds zurückgeben, werden für die Ausführung mit dem Zugriff auf ein Feld optimiert. sehr wenig Leistungsgewinn ist mit der Verwendung extern sichtbarer Felder für Eigenschaften verknüpft.

 Extern sichtbar bezieht sich auf die Barrierefreiheits Stufen `public`, `protected` und `protected internal` (`Public`, `Protected` und `Protected Friend` Visual Basic).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, machen Sie das Feld `private` oder `internal`, und machen Sie es mithilfe einer extern sichtbaren Eigenschaft verfügbar.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Extern sichtbare Felder bieten keine Vorteile, die für Eigenschaften nicht verfügbar sind. Darüber hinaus können öffentliche Felder nicht durch [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)Aufrufe geschützt werden. Weitere Informationen finden Sie unter [CA2112: gesicherte Typen sollten keine Felder](../code-quality/ca2112-secured-types-should-not-expose-fields.md)verfügbar machen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ (`BadPublicInstanceFields`), der gegen diese Regel verstößt. `GoodPublicInstanceFields` den korrigierten Code anzeigt.

 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesPublicInstanceFields/cs/FxCop.Design.TypesPublicInstanceFields.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Siehe auch
 [Link Aufrufe](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
