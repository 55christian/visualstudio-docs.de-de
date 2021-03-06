---
title: 'CA1308: Zeichen folgen in Großbuchstaben normalisieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dfe8495184bf4daadb3bf8899ee2857a9743c842
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661391"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Zeichenfolgen in Großbuchstaben normalisieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategorie|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Vorgang normalisiert eine Zeichenfolge in Kleinbuchstaben.

## <a name="rule-description"></a>Regelbeschreibung
 Zeichenfolgen sollten in Großschreibung normalisiert werden. Bei einer kleinen Gruppe von Zeichen, die in Kleinbuchstaben konvertiert werden, kann kein Roundtrip durchlaufen werden. Ein Roundtrip bedeutet, dass die Zeichen von einem Gebiets Schema in ein anderes Gebiets Schema konvertiert werden sollen, das Zeichendaten unterschiedlich darstellt, und dann die ursprünglichen Zeichen aus den konvertierten Zeichen genau abzurufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Änderungs Vorgänge, bei denen Zeichen folgen in Kleinbuchstaben konvertiert werden, sodass die Zeichen folgen stattdessen in Großbuchstaben konvertiert werden. Ändern Sie beispielsweise `String.ToLower(CultureInfo.InvariantCulture)` zu `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnmeldung zu unterdrücken, wenn Sie keine Sicherheits Entscheidung basierend auf dem Ergebnis treffen (z. b. bei der Anzeige in der Benutzeroberfläche).

## <a name="see-also"></a>Siehe auch
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md)
