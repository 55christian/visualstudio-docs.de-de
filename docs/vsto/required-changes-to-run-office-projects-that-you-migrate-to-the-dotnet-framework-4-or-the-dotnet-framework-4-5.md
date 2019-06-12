---
title: Erforderliche Änderungen für Office-Projekten migriert auf .NET Framework 4, 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 82ae3f8a43b65e6ff617192dc38149691d229455
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836061"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Erforderliche Änderungen für das Ausführen von Office-Projekten, die auf .NET Framework 4 oder .NET Framework 4.5 migriert werden
  Wenn das Zielframework eines Office-Projekts, um geändert wird die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder später von einer früheren Version von .NET Framework, Sie müssen die folgenden Aufgaben aus, um sicherzustellen, dass die Lösung auf dem Entwicklungscomputer und auf Endbenutzercomputern ausgeführt werden kann:

- Entfernen Sie das <xref:System.Security.SecurityTransparentAttribute> aus dem Projekt, wenn Sie ein Upgrade aus Visual Studio 2008 ausgeführt haben.

- Führen Sie eine **Bereinigen** -Befehl in Visual Studio in der Lage, ausführen oder Debuggen des Projekts auf dem Entwicklungscomputer installiert sein.

- Aktualisieren Sie die .NET Framework-Voraussetzung für das Projekt.

- Endbenutzer müssen außerdem die Projektmappe neu installieren, wenn Sie diese zuvor mit ClickOnce bereitgestellt haben, bevor Sie das Zielframework geändert haben.

  Weitere Informationen zu den einzelnen Aufgaben finden Sie in den entsprechenden Abschnitten weiter unten.

## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Entfernen Sie das SecurityTransparent-Attribut aus Projekten, die Aktualisierung von Visual Studio 2008
 Wenn Sie ein Upgrade für ein Office-Projekt aus Visual Studio 2008 ausgeführt haben und sich das Zielframework des Projekts anschließend in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher ändert, müssen Sie das <xref:System.Security.SecurityTransparentAttribute> aus dem Projekt entfernen. Visual Studio entfernt dieses Attribut nicht automatisch für Sie. Wenn Sie dieses Attribut nicht entfernen, erhalten Sie eine Fehlermeldung, wenn Sie das Projekt kompilieren.

 Weitere Informationen zu den Bedingungen, die in der Visual Studio das Zielframework eines aktualisierten Projekts in ändern können die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], finden Sie unter [aktualisieren und Migrieren von Office-Projektmappen](../vsto/upgrading-and-migrating-office-solutions.md).

#### <a name="to-remove-the-securitytransparentattribute"></a>So entfernen Sie "SecurityTransparentAttribute"

1. Öffnen Sie den **Projektmappen-Explorer**, während das Projekt in Visual Studio geöffnet ist.

2. Doppelklicken Sie unter dem Knoten **Eigenschaften** (für C#) oder dem Knoten **Mein Projekt** (für Visual Basic) auf die Codedatei "AssemblyInfo", um diese im Code-Editor zu öffnen.

    > [!NOTE]
    > In Visual Basic-Projekten müssen Sie im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen** klicken, um die Codedatei "AssemblyInfo" anzuzeigen.

3. Suchen Sie nach <xref:System.Security.SecurityTransparentAttribute>, und entfernen Sie das Attribut aus der Datei, oder kommentieren Sie es aus.

    ```vb
    <Assembly: SecurityTransparent()>
    ```

    ```csharp
    [assembly: SecurityTransparent()]
    ```

## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Ausführen des Befehls "bereinigen" zum Debuggen oder Ausführen eines Projekts auf dem Entwicklungscomputer
 Wenn ein Office-Projekt erstellt wurde, bevor das Zielframework des Projekts, um geändert wird die [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher verwenden, müssen Sie führen eine **Bereinigen** Befehl aus, und klicken Sie dann das Projekt neu, nachdem das Zielframework geändert wurde. Wenn führen Sie keine **Bereinigen** Befehl erhalten Sie eine <xref:System.Runtime.InteropServices.COMException> beim Versuch, Debuggen oder Ausführen von neu ausgerichteten Projekt.

 Weitere Informationen zu den **Bereinigen** Befehl, finden Sie unter [erstellen Office-Projektmappen](../vsto/building-office-solutions.md).

## <a name="update-the-prerequisites-for-deployment"></a>Aktualisieren Sie die Voraussetzungen für die Bereitstellung
 Wenn Sie ein Office-Projekt umleiten [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher verwenden, müssen Sie auch die entsprechenden .NET Framework-Voraussetzung im aktualisieren die **Voraussetzungen** Dialogfeld. Andernfalls sucht die ClickOnce-Bereitstellung oder das InstallShield Limited Edition-Projekt nach einer früheren Version von .NET Framework und installiert diese.

 Weitere Informationen zu den Voraussetzungen für die Bereitstellung auf Endbenutzercomputern aktualisiert, finden Sie unter [Vorgehensweise: Installieren der erforderlichen Komponenten auf Endbenutzercomputern zum Ausführen von Office-Projektmappen](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

## <a name="reinstall-solutions-on-end-user-computers"></a>Installieren von Projektmappen auf Endbenutzercomputern
 Wenn Sie mithilfe von ClickOnce eine Office-Projektmappe bereitstellen, die als Zielframework .NET Framework 3.5 verwendet, und dann das Projekt auf [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher umstellen, müssen Endbenutzer die Projektmappe deinstallieren und dann erneut installieren, nachdem Sie sie veröffentlicht haben. Wenn Sie erneut, die neu zugewiesene Lösung veröffentlichen, und die Lösung auf Endbenutzercomputern aktualisiert wird, erhalten Endbenutzer eine <xref:System.Runtime.InteropServices.COMException> Wenn sie die aktualisierte Lösung ausführen.

## <a name="see-also"></a>Siehe auch
- [Migrieren von Office-Projektmappen zu .NET Framework 4 oder höher](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
