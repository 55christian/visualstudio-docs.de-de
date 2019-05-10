---
title: 'DA0011: Speicherintensive CompareTo-Funktionen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee5839e91e2205a98a38ed27823a26a4a127e1ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936586"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Speicherintensive CompareTo-Funktionen

|||
|-|-|
|Regel-ID|DA0011|
|Kategorie|.NET Framework-Verwendung|
|Profilerstellungsmethoden|Sampling<br /><br /> .NET-Arbeitsspeicher|
|Meldung|CompareTo-Funktionen dürfen nicht speicherintensiv sein und keinen Speicher belegen. Reduzieren Sie daher, wenn möglich, die Komplexität der CompareTo-Funktionen.|
|Regeltyp|Warnung|

## <a name="cause"></a>Ursache
 Die CompareTo-Methode des Typs ist aufwändig oder belegt Arbeitsspeicher.

## <a name="rule-description"></a>Regelbeschreibung
 CompareTo-Methoden sollten effizient sein und keinen Arbeitsspeicher zuordnen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Verringern Sie die Komplexität der CompareTo-Methode.