---
title: Beim Kontaktieren des Remotecomputers ist ein DCOM-Fehler aufgetreten. Der Zugriff wird verweigert. | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc9cae027a078a62b1ef7bab16994a418d76763
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745831"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Beim Kontaktieren des Remotecomputers ist ein DCOM-Fehler aufgetreten. Der Zugriff wird verweigert.
Remotedebugging verwendet DCOM für die Kommunikation zwischen dem lokalen und dem Remotecomputer, wenn eine der folgenden Situationen vorliegt:

- Der Debugger ist auf **Nativer Kompatibilitätsmodus** festgelegt, oder auf der Seite **Extras > Optionen > Debuggen** ist **Verwalteter Kompatibilitätsmodus** aktiviert.

- Sie debuggen verwalteten C++-Code (C++/CLI).

- In Visual Studio 2013 ist auf der Seite **Extras > Optionen > Debuggen** die Option **Natives Bearbeiten und Fortfahren aktivieren** aktiviert.

- Einige Debuggingszenarien von Drittanbietern

  Dieser Fehler tritt auf, wenn der Visual Studio-Prozess sich nicht über DCOM beim Remotedebuggerprozess authentifizieren kann (oder die angegebenen Anmeldeinformationen für unzureichend angesehen wurden). Das Problem kann mit einer oder zwei der folgenden Methoden möglicherweise umgangen werden:

- Deaktivieren Sie  **Systemeigenen Kompatibilitätsmodus verwenden** und **Verwalteter Kompatibilitätsmodus**.

- Deaktivieren Sie in Visual Studio 2013 die Option **Systemeigenes Bearbeiten und Fortfahren aktivieren**.

- Starten Sie beide Computer neu.

- Wenn für das Remotedebugging die Eingabe von Anmeldeinformationen erforderlich ist, aktivieren Sie die Option zum Speichern der Anmeldeinformationen.

## <a name="see-also"></a>Siehe auch

- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)