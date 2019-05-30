---
title: Ermitteln von Systemanforderungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ef76bc111fc48a717605f1beea74c4b91d0f2b4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351642"
---
# <a name="detect-system-requirements"></a>Ermitteln von Systemanforderungen
Eine VSPackage funktioniert nicht, es sei denn, die Visual Studio installiert ist. Wenn Sie Microsoft Windows Installer, zum Verwalten der Installation von einem VSPackage verwenden, können Sie das Installationsprogramm aus, um festzustellen, ob die Installation von Visual Studio konfigurieren. Sie können auch damit das System für andere Anforderungen, z. B. überprüfen, eine bestimmte Version von Windows oder einer bestimmten Menge an RAM konfigurieren.

## <a name="detect-visual-studio-editions"></a>Erkennen von Visual Studio-Editionen
 Um zu bestimmen, ob eine Edition von Visual Studio installiert ist, überprüfen, ob der Wert des der **installieren** Registrierungsschlüssel ist *(REG_DWORD) 1* im entsprechenden Ordner, in der folgenden Tabelle genannten. Beachten Sie, dass eine Hierarchie von Visual Studio-Editionen:

1. Enterprise

2. Professionell

3. Community

Wenn eine neuere Version installiert ist, werden die Registrierungsschlüssel für diese Edition ebenfalls wie bei früheren Versionen hinzugefügt. D. h., wenn die Enterprise Edition installiert ist, die **installieren** Schlüssel nastaven NA hodnotu *1* für Unternehmen sowie für die Editionen Professional und Community. Aus diesem Grund müssen Sie nur auf der aktuellsten Version zu überprüfen, die Sie benötigen.

> [!NOTE]
> 32-Bit-Schlüssel werden in der 64-Bit-Version des Registrierungs-Editor unter angezeigt **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\** . Die Visual Studio-Schlüssel befinden sich unter **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\** .

|Produkt|Key|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 Shell (integriert und isoliert)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Erkennen Sie, wenn Visual Studio ausgeführt wird
 Das VSPackage kann nicht ordnungsgemäß registriert werden, wenn Visual Studio ausgeführt wird, wenn VSPackages installiert ist. Das Installationsprogramm muss erkennen, wenn Visual Studio ausgeführt wird, und klicken Sie dann zum Installieren des Programms verweigert. Windows Installer können nicht Sie Einträge zu verwenden, um diese Erkennung zu aktivieren. Stattdessen müssen Sie eine benutzerdefinierte Aktion, wie folgt erstellen: Verwenden der `EnumProcesses` Funktion zum Erkennen der *devenv.exe* verarbeiten, und legen Sie dann entweder eine Installer-Eigenschaft, die in eine Startbedingung verwendet oder bedingt zeigt ein Dialogfeld, das den Benutzer auffordert, schließen Sie Visual Studio.

## <a name="see-also"></a>Siehe auch
- [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)