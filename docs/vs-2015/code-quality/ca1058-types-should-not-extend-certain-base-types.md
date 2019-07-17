---
title: 'CA1058: Typen sollten bestimmte Basistypen nicht erweitern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1ce67a70b6cbe955ef13bf6475a672bcbb687d95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200449"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typen sollten bestimmte Basistypen nicht erweitern.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ erweitert bestimmte Basistypen. Diese Regel meldet derzeit Typen, die von der folgenden Typen abgeleitet werden:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung
 Für [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Version 1 wurde empfohlen, neue Ausnahmen von abzuleiten <xref:System.ApplicationException>. Die Empfehlung wurde geändert und neue Ausnahmen sollten abgeleitet <xref:System.Exception?displayProperty=fullName> oder eine ihrer Unterklassen in die <xref:System> Namespace.

 Erstellen Sie eine Unterklasse von nicht <xref:System.Xml.XmlDocument> sollten Sie eine XML-Ansicht der zugrunde liegenden Modell oder die Datenquelle zu erstellen.

### <a name="non-generic-collections"></a>Nicht generische Auflistungen
 Verwenden Sie und/oder Erweitern von generischen Auflistungen, wann immer möglich. Nicht generische Auflistungen in Ihrem Code können nicht erweitert werden, es sei denn, die Sie bereits geliefert haben.

 **Beispiele für die falsche Verwendung**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Beispiele für die richtige Verwendung**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, leiten Sie den Typ von einem unterschiedlichen Basistyp oder einer generischen Auflistung ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel für Verstöße zu <xref:System.ApplicationException>. Es ist sicherer, unterdrücken Sie eine Warnung dieser Regel Verstöße zu <xref:System.Xml.XmlDocument>. Es ist sicher, um eine Warnung über eine nicht generische Auflistung zu unterdrücken, wenn der Code zuvor veröffentlicht wurden.
