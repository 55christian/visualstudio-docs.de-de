---
title: 'CA1700: Enum-Werte nicht den Namen &#39;reserviert&#39; | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a5446d21b51f57b4a614e8931b154654bee99cd2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189262"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Enum-Werte nicht den Namen &#39;reserviert&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Enumerationsmembers enthält das Wort "reserviert".

## <a name="rule-description"></a>Regelbeschreibung
 Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen. Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung. Sie sollten nicht erwarten, dass Benutzer, um ein Element zu ignorieren, nur weil der Name "reservierte" enthält, noch können Sie sich auf Benutzer zu lesen, oder halten Sie sich die Dokumentation an verlassen. Darüber hinaus da reservierte Elemente im Objektbrowser und intelligente integrierten entwicklungsumgebungen angezeigt werden, können sie Verwirrung darüber, welche Mitglieder tatsächlich verwendet werden.

 Fügen Sie statt eines reservierten Members, auf die Enumeration in der zukünftigen Version ein neues Mitglied hinzu. In den meisten Fällen ist das Hinzufügen des neuen Mitglieds nicht über eine bedeutende Änderung, solange die Hinzufügung nicht die Werte von der ursprünglichen Elemente ändern kann.

 In einer begrenzten Anzahl von Fällen ist das Hinzufügen eines Elements eine unterbrechende Änderung, auch wenn der ursprünglichen Elemente auf ihre ursprünglichen Werte erhalten bleiben. Das neue Element kann nicht in erster Linie von vorhandenen Codepfaden zurückgegeben werden, ohne unterbrechende Aufrufer, mit denen eine `switch` (`Select` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)])-Anweisung für den Rückgabewert, umfasst die gesamte Memberliste und, die eine Ausnahme in, der der Standardfall. Ein weiteres Problem ist, dass der Clientcode keine Änderungen im Verhalten von Reflektionsmethoden wie z. B. behandelt <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. Entsprechend ist, wenn das neue Element wurde aus der vorhandenen Methoden zurückgegeben werden, oder eine bekannte Anwendungsinkompatibilität tritt auf, aufgrund schlechter, die einzige geschützte Lösung zu:

1. Fügen Sie eine neue Enumeration, die die ursprünglichen und neuen Elemente enthält.

2. Markieren Sie die ursprüngliche Enumeration mit den <xref:System.ObsoleteAttribute?displayProperty=fullName> Attribut.

   Führen Sie dieselbe Verfahren für extern sichtbare Typen oder Member, die die ursprüngliche Enumeration verfügbar zu machen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie, oder benennen Sie den Member.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, unterdrücken eine Warnung dieser Regel für ein Element, das derzeit verwendet wird, oder für Bibliotheken, die bereits veröffentlicht haben.

## <a name="related-rules"></a>Verwandte Regeln
 [CA2217: Nicht Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: Führen Sie keine Präfixe für Enumerationswerte mit Typnamen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: -Enumerationen sollten NULL-Wert aufweisen.](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
