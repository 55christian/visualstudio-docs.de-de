---
title: 'Testbereich 6: Delete | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3ffe786b5bc5f6d0bb0233fbb431988e0145611d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155934"
---
# <a name="test-area-6-delete"></a>Testbereich 6: Löschen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quellcodeverwaltung Hierunter-Plug-in Test löschen-Aktionen.  
  
 Löschen von Aktionen im Datenquellen-Steuerelement reagiert **Projektmappen-Explorer**.  
  
 Es folgt eine Liste von Elementen, die gelöscht werden können:  
  
- Dateien  
  
- Ordner  
  
- Projekt  
  
  Je nach Projekttyp, haben Sie möglicherweise die Möglichkeit, **entfernen** des Projekts (verlassen die Dateien auf Datenträger) oder **löschen** des Projekts (entfernt die Dateien auf dem Datenträger). Beide Aktionen entfernt, das Projekt oder Projektelement aus **Projektmappen-Explorer**.  
  
## <a name="expected-behavior"></a>Es wird erwartet  
 Das erwartete Verhalten für die Testfälle im Testbereich löschen ist:  
  
- Gelöschtes Element wird nicht mehr angezeigt, in **Projektmappen-Explorer**.  
  
- Das gelöschte Projekt oder Element das übergeordnete Element ist ausgecheckt, nach Bedarf (möglicherweise mit einer Eingabeaufforderung.)  
  
- Nachdem Sie einen aktivierten zu löschen oder Element hinzugefügt, er erscheint nicht in der **Anstehende Eincheckvorgänge** Fenster.  
  
- Das Element ist immer noch im Speicher quellcodeverwaltung, vorhanden ist, auch nach dem Löschvorgang erhalten, und muss manuell gelöscht werden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Löschen eines Clientprojekts|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Entfernen Sie das gesamte Projekt aus Projektmappe|Allgemeine Erwartetes Verhalten.|  
|Löschen Sie eine leere Datei|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie eine Datei zum Projekt hinzu.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Wählen Sie die Datei, löschen Sie diese.|Allgemeine Erwartetes Verhalten.|  
|Löschen eines Ordners mit einer Datei|1.  Einzelne Projektmappe zu erstellen.<br />2.  Fügen Sie einen Ordner hinzu.<br />3.  Fügen Sie eine Datei in den Ordner hinzu.<br />4.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />5.  Sehen Sie sich das Projekt aus, um aufforderungen zu vermeiden.<br />6.  Löschen Sie den Ordner an.|Allgemeine Erwartetes Verhalten.|  
|Löschen einer Datei System-Webprojekt|1.  Erstellen Sie eine Datei System Web-Projekt (verwenden Sie die Schaltfläche zum Durchsuchen an einen UNC-Pfad).<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Entfernen Sie das gesamte Projekt aus der Projektmappe.<br />4.  Wiederholen Sie die Schritte 1 bis 3 für ein lokales Webprojekt (verschiedene Pfade durch den Code ausführt, aber hat die gleiche externe Schnittstelle und das Verhalten).|Allgemeine Erwartetes Verhalten.|  
|Löschen einer Datei aus einer Datei System-Webprojekt|1.  Erstellen Sie ein Projekt Datei System.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Löschen Sie eine Datei aus dem Projekt ein.<br />4.  Wiederholen Sie die Schritte 1 bis 3 für ein lokales Webprojekt (verschiedene Pfade durch den Code ausführt, aber hat die gleiche externe Schnittstelle und das Verhalten).|Allgemeine Erwartetes Verhalten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
