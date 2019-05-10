---
title: Entsperren Sie den Download der Remotetools
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903022"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Vorgehensweise: Entsperren Sie den Download der Remotetools unter Windows Server

Die standardsicherheitseinstellungen in Internet Explorer unter Windows Server können zum Herunterladen von Komponenten wie z. B. die Remotetools zeitaufwändige gestalten.

* Durch die verstärkte Sicherheitskonfiguration für Internet Explorer, der verhindert, dass Sie von Websites öffnen und den Zugriff auf Webressourcen, es sei denn, die Domäne, die mit der Ressource explizit zugelassen wird aktiviert ist (d. h. vertrauenswürdig). Obwohl Sie diese Einstellung deaktivieren können, empfohlen nicht es, da er ein Sicherheitsrisiko darstellen kann.

* Unter Windows Server 2016 eine Standardeinstellung in **Internetoptionen** > **Sicherheit** > **Internet**  >   **Stufe** > **Downloads** auch deaktiviert Dateidownloads. Wenn Sie die Remoteserver-Verwaltungstools unter Windows Server direkt herunterladen möchten, müssen Sie die Datei zum Herunterladen aktivieren.

Herunterladen von Tools unter Windows Server, empfehlen wir eine der folgenden:

* Laden Sie die Remoteserver-Verwaltungstools auf einem anderen Computer wie die einer ausgeführten Visual Studio, und kopieren Sie die *.exe* -Datei mit Windows Server.

* Ausführen des Remotedebuggers [aus einer Dateifreigabe](../debugger/remote-debugging.md#fileshare_msvsmon) auf Ihrem Computer Visual Studio.

* Laden Sie die Remoteserver-Verwaltungstools direkt auf Windows Server, und akzeptieren Sie die aufforderungen, um den vertrauenswürdigen Sites hinzufügen. Moderne Websites enthalten häufig viele Ressourcen von Drittanbietern, damit dies zahlreiche Anweisungen führen kann. Darüber hinaus müssen alle umgeleiteten Links manuell hinzugefügt werden. Sie können auch einige der vertrauenswürdigen Sites hinzufügen, bevor Sie den Download ab. Wechseln Sie zu **Internetoptionen > Sicherheit > Vertrauenswürdige Sites > Websites** und fügen Sie den folgenden Websites hinzu.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * Informationen zu: leer

  Fügen Sie bei älteren Versionen des Debuggers auf my.visualstudio.com wird diese zusätzliche Websites hinzu, stellen Sie sicher, dass diese Anmeldung erfolgreich ist:

  * microsoft.com
  * go.microsoft.com
  * 0download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Wenn Sie diese Domänen, die beim Herunterladen der Remoteserver-Verwaltungstools hinzufügen möchten, und wählen Sie dann **hinzufügen** Aufforderung.

    ![Blockierte Content (Dialogfeld)](../debugger/media/remotedbg-blocked-content.png)

    Wenn Sie die Software herunterladen, erhalten Sie einige zusätzlichen Anforderungen zum Laden von verschiedenen Website-Skripts und Ressourcen berechtigt zu gewähren. Auf my.visualstudio.com empfehlen wir, dass Sie, die zusätzlichen Domänen hinzufügen an, stellen Sie sicher, dass diese Anmeldung erfolgreich ist.