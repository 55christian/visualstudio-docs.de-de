---
title: Entfernen von Visual Studio
titleSuffix: ''
description: Ausführliche Informationen zum vollständigen Entfernen von Visual Studio von Ihren Computer
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e363065d96169660817a548fb97d39f09cf679c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810389"
---
# <a name="remove-visual-studio"></a>Entfernen von Visual Studio

Wenn ein schwerwiegender Fehler auftritt und Sie Visual Studio nicht reparieren können oder deinstallieren müssen, können Sie mit dem Tool `InstallCleanup.exe` Installationsdateien und Produktinformationen für alle installierten Instanzen von Visual Studio 2017 oder Visual Studio 2019 entfernen. Auf dieses Tool sollte nur im Notfall zurückgegriffen werden, wenn eine Reparatur oder Deinstallation nicht mehr möglich ist, da es Funktionen aus anderen Visual Studio-Installationen oder Produkten deinstallieren kann, die anschließend möglicherweise ebenfalls repariert werden müssen.

Für die folgenden Schritte können Sie das Tool mit verschiedenen Befehlszeilenschaltern ausführen, die folgendes Verhalten aufweisen:

| Schalter | Verhalten |
| ------ | -------- |
| `-i`   | Dieser Schalter ist die Standardeinstellung, wenn kein anderer Schalter übergeben wird, und entfernt nur das Hauptinstallationsverzeichnis und die Produktinformationen. Dieses Verhalten ist vorzuziehen, wenn Sie nach der Ausführung des Tools `InstallCleanup.exe` dieselbe Version erneut installieren möchten. |
| `-f`   | Indem Sie diesen Schalter angeben, werden das Hauptinstallationsverzeichnis, die Produktinformationen und fast alle Funktionen entfernt, die außerhalb des Installationsverzeichnisses installiert wurden und für andere Visual Studio-Installationen oder Produkte freigegeben werden können. Dieses Verhalten ist empfehlenswert, wenn Sie Visual Studio ohne spätere Neuinstallation entfernen möchten. |

1. Schließen Sie den Visual Studio-Installer.
2. Öffnen Sie eine Eingabeaufforderung als Administrator. Wenn Sie eine Eingabeaufforderung als Administrator öffnen möchten, führen Sie diese Schritte aus:
   * Geben Sie **cmd** in das Suchfeld ein.
   * Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung** und dann auf **Als Administrator ausführen**.
3. Geben Sie den vollständigen Pfad des Hilfsprogramms `InstallCleanup.exe` ein, und übergeben Sie den gewünschten Befehlszeilenschalter. Der Pfad des Hilfsprogramms ist standardmäßig wie folgt:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Wenn Sie `InstallCleanup.exe` nicht im Verzeichnis des Visual Studio-Installers finden (immer in `%ProgramFiles(x86)%\Microsoft Visual Studio`), führen Sie die Schritte unter [Installieren von Visual Studio](install-visual-studio.md) aus. Wenn der Auswahlbildschirm für Workloads angezeigt wird, schließen Sie das Fenster, und führen Sie die vorherigen Schritte erneut aus.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Visual Studio aktualisieren](update-visual-studio.md)
* [Ändern von Visual Studio](modify-visual-studio.md)
* [Deinstallieren von Visual Studio](uninstall-visual-studio.md)
