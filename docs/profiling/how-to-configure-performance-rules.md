---
title: 'Vorgehensweise: Konfigurieren von Leistungsregeln | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7387cc54e96aec4deea6a65875f693d704d51859
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973967"
---
# <a name="how-to-configure-performance-rules"></a>Vorgehensweise: Konfigurieren von Leistungsregeln
Die Leistungswarnungen der Profilerstellungstools von Visual Studio deuten auf Probleme in einer mit einem Profil versehenen Anwendung hin, die die Programmausführung verlangsamen können. Warnungen können auch anzeigen, dass Sie möglicherweise die Auflistungsmethoden ändern müssen, um nützlichere Daten zu erfassen. Leistungswarnungen werden automatisch in einer Profilerstellungssitzung generiert und im Fenster **Fehlerliste** angezeigt, wenn eine Datei mit Profilerstellungsdaten in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] geöffnet wird. Bestimmte Warnungen gelten unter Umständen nicht für die Szenarios, für die Sie sich interessieren, und einige Warnungen sind möglicherweise ungenau. Sie können Leistungswarnungen konfigurieren, um bestimmte Warnungen anzuzeigen oder auszublenden.

### <a name="to-configure-profiler-performance-warnings"></a>So konfigurieren Sie Leistungswarnungen des Profilers

1. Klicken Sie im Menü **Extras** auf **Optionen**.

2. Erweitern Sie **Leistungstools**, und klicken Sie dann auf **Regeln**.

3. Aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Warn-**ID** und dem Namen, um eine Warnung zu aktivieren oder zu deaktivieren.

4. Klicken Sie zum Angeben der Warnstufe einer Regel neben der Regel auf die Zelle **Aktion** und anschließend auf die Warnstufe.

    - **Deaktiviert**: Deaktiviert die Regel (entspricht dem Deaktivieren des Kontrollkästchens neben der Regel-ID).

    - **Warnung**: Zeigt die Regel als Warnung an.

    - **Fehler**: Hält die Profilerstellung an und zeigt die Regel als Fehler an.

    - **Informationen**: Zeigt die Regel lediglich als Information an.