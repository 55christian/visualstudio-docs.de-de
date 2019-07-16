---
title: Legen Sie die Regel für verwaltete Mindestregeln für verwalteten Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fbbbdf8a1ece9a57d0216a6c9b59ac9d2a8ea474
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142219"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Regelsatz für verwaltete Mindestregeln für verwalteten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die verwaltete Mindestregeln konzentrieren sich auf die kritischsten Probleme in Ihrem Code, einschließlich potenzieller Sicherheitslücken, Anwendungsabstürze und anderen wichtigen Logik- und Designfehlern. Sie sollten diesen Regelsatz in alle benutzerdefinierten Regelsätze einbinden, die Sie für Ihre Projekte erstellen.  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typen, die löschbare Felder besitzen, müssen gelöscht werden können.|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Leere Finalizer entfernen.|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Verwerfbare Felder verwerfen.|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.|
