---
title: Ereignisbeschreibungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7267011c61a3b43c76db80a758a86f1af1dd228b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315365"
---
# <a name="event-descriptions"></a>Ereignisbeschreibungen
Jeder Ereignistyp hat einen bestimmten Zweck.

## <a name="events-and-the-reasons-for-their-use"></a>Ereignisse und die Gründe für deren Verwendung

|event|Beschreibung|
|-----------|-----------------|
|Aktivieren der Dokumentereignisse|Treten Sie auf, wenn die Debug-Engine (DE) möchte, die IDE dass zu öffnen oder ein Dokument in den Vordergrund zu bringen.|
|Haltepunkt gebunden oder Haltepunkt-Fehlerereignisse|Gesendet, wenn ein Haltepunkt gebunden ist oder wenn ein Haltepunkt kann nicht gebunden werden und ein Fehler zurückgegeben.|
|Ungebundene Haltepunktereignisse|Treten Sie auf, wenn Sie ein gebundener Haltepunkt aus Code hebt die Bindung.|
|Ereignisse können beendet werden.|Gesendet, um die IDE zu bestimmen, ob der Benutzer an einem angegebenen Punkt im Code beenden möchten.|
|Haltepunktereignisse|Treten Sie auf, wenn ein Code oder Daten-Haltepunkt erreicht wird.|
|Dokument-Text-Ereignisse|Treten Sie auf, wenn der Text in einem Dokument geändert wird. Diese Ereignisse werden nicht gesendet, über die `IDebugEventCallBack2::Event` Methode.|
|-Engine-Ereignisse erstellen.|Gesendet, wenn ein Modul zum ersten Mal erstellt wird.|
|Punktereignisse Eintrag|Gesendet, wenn die zu debuggende Programm wird der Initialisierungscode ausgeführt und der Einstiegspunkt für die ersten Benutzer erreicht.|
|Ausnahmeereignisse|Gesendet, wenn ein ausgeführtes Programm eine Ausnahme trifft.|
|Ereignisse durch Abschluss der Ausdruck Auswertung|Gesendet, wenn asynchrone ausdrucksauswertung abgeschlossen ist.|
|Symbol-Events suchen|Gesendet, wenn die DE der Benutzer zum Suchen von Symbolen für ein Modul aufgefordert muss.|
|Laden Sie die Ereignisse zum Abschluss|Gesendet von nur auf, wenn die Last zu startendes Programm abgeschlossen ist und der erste Code in das Programm ausgeführt wird.|
|Nachrichtenereignisse|Gesendet, wenn Nachrichten an Benutzer gesendet werden.|
|Ladeereignisse für Module|Gesendet, wenn ein neues Modul geladen oder entladen wird.|
|Ausgabeereignisse-Zeichenfolge|Gesendet, wenn das Programm-Debug-Ausgabe schreibt.|
|Erstellen und Zerstören von Ereignissen|Gesendet, um die Erstellung oder Zerstörung von Prozessen, Programme, Eigenschaften, Sitzungen und Threads anzukündigen, damit Visual Studio-IDE den Status der gedebuggten Programme mitverfolgen können.|
|Ereignisse zum Abschluss von Schritt|Gesendet, wenn ein Schritt abgeschlossen ist.|
|Thread-Name-Change-Ereignissen|Gesendet, wenn der Benutzer den Namen eines Threads ändert.|
|Ereignisse des Programms Namen ändern|Gesendet, wenn der Benutzer den Namen eines Programms ändert.|

## <a name="see-also"></a>Siehe auch
- [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)