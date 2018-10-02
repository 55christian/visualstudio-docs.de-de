---
title: Anfügen an den Prozess nicht möglich | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.remote.unable2attach
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41eed3132039f2622c5d46b9937893ddaafa2dbf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511583"
---
# <a name="unable-to-attach-to-the-process"></a>Anfügen an den Prozess nicht möglich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [kann nicht an den Prozess anhängen](https://docs.microsoft.com/visualstudio/debugger/unable-to-attach-to-the-process).  
  
Anfügen an den Prozess nicht möglich. Der Debuggerkomponente auf dem Server wurde beim Herstellen einer Verbindung zu diesem Computer der Zugriff verweigert.  
  
 Es gibt zwei gängige Szenarios, durch die dieser Fehler verursacht wird:  
  
 **Szenario 1:** Computer A Windows XP ausgeführt wird. Auf Computer B wird Windows Server 2003 ausgeführt. Die Registrierung auf Computer B enthält den folgenden DWORD-Wert:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 Benutzer 1 startet eine Terminal Server-Sitzung (Sitzung 1) auf Computer B und ruft in dieser Sitzung eine verwaltete Anwendung auf.  
  
 Benutzer 2, Administrator beider Computer ist, ist bei Computer a angemeldet. Von dort aus versucht er für die Verbindung zu einer Anwendung, die auf Computer b in Sitzung 1 ausgeführt  
  
 **Szenario 2:** auf zwei Computern, A und B in derselben Arbeitsgruppe, ein Benutzer angemeldet ist, mit dem gleichen Kennwort auf beiden Computern. Der Debugger auf Computer A ausgeführt wird und versucht, Anfügen an eine verwaltete Anwendung, die auf Computer b-Computer ein **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** festgelegt **Gast**.  
  
### <a name="to-solve-scenario-1"></a>So lösen Sie Szenario 1  
  
-   Führen Sie den Debugger und die verwaltete Anwendung unter Verwendung desselben Benutzerkontonamens und Kennworts aus.  
  
### <a name="to-solve-scenario-2"></a>Lösen Sie Szenario 2  
  
1.  Von der **starten** Menü wählen **Systemsteuerung**.  
  
2.  In der Systemsteuerung, doppelklicken Sie auf **Verwaltung**.  
  
3.  Doppelklicken Sie im Fenster Verwaltung auf **Local Security Policy**.  
  
4.  Wählen Sie im Fenster Lokale Sicherheitsrichtlinie **lokale Richtlinien**.  
  
5.  In der **Richtlinien** Spalte doppelklicken Sie auf **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten**.  
  
6.  In der **Netzwerkzugriff: Modell für gemeinsame Nutzung und Sicherheitsmodell für lokale Konten** Dialogfeld ändern, die lokale sicherheitseinstellung **klassischen**, und klicken Sie auf **OK**.  
  
    > [!CAUTION]
    >    Das Ändern des Sicherheitsmodells in Klassisch kann zu unerwünschtem Zugriff auf freigegebene Dateien und DCOM-Komponenten führen. Wenn Sie diese Änderung vornehmen, kann sich ein Remotebenutzer mit Ihrem lokalen Benutzerkonto anstatt als Gast authentifizieren. Wenn ein Remotebenutzer Ihren Benutzernamen und Ihr Kennwort angibt, kann dieser Benutzer auf alle von Ihnen freigegebenen Ordner und DCOM-Objekte zugreifen. Um nicht autorisierte Zugriffe bei der Verwendung dieses Sicherheitsmodells zu vermeiden, sollten Sie dafür sorgen, dass alle Benutzerkonten auf dem Computer über sichere Kennwörter verfügen, oder richten Sie einen isolierten Netzwerkabschnitt für zu debuggende Computer und die Computer ein, auf denen das Debuggen ausgeführt wird.  
  
7.  Schließen Sie alle Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)


