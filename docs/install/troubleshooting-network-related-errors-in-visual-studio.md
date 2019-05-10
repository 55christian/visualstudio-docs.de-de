---
title: Problembehandlung von Netzwerk- oder Proxyfehlern
description: Finden Sie Lösungen für netzwerk- oder proxybezogene Fehler, die beim Installieren oder Verwenden von Visual Studio hinter einer Firewall oder einem Proxyserver auftreten können.
ms.date: 03/30/2019
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e98f06a2dabd6627fbc70b1d072d0e34924c6691
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968131"
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Beheben von Netzwerkfehlern beim Installieren oder Verwenden von Visual Studio

Hier erfahren Sie, welche Lösungen für die häufigsten netzwerk- oder proxybezogenen Fehler zur Verfügung stehen, die beim Installieren oder Verwenden von Visual Studio hinter einer Firewall oder einem Proxyserver auftreten können.

## <a name="error-proxy-authorization-required"></a>Fehler: „Proxyautorisierung erforderlich“

Dieser Fehler tritt normalerweise auf, wenn Benutzer über einen Proxyserver mit dem Internet verbunden sind, und der Proxyserver die Aufrufe einiger Netzwerkressourcen blockiert, die von Visual Studio ausgeführt werden.

### <a name="to-fix-this-proxy-error"></a>So beheben Sie diesen Proxyfehler

- Starten Sie Visual Studio neu. Das Dialogfeld Proxy-Authentifizierung sollte angezeigt werden. Geben Sie bei Aufforderung Ihre Anmeldeinformationen in das Dialogfeld ein.

- Wenn das Problem durch einen Neustart von Visual Studio nicht behoben wird, liegt dies möglicherweise daran, dass der Proxyserver keine Anmeldeinformationen für „http:&#47;&#47;go.microsoft.com“-Adressen, sondern für „&#42;.visualStudio.com“-Adressen erwartet. Für diese Server müssen Sie der Whitelist ggf. die folgenden URLs hinzufügen, um die Blockierung aller Anmeldeszenarien in Visual Studio aufzuheben:

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- Sie können die Adresse „http:&#47;&#47;go.microsoft.com“ andernfalls aus der Whitelist entfernen, damit das Dialogfeld „Proxyauthentifizierung“ beim Neustart von Visual Studio sowohl für die Adresse „http:&#47;&#47;go.microsoft.com“ als auch die Serverendpunkte angezeigt wird.

  -ODER-

- Wenn Sie die standardmäßigen Anmeldeinformationen mit Ihrem Proxy verwenden möchten, können Sie Folgendes tun:

::: moniker range="vs-2017"

  1. Suchen Sie **devenv.exe.config** (die Konfigurationsdatei „devenv.exe“) in **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** oder **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. Suchen Sie in der Konfigurationsdatei die `<system.net>`-Sperre und fügen Sie dann diesen Code hinzu:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Sie müssen die korrekte Proxy-Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>` einfügen.

     > [!NOTE]
     > Weitere Informationen finden Sie auf den Seiten zu den Elementen [&lt;defaultProxy&gt; (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) und [&lt;proxy&gt; (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings).

::: moniker-end

::: moniker range="vs-2019"

  1. Suchen Sie **devenv.exe.config** (die Konfigurationsdatei „devenv.exe“) in **%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE** oder **%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**.

  2. Suchen Sie in der Konfigurationsdatei die `<system.net>`-Sperre und fügen Sie dann diesen Code hinzu:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Sie müssen die korrekte Proxy-Adresse für Ihr Netzwerk in `proxyaddress="<http://<yourproxy:port#>` einfügen.

     > [!NOTE]
     > Weitere Informationen finden Sie auf den Seiten zu den Elementen [&lt;defaultProxy&gt; (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings/) und [&lt;proxy&gt; (Netzwerkeinstellungen)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings).

::: moniker-end

## <a name="error-the-underlying-connection-was-closed"></a>Fehler: „The underlying connection was closed.“ (Die zugrunde liegende Verbindung wurde geschlossen)

Wenn Sie Visual Studio in einem privaten Netzwerk mit einer Firewall verwenden, kann Visual Studio möglicherweise keine Verbindung mit einigen Netzwerkressourcen herstellen. Dies kann auch Azure DevOps Services für Anmeldung und Lizenzierung, NuGet und Azure-Dienste betreffen. Falls Visual Studio keine Verbindung mit einer dieser Ressourcen herstellen kann, wird möglicherweise die folgende Fehlermeldung angezeigt:

  **The underlying connection was closed: An unexpected error occurred on send (Die zugrunde liegende Verbindung wurde geschlossen: Unerwarteter Fehler beim Senden.)**

Visual Studio verwendet das Protokoll Transport Layer Security (TLS) 1.2 für die Verbindung mit Netzwerkressourcen. Sicherheitsappliances blockieren in einigen privaten Netzwerken bestimmte Serververbindungen, wenn Visual Studio TLS 1.2 verwendet.

### <a name="to-fix-this-connection-error"></a>So beheben Sie diesen Verbindungsfehler

Lassen Sie Verbindungen mit den folgenden URLs zu:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (für Azure-Verbindungen)

- &#42;.visualstudio.com

- cdn.vsassets.io (Hosting von CDN-Inhalten (Content Delivery Network))

- &#42;.gallerycdn.vsassets.io (hostet Azure DevOps Services-Erweiterungen)

- static2.sharepointonline.com (Hosting von Ressourcen wie beispielsweise Schriftarten, die Visual Studio im Office Fabric UI-Kit verwendet)

- &#42;.nuget.org (für NuGet-Verbindungen)

  > [!NOTE]
  > URLs von privaten NuGet-Servern sind in dieser Liste möglicherweise nicht enthalten. Sie können in „%APPData%\Nuget\NuGet.Config“ überprüfen, welche NuGet-Server Sie verwenden.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren und Verwenden von Visual Studio hinter einer Firewall oder einem Proxyserver](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
* [Installieren von Visual Studio](install-visual-studio.md)
