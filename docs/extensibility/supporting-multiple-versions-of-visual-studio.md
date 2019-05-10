---
title: Unterstützen mehrerer Versionen von Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 566407f4d15fdaedaf9a89eb50648e555a370750
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434539"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Unterstützen mehrerer Versionen von Visual Studio
Der Begriff *Seite-an-Seite* bedeutet, dass Sie installieren und mehrere Versionen eines Produkts auf dem gleichen Computer verwalten können. Für VSPackages bedeutet, dass an, dass ein Benutzer mehrere Versionen von Visual Studio auf demselben Computer installiert haben kann. Allerdings möglich keine Seite-an-Seite Ihre VSPackages Laden in eine einzelne Version von Visual Studio-Versionen.

 Bevor Sie Ihr VSPackage in die Seite-an-Seite-Versionen von Visual Studio geladen werden können vornehmen, berücksichtigen Sie Folgendes:

- Sie müssen bestimmen, welche Seite-an-Seite Implementierungsstrategie für die Sie ausführen möchten.

   Weitere Informationen finden Sie unter [auswählen zwischen freigegebenen "und" mit versionsverwaltung durch das VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Ihre Dateiformate Projektmappen- und Projektdateien müssen Ihre Strategie für die Implementierung passen.

   Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) und [Registrieren von Dateierweiterungen für Seite-an-Seite Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Das Installationsprogramm muss Ihre Strategie für die Implementierung behandeln, sodass mit versionsverwaltung durch das Komponenten sowie alle Versionen, gemeinsam genutzte Komponenten ordnungsgemäß installiert und registriert werden.

   Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) sowie [Komponentenverwaltung](../extensibility/internals/component-management.md).

  > [!NOTE]
  > Installieren einer Version von Visual Studio auch eine entsprechende Version von installiert die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Installieren von Visual Studio 2010 und Visual Studio 2012 auf dem gleichen Computer z. B. auch Versionen 4.0 und 4.5 installiert die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]bzw.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Auswählen zwischen freigegebenen "und" mit versionsverwaltung durch das VSPackages](../extensibility/choosing-between-shared-and-versioned-vspackages.md) wird erläutert, wie Seite-an-Seite Probleme in Ihrem VSPackage zu beheben.

- [Registrieren von Dateierweiterungen für Seite-an-Seite Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) wird beschrieben, wie Ihr VSPackage dateizuordnungen in einem Seite-an-Seite-Szenario registrieren kann.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
