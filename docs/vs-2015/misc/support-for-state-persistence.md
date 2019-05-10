---
title: Unterstützung von Statuspersistenz | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434318"
---
# <a name="support-for-state-persistence"></a>Unterstützung von Statuspersistenz
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] den Status der allgemeine Objekte können beibehalten werden. Beispielsweise sind die Projektmappen-und Projekteigenschaften gespeichert und von Projektmappen-und Projektdateien wiederhergestellt. Benutzereinstellungen können exportiert und aus Dateien für konformitätseinstellungen importiert werden.  
  
 VSPackages stützen sich normalerweise auf lokalen Speicher, entweder in der Registrierung oder in den Anwendungsordner für die Daten für den aktuellen Benutzer oder Computer. Werte, die eine kleine Menge an Speicherplatz für Speicher, z. B. ganze Zahlen und Zeichenfolgen, erfordern, werden in der Regel in der systemregistrierung gespeichert. Werte, die viel Platz für Speicher, z. B. Bitmaps, erfordern, werden in einer Datei gespeichert. Der Pfad der Datei kann selbst in der systemregistrierung gespeichert werden. Der Dauerhaftigkeitsmechanismus muss über die Berechtigung zum Zugriff auf den lokalen Speicher.  
  
## <a name="support-for-locating-local-storage"></a>Unterstützung für die Suche nach lokalen Speicher  
 Die <xref:Microsoft.VisualStudio.Shell.Package> -Klasse bietet Unterstützung für die Suche nach Informationen in der Registrierung oder eine Anwendung Daten Systemordner für den aktuellen Benutzer oder Computer.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Gibt den Pfad der des lokalen Computers Registrierungsstamm für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z. B. HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0Exp.  
  
 Der lokalen Registrierungsstamm aus einer der <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> Service. Wenn dies nicht verfügbar ist, wird es abgerufen, von der <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> Attribut des VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Gibt den Pfad des aktuellen Benutzers (pro Computer) Registrierungsstamm für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], z. B. HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp.  
  
 Der lokalen Registrierungsstamm aus einer der <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> Service. Wenn dies nicht verfügbar ist, wird es aus dem DefaultLocalRegistryRoot-Attribut des VSPackage abgerufen.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Gibt den Pfad des Verzeichnisses, das als allgemeines Repository für dient [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Daten für den aktuellen Roamingbenutzers, z. B. C:\Documents and Settings\\*YourAccountName*\Application Data\Microsoft\ VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Gibt den Pfad des Verzeichnisses, das als allgemeines Repository für dient [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Daten für den aktuellen nicht-roaming-Benutzer, z. B. C:\Documents and Settings\\*YourAccountName*\Local Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackage-Status](../misc/vspackage-state.md)