---
title: Allgemeine Projekteigenschaften (Android C++-Makefile) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: b7fa1b91951e7a3fb145cc26275016037d1b5f2b
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950577"
---
# <a name="general-project-properties-android-c-makefile"></a>Allgemeine Projekteigenschaften (Android C++-Makefile)

Eigenschaft | BESCHREIBUNG | Auswahlmöglichkeiten
--- | ---| ---
Ausgabeverzeichnis | Gibt einen relativen Pfad zum Ausgabedateiverzeichnis an. Kann Umgebungsvariablen enthalten.
Zwischenverzeichnis | Gibt einen relativen Pfad zum Zwischendateiverzeichnis an. Kann Umgebungsvariablen enthalten.
Buildprotokolldatei | Gibt die zu schreibende Buildprotokolldatei an, wenn die Buildprotokollierung aktiviert ist.
Konfigurationstyp | Gibt den Typ der Ausgabe an, die diese Konfiguration generiert. | **Dynamische Bibliothek (.so)** : Dynamische Bibliothek ( *.so*)<br>**Statische Bibliothek (.a)** : Statische Bibliothek ( *.a*)<br>**Hilfsprogramm**: Hilfsprogramm<br>**Makefile**: Makefile<br>
