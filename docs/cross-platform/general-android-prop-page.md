---
title: Allgemeine Projekteigenschaften (Android C++) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 4bb6f26fe40b639b43cb803577a785fa9b48823d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818946"
---
# <a name="general-project-properties-android-c"></a>Allgemeine Projekteigenschaften (Android C++)

Eigenschaft | Beschreibung | Auswahlmöglichkeiten
--- | ---| ---
Ausgabeverzeichnis | Gibt einen relativen Pfad zum Ausgabedateiverzeichnis an. Kann Umgebungsvariablen enthalten.
Zwischenverzeichnis | Gibt einen relativen Pfad zum Zwischendateiverzeichnis an. Kann Umgebungsvariablen enthalten.
Target Name | Gibt einen Dateinamen an, den dieses Projekt generiert.
Zielerweiterung | Gibt eine Dateierweiterung an, die dieses Projekt generiert. (Beispiel: *.exe* oder *.dll*)
Bei der Bereinigung zu löschende Erweiterungen | Durch Semikolons getrennte Platzhalterspezifikation, die angibt, welche Dateien im Zwischenverzeichnis beim Bereinigen oder erneuten Erstellen gelöscht werden sollen.
Buildprotokolldatei | Gibt die zu schreibende Buildprotokolldatei an, wenn die Buildprotokollierung aktiviert ist.
Plattformtoolset | Gibt das Toolset zum Erstellen der aktuellen Konfiguration an. Wenn keine Angabe erfolgt, wird das Standardtoolset verwendet.
Konfigurationstyp | Gibt den Typ der Ausgabe an, die diese Konfiguration generiert. | **Dynamische Bibliothek (.so)**: Dynamische Bibliothek (*.so*)<br>**Statische Bibliothek (.a)**: Statische Bibliothek (*.a*)<br>**Hilfsprogramm**: Hilfsprogramm<br>**Makefile**: Makefile<br>
API-Zielebene | API-Ebene des Android NDK, die diese Konfiguration als Ziel hat.
Verwendung von STL | Gibt an, welche C++-Standardbibliothek für diese Konfiguration verwendet werden soll. | **Minimale C++-Laufzeitbibliothek (system)**<br>**C++-Laufzeit statische Bibliothek (gabi++_static)**<br>**C++-Laufzeit freigegebene Bibliothek (gabi++_shared)**<br>**STLport-Laufzeit statische Bibliothek (stlport_static)**<br>**STLport-Laufzeit freigegebene Bibliothek (stlport_shared)**<br>**GNU STL statische Bibliothek (gnustl_static)**<br>**GNU STL freigegebene Bibliothek (gnustl_shared)**<br>**LLVM libc++ statische Bibliothek (c++_static)**<br>**LLVM libc++ freigegebene Bibliothek (c++_shared)**<br>
Thumb-Modus | Generieren Sie Code, der für die Thumb-Mikroarchitektur ausgeführt wird. Dies gilt nur für die ARM-Architektur. | **Thumb**<br>**Arm**<br>**Disabled** (deaktiviert)<br>
