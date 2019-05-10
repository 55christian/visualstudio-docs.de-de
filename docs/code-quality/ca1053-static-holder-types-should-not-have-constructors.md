---
title: 'CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52f04355a266f87a039b8197675c2f5377b840ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388315"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen.

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder verschachtelter öffentlicher Typ deklariert nur statische Member und verfügt über einen öffentlichen oder geschützten Standardkonstruktor.

## <a name="rule-description"></a>Regelbeschreibung
 Der Konstruktor ist überflüssig, da zum Aufrufen statischer Member keine Instanz des Typs erforderlich ist. Darüber hinaus, da der Typ keine nicht statische Member, bietet erstellen Sie eine Instanz Zugriff auf Member des Typs keine.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Standardkonstruktor, oder stellen sie private.

> [!NOTE]
> Einige Compiler erstellen automatisch einen öffentlichen Standardkonstruktor, wenn der Typ keine Konstruktoren definiert ist. Ist dies der Fall bei Ihrem Typ, fügen Sie einen privaten Standardkonstruktor, um die Verletzung zu entfernen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Das Vorhandensein des Konstruktors legt nahe, dass der Typ nicht um einen statischen Typ ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt. Beachten Sie, dass kein Standardkonstruktor vorhanden, im Quellcode ist. Wenn dieser Code in eine Assembly kompiliert wird, wird der C#-Compiler einen Standardkonstruktor, einfügen, der gegen diese Regel verstoßen wird. Um dies zu korrigieren, deklarieren Sie einen privaten Konstruktor.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]