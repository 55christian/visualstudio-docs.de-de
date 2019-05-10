---
title: Codeanalyse für verwalteten Code (Warnungen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 237091c4304b6d6fef90197d503f84fe86c12b9e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958460"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Warnungen bei der Analyse von verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Tool für die Analyse von verwaltetem Code stellt Warnungen über Regelverletzungen in verwalteten Codebibliotheken bereit. Die Warnungen werden in Regelbereichen, etwa Design, Lokalisierung, Leistung und Sicherheit, angeordnet. Jede Warnung steht für die Verletzung einer Analyseregel für verwalteten Code. Dieser Abschnitt enthält ausführliche Diskussionen und Beispiele für jede Warnung zur Analyse von verwaltetem Code.  
  
 Die folgende Tabelle zeigt die Art der Informationen, die für jede Warnung bereitgestellt werden.  
  
|Element|Beschreibung|  
|----------|-----------------|  
|Typ|TypeName für die Regel.|  
|CheckId|Eindeutiger Bezeichner für die Regel. CheckId und Category werden für die Unterdrückung einer Warnung im Quellcode verwendet.|  
|Kategorie|Kategorie der Warnung.|  
|Unterbrechende Änderung|Gibt an, ob die Lösung einer Verletzung der Regel eine unterbrechende Änderung ist. Unterbrechende Änderung bedeutet, dass eine Assembly, die eine Abhängigkeit von dem Ziel aufweist, das die Verletzung verursacht hat, nicht mit der neuen behobenen Version erneut kompiliert wird oder aufgrund der Änderung zur Laufzeit möglicherweise fehlschlägt. Wenn mehrere Lösungen verfügbar sind und mindestens eine Lösung eine unterbrechende Änderung und eine Lösung keine unterbrechende Änderung darstellt, werden 'Breaking' und 'Non Breaking' angegeben.|  
|Ursache|Der spezielle verwaltete Code, aufgrund dessen die Regel eine Warnung generiert.|  
|Beschreibung|Erläutert die Probleme, die zur Warnung geführt haben.|  
|Behandeln von Verstößen|Erläutert, wie der Quellcode geändert werden kann, damit die Regel eingehalten wird und sie keine Warnung mehr generiert.|  
|Wann sollten Warnungen unterdrückt werden?|Beschreibt, wann es sicher ist, eine Warnung der Regel zu unterdrücken.|  
|Beispielcode|Beispiele, die die Regel verletzen, und korrigierte Beispiele, die die Regel erfüllen.|  
|Zugehörige Warnungen|Zugehörige Warnungen.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|||  
|-|-|  
|[Warnungen nach CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Listet alle Warnungen nach CheckId auf|  
|[Kryptografiewarnungen](../code-quality/cryptography-warnings.md)|Warnungen, die sicherere Bibliotheken und Anwendungen durch die korrekte Verwendung von Kryptografie unterstützen.|  
|[Entwurfswarnungen](../code-quality/design-warnings.md)|Warnungen, die ein korrektes Bibliotheksdesign entsprechend den [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] -Entwurfsrichtlinien unterstützen.|  
|[Globalisierungswarnungen](../code-quality/globalization-warnings.md)|Warnungen, die global verwendbare Bibliotheken und Anwendungen unterstützen.|  
|[Interoperabilitätswarnungen](../code-quality/interoperability-warnings.md)|Warnungen, die die Interaktion mit COM-Clients unterstützen.|  
|[Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md)|Warnungen, die die Bibliotheks- und Anwendungswartung unterstützen.|  
|[Mobility Warnings](../code-quality/mobility-warnings.md)|Warnungen, die einen effizienten Stromverbrauch unterstützen.|  
|[Benennungswarnungen](../code-quality/naming-warnings.md)|Warnungen, die die Einhaltung der Namenskonventionen der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] -Entwurfsrichtlinien unterstützen.|  
|[Leistungswarnungen](../code-quality/performance-warnings.md)|Warnungen, die leistungsstarke Bibliotheken und Anwendungen unterstützen.|  
|[Portability Warnings](../code-quality/portability-warnings.md)|Warnungen, die Portabilität auf verschiedenen Plattformen unterstützen.|  
|[Zuverlässigkeitswarnungen](../code-quality/reliability-warnings.md)|Warnungen, die Bibliotheks- und Anwendungszuverlässigkeit unterstützen, wie z. B. die richtige Speicher- und Threadverwendung.|  
|[Sicherheitswarnungen](../code-quality/security-warnings.md)|Warnungen, die sicherere Bibliotheken und Anwendungen unterstützen.|  
|[Verwendungswarnungen](../code-quality/usage-warnings.md)|Warnungen, die die angemessene Verwendung von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]unterstützen.|  
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|Fehler die auftreten, wenn die Codeanalyserichtlinie beim Einchecken nicht erfüllt wird.|
