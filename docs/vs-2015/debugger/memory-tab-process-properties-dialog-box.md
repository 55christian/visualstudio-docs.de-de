---
title: Registerkarte "Arbeitsspeicher", im Dialogfeld "Eigenschaften" Process | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b70c5a982da866cbeb9e9907859ad4d270d79bd9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957661"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Registerkarte "Arbeitsspeicher", Dialogfeld "Prozesseigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden der **Arbeitsspeicher** Tab, um zu zeigen, wie ein Prozess Arbeitsspeicher verwendet. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), verschieben Sie den Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **Arbeitsspeicher** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Virtuelle Bytes**|Die aktuelle Größe (in Bytes) des virtuellen Adressraums des Prozesses verwendet. Die Verwendung des virtuellen Adressraums impliziert nicht notwendigerweise entsprechende Verwendung von Datenträger- oder Hauptspeicherseiten. Allerdings virtuelle Raum ist begrenzt, und mit viel möglicherweise eingeschränkt des Prozesses, Bibliotheken zu laden.|  
|**Virtuelle Bytes max.**|Die maximale Anzahl von Bytes des virtuellen Adressraums des Prozesses wurde zu jedem Zeitpunkt verwendet.|  
|**Arbeitssatz**|Der Satz von Speicherseiten vor kurzem von den Threads im Prozess. Wenn der freier Speicher des Computers oberhalb des Schwellenwerts ist, sind Seiten in den Workingsets eines Prozesses übrig, auch wenn sie nicht verwendet werden. Wenn freier Speicher unter einen bestimmten Schwellenwert fällt, werden Seiten aus den Arbeitsseiten entfernt. Wenn sie benötigt werden, werden sie wieder in die Workingsets zurückverschoben vor dem Verlassen des Hauptspeichers.|  
|**Arbeitssatz max.**|Die maximale Anzahl von Seiten im Workingset dieses Prozesses zu jedem Zeitpunkt.|  
|**Auslagerbare Poolbytes**|Die aktuelle Größe des ausgelagerten Pools, die vom Prozess belegt wird. Auslagerungspool ist ein System-Speicherbereich, in denen Komponenten des Betriebssystems Speicherplatz abrufen können, während sie Ihre Aufgaben erledigen. Auslagerungspool-Seiten können nicht in die Auslagerungsdatei, wenn das System für einen längeren Zeitraum nicht auf Sie zugreifen ausgelagert werden.|  
|**Nicht auslagerbare Poolbytes**|Die aktuelle Anzahl der Bytes im nicht ausgelagerten Pools durch den Prozess zugeordnet. Der nicht ausgelagerte Pool ist eine System-Speicherbereich, in dem Speicherplatz von Betriebssystemkomponenten erworben wird, wie sie Ihre Aufgaben erledigen. Seiten des nicht ausgelagerten Pools können nicht in die Auslagerungsdatei ausgelagert werden; Sie bleiben im Hauptspeicher, solange sie zugeordnet sind.|  
|**Private Bytes**|Die aktuelle Anzahl der Bytes, die in die diesem Prozess reserviert hat, kann nicht für andere Prozesse freigegeben werden.|  
|**Freie Bytes**|Der insgesamt nicht verwendete virtuelle Adressraum dieses Prozesses.|  
|**Reservierte Bytes**|Die Gesamtmenge des virtuellen Arbeitsspeichers, die von diesem Prozess zur künftigen Verwendung reserviert.|  
|**Freie Bytes des Images**|Die Menge des virtuellen Adressraums, die noch nicht verwendet oder von Images in diesem Prozess reserviert werden soll.|  
|**Reservierte Bytes des Images**|Die Summe der virtuellen Speichers durch Bilder, die innerhalb dieses Prozesses ausgeführt.|
