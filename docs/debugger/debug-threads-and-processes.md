---
title: Tools zum Debuggen von Threads und Prozessen | Microsoft-Dokumentation
ms.date: 04/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcdaf083462b75485449cae05894681e2bb5c900
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738377"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Tools zum Debuggen von Threads und Prozessen in Visual Studio
*Threads* und *Prozesse* sind verwandte Konzepte der Informatik. Beide stellen Folgen von Anweisungen dar, die in einer bestimmten Reihenfolge ausgeführt werden müssen. Anweisungen von verschiedenen Threads oder Prozessen können aber parallel ausgeführt werden.

 Prozesse werden im Betriebssystem verwaltet und entsprechen dem, was Benutzer als Programme oder Anwendungen sehen. Ein Thread hingegen wird von einem Prozess verwaltet. Aus diesem Grund werden Threads gelegentlich als *Lightweightprozesse* bezeichnet. Jeder Prozess besteht aus einem oder mehreren Threads.

 Die Möglichkeit, mehrere Prozesse auszuführen, versetzt einen Computer in die Lage, mehr als eine Aufgabe gleichzeitig auszuführen. Das Vorhandensein mehrerer Threads versetzt einen Prozess in die Lage, Arbeiten so aufzuteilen, dass sie parallel ausgeführt werden können. Auf einem Computer mit Multiprozessoren können Prozesse oder Threads auf verschiedenen Prozessoren ausgeführt werden. Dies ermöglicht eine echte Parallelverarbeitung.

 Echte Parallelverarbeitung ist nicht immer möglich. Threads müssen manchmal synchronisiert werden. Ein Thread muss möglicherweise auf das Ergebnis eines anderen Threads warten, oder ein Thread benötigt exklusiven Zugriff auf eine Ressource, die von einem anderen Thread verwendet wird. Synchronisierungsprobleme sind eine häufige Ursache von Programmfehlern in Multithreadanwendungen. Es kann passieren, dass Threads auf eine Ressource warten, die nie verfügbar wird. Dies führt zu einem Zustand, der *Deadlock* genannt wird.

 Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger stellt leistungsstarke und benutzerfreundliche Tools zum Debuggen von Threads und Prozessen bereit.

## <a name="tools-and-features"></a>Tools und Features
Die Tools, die Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwenden müssen, hängen davon ab, welche Art von Code Sie debuggen möchten:

- Für Prozesse sind die primären Tools das Dialogfeld **an den Prozess anhängen** , das Fenster **Prozesse** und die Symbolleiste **Debugspeicherort** .

- Die wichtigsten Tools für das Debuggen von Threads sind das Fenster **Threads** , Thread Markierungen in Quell Fenstern, **parallele Stapel** Fenster, **parallele Überwachungs** Fenster und die Symbolleiste **Debugspeicherort** .

- Für Code, in dem die <xref:System.Threading.Tasks.Task> im [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)verwendet wird, werden die [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/) (nativer Code), die primären Tools zum Debuggen von Multithreadanwendungen, das **parallele Stapel** Fenster, die **parallele Überwachung** Fenster und **Aufgaben** Fenster (das **Aufgaben** Fenster unterstützt auch das JavaScript Promise-Objekt).

- Zum Debuggen von Threads auf der GPU ist das primäre Tool die **GPU-Thread** Fenster.

  In der folgenden Tabelle sind die verfügbaren Informationen und die an jeder Stelle möglichen Aktionen aufgeführt:

|Benutzeroberfläche|Verfügbare Informationen|Ausführbare Aktionen|
|--------------------|---------------------------|-----------------------------|
|Dialogfeld **An den Prozess anhängen**|Verfügbare Prozesse, an die angehängt werden kann:<br /><br /> –   Prozessname (.exe)<br />–   Prozess-ID-Nummer<br />–   Menüleistentitel<br />–   Typ (Managed v4.0, Managed v2.0, v1.1, v1.0, x86, x64, IA64)<br />–   Benutzername (Kontoname)<br />–   Sitzungsnummer|Auswählen eines Prozesses, an den angehängt werden soll<br /><br /> Auswählen eines Remotecomputers<br /><br /> Ändern des Transporttyps für die Verbindung mit Remotecomputern|
|Fenster **Prozesse**|Angehängte Prozesse:<br /><br /> –   Prozessname<br />–   Prozess-ID-Nummer<br />–   Pfad zur EXE-Datei des Prozesses<br />–   Menüleistentitel<br />–   Zustand (Unterbrechen, Aktiv)<br />–   Debuggen (nativ, verwaltet usw.)<br />–   Transporttyp (standardmäßig, nativ ohne Authentifizierung)<br />–   Transportqualifizierer (Remotecomputer)|Tools:<br /><br /> –   Anfügen<br />–   Trennen<br />–   Beenden<br /><br /> Kontextmenü:<br /><br /> –   Anfügen<br />–   Trennen<br />–   Nach Beenden des Debuggings trennen<br />–   Beenden|
|Fenster **Threads**|Threads in aktuellem Prozess:<br /><br /> –   Thread-ID<br />–   Verwaltete ID<br />–   Kategorie (Hauptthread, Benutzeroberflächenthread, Remoteprozeduraufruf-Handler oder Arbeitsthread)<br />–   Threadname<br />–   Ort, an dem der Thread erstellt wird<br />–   Priorität<br />–   Affinitätsmaske<br />–   Angehaltene Anzahl<br />–   Prozessname<br />–   Kennzeichenindikator<br />–   Angehaltener Indikator|Tools:<br /><br /> –   Suchen<br />–   Aufrufliste durchsuchen<br />–   Nur eigenen Code kennzeichnen<br />–   Benutzerdefinierte Modulauswahl kennzeichnen<br />–   Gruppieren nach<br />–   Spalten<br />–   Aufruflisten aufklappen/zuklappen<br />–   Gruppen aufklappen/zuklappen<br />–   Threads einfrieren/reaktivieren<br /><br /> Kontextmenü:<br /><br /> –   Threads in Quelle anzeigen<br />–   Zu Thread wechseln<br />–   Ausgeführten Thread sperren<br />–   Eingefrorenen Thread reaktivieren<br />–   Thread zur weiteren Überprüfung kennzeichnen<br />–   Kennzeichnung eines Threads aufheben<br />–   Thread umbenennen<br />–   Threads anzeigen und ausblenden<br /><br /> Sonstige Aktionen:<br /><br /> –   Aufrufliste für einen Thread in einem DataTip anzeigen|
|Quellcodefenster|Threadindikatoren im linken Bundsteg geben einzelne oder mehrere Threads an (standardmäßig deaktiviert, die Aktivierung erfolgt über das Kontextmenü im Fenster **Threads**).|Kontextmenü:<br /><br /> –   Zu Thread wechseln<br />–   Thread zur weiteren Überprüfung kennzeichnen<br />–   Kennzeichnung eines Threads aufheben|
|Symbolleiste **Debugspeicherort**|–   Aktueller Prozess<br />–   Anwendung anhalten<br />–   Anwendung fortsetzen<br />–   Anwendung anhalten und herunterfahren<br />–   Aktueller Thread<br />–   Aktuellen Status des Threadkennzeichens umkehren<br />–   Nur gekennzeichnete Threads anzeigen<br />–   Nur aktuellen Prozess anzeigen<br />–   Aktueller Stapelrahmen|–   Zu einem anderen Prozess wechseln<br />–   Anwendung anhalten, fortsetzen oder herunterfahren<br />–   Zu einem anderen Thread im aktuellem Prozess wechseln<br />–   Zu einem anderen Stapelrahmen in aktuellem Thread wechseln<br />–   Aktuelle Threads kennzeichnen bzw. Kennzeichnung aufheben<br />–   Nur gekennzeichnete Threads anzeigen<br />–   Nur den aktuellen Prozess anzeigen|
|Fenster **Parallele Stapel**|–   Aufruflisten für mehrere Threads in einem Fenster<br />–   Aktiver Stapelrahmen für jeden Thread<br />–   Aufrufer und Aufgerufene für die einzelnen Methoden|–   Bestimmte Threads herausfiltern<br />-Zur Aufgaben Ansicht wechseln<br />–   Thread kennzeichnen bzw. Kennzeichnung aufheben<br />–   Zoomen|
|Fenster **Parallele Überwachung**|–   Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.<br />–   Die Framespalte, in der ein Pfeil den ausgewählten Frame angibt.<br />–   Eine konfigurierbare Spalte, in der der Computer, der Prozess, die Kachel, die Aufgabe und der Thread angezeigt werden können.|–   Thread kennzeichnen bzw. Kennzeichnung aufheben<br />–   Nur gekennzeichnete Threads anzeigen<br />–   Frames wechseln<br />–   Spalte sortieren<br />–   Threads gruppieren<br />–   Threads einfrieren oder reaktivieren<br />–   Daten im parallelen Überwachungsfenster exportieren|
|**Aufgaben** Fenster|–   Informationen zu <xref:System.Threading.Tasks.Task>-Objekten anzeigen, einschließlich der Aufgaben-ID, des Aufgabenstatus (geplant, ausgeführt, wartend, blockiert) und der der Aufgabe zugewiesenen Threads.<br />–   Aktuelle Position in der Aufrufliste.<br />–   Zur Erstellungszeit an die Aufgabe übergebener Delegat|–   Zur aktuellen Aufgabe wechseln<br />–   Aufgabe kennzeichnen oder Kennzeichnung aufheben<br />–   Aufgabe  einfrieren oder reaktivieren|
|Fenster **GPU-Threads**|–   Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.<br />-Die aktuelle Thread Spalte, in der ein gelber Pfeil den aktuellen Thread angibt.<br />–   Die Spalte **Threadanzahl**, in der die Anzahl von Threads an derselben Position angezeigt wird.<br />–   Die Spalte **Zeile**, in der die Codezeile angezeigt wird, in der sich die jeweilige Threadgruppe befindet.<br />–   Die Spalte **Adresse**, in der die Anweisungsadresse angezeigt wird, in der sich die jeweilige Threadgruppe befindet.<br />–   Die Spalte **Speicherort**, in der der Ort im Code die Adresse angegeben ist.<br />–   Die Spalte **Status**, in der angegeben ist, ob der Thread aktiv oder blockiert ist.<br />–   Die Spalte **Kachel**, in der der Kachelindex für die Threads in der Zeile angezeigt wird.|-Ändern in einen anderen Thread<br />–   Bestimmte Kachel und bestimmten Thread anzeigen<br />–   Spalte ein- oder ausblenden<br />–   Nach Spalte sortieren<br />–   Threads gruppieren<br />–   Threads einfrieren oder reaktivieren<br />–   Thread kennzeichnen bzw. Kennzeichnung aufheben<br />–   Nur gekennzeichnete Threads anzeigen|

## <a name="see-also"></a>Siehe auch

- [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md)