---
title: 'CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6be4dbc8ebb8e0cd401716e9ecf913045e0996f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958238"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Überschreibungslinkaufrufe sollten mit der Basis identisch sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ überschreibt eine Methode oder eine Schnittstelle implementiert und verfügt nicht über die gleichen [Verknüpfungsaufrufe](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) wie die Schnittstelle oder eine virtuelle Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Durch diese Regel wird eine Methode mit ihrer Basismethode verglichen. Bei dieser handelt es sich entweder um eine Schnittstelle oder um eine virtuelle Methode in einem anderen Typ. Anschließend werden die Linkaufruf mit denen der Schnittstelle bzw. virtuellen Methode verglichen. Ein Verstoß wird gemeldet, wenn die-Methode oder die Basismethode einen Linkaufruf enthält, und das andere nicht.

 Wenn diese Regel verletzt wird, kann ein böswilliger Aufrufer den Linkaufruf umgehen, lediglich durch Aufruf der ungesicherten Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie den gleichen Linkaufruf auf die Überschreibungsmethode oder die Implementierung aus. Wenn dies nicht möglich ist, markieren Sie die Methode mit einer vollständigen Anforderung aus, oder entfernen Sie das Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt verschiedene Verstöße gegen diese Regel.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>Siehe auch
 [Sichern Sie die Richtlinien für das Codieren](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Linkaufrufe](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
