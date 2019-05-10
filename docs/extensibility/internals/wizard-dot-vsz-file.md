---
title: Assistenten (. VSZ)-Datei | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1bd68e9d647f9a44eaa8b975995f2d7de3d9640
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907544"
---
# <a name="wizard-vsz-file"></a>Assistentendatei (VSZ)

Die integrierte Entwicklungsumgebung (IDE) verwendet die VSZ-Dateien zum Starten von Assistenten. Diese VSZ-Dateien enthalten Informationen, die die IDE verwendet werden, um zu bestimmen, welcher Assistent aufrufen und welche Informationen an den Assistenten übergeben.

Eine VSZ-Datei ist eine Version einer INI-formatierte Textdatei, die keine Abschnitte aufweist. Informationen, die bekanntermaßen von der IDE werden am Anfang der Datei gespeichert. Dadurch wird eine Verknüpfung zwischen den Assistenten, den die IDE aufruft und die Parameter in der VSZ-Datei, die an der IDE übergeben werden. Der Rest der Datei enthält die Parameter, die sind spezifisch für den Assistenten und werden von der IDE gesammelt werden sollen und an den bestimmten Assistenten übergeben.

Das folgende Beispiel zeigt den Inhalt des eine VSZ-Datei.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Im folgenden werden die Teile in der VSZ-Datei.

|Segment|Beschreibung|
|----------|-----------------|
|VSWizard|Der erste Parameter in der Datei ist die Versionsnummer des Vorlagendateiformats. Diese Versionsnummer muss 6.0, 7.0, 7.1 oder 8.0. Andere Zahlen können nicht gestartet werden und verursacht den Fehler ein ungültiges Format.|
|Assistent|Dieses Feld enthält die OLE-ProgID des Assistenten, oder alternativ eine Zeichenfolgendarstellung der GUID der CLSID des Assistenten, der gleichzeitig von der IDE erstellt wird.|
|Parameter|Diese Komponenten sind optional. Sie können so viele wie nötig hinzufügen.|

Die Parameter ermöglichen die VSZ-Datei weitere benutzerdefinierte Parameter an den Assistenten übergeben. Jeder Wert wird als Zeichenfolgenelement in einem Array von Varianten an den Assistenten übergeben. Weitere Informationen finden Sie unter [benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md).

Um eine Standard-Gebietsschema-ID der VSZ-Datei hinzuzufügen, geben `FALLBACK_LCID`= Xxxx, Xxxx die Gebietsschema-ID, z. B. 1033 für Englisch ist. Wenn `FALLBACK_LCID` Parameter definiert ist, wird der Assistent verwendet die angegebenen fallback-Gebietsschema-ID aus, wenn die aktuelle ID nicht gefunden wird.

## <a name="see-also"></a>Siehe auch

- [Benutzerdefinierte Parameter](../../extensibility/internals/custom-parameters.md)
- [Assistenten](../../extensibility/internals/wizards.md)
- [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)