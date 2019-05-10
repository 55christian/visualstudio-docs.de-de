---
title: 'CA1504: Irreführende Feldnamen überprüfen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c58a0a27c11aea2954d4950b742a8928f98732e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546322"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Irreführende Feldnamen überprüfen.

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Der Name eines Instanzenfelds beginnt mit "S_" oder den Namen einer `static` (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Feld beginnt mit "M_".

## <a name="rule-description"></a>Regelbeschreibung
 Feldnamen, die mit "S_" beginnen, sind statische Daten von vielen Benutzern zugeordnet. Auf ähnliche Weise werden die Feldnamen, die mit "M_" beginnen (Member) Instanzdaten zugeordnet. Für Code einfacher zu verwalten sollten Namen in der Regel verwendeten Konventionen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie das Feld mit dem entsprechenden Präfix. Alternativ passen Sie das Feld mit dem aktuellen Suffix durch Hinzufügen oder Entfernen der `static` Modifizierer.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.