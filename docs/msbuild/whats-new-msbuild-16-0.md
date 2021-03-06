---
title: Neuerungen in MSBuild 16.0 | Microsoft-Dokumentation
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 1a83ce4cf47f8a1607e562dfdb69b5b7374de1a6
ms.sourcegitcommit: ca9375d1c48355f2e9f7bc1b2d3f0e94eb15db00
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022345"
---
# <a name="whats-new-in-msbuild-160"></a>Neuerungen in MSBuild 16.0

In diesem Artikel werden die aktualisierten Funktionen und Eigenschaften in MSBuild 16.0 beschrieben. Die detaillierten Versionshinweise finden Sie unter [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Geänderter Pfad

 MSBuild wird im Ordner *\Current* der jeweiligen Version von Visual Studio installiert. Beispiel: *C:\Program Files (x86)\Microsoft Visual Studio\Current\Enterprise\MSBuild*. Sie können MSBuild auch mit dem folgenden PowerShell-Modul suchen: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Geänderte Eigenschaften

 Die folgenden MSBuild-Eigenschaften wurden aufgrund der neuen Versionsnummer aktualisiert.

- `MSBuildToolsVersion` für diese Version der Tools ist „Current“. Die Assembly-Version ist 15.1.0.0 und entspricht somit der von Visual Studio 2017.

- `VisualStudioVersion` für diese Version der Tools ist „16.0“.

## <a name="updates"></a>Updates

MSBuild (und Visual Studio) zielt jetzt auf .NET Framework 4.7.2 ab. Wenn Sie die neuen MSBuild-API-Funktionen verwenden möchten, müssen Sie ebenfalls ein Upgrade Ihrer Assembly durchführen, wobei vorhandener Code aber weiterhin funktionsfähig bleibt.

## <a name="see-also"></a>Siehe auch
- [MSBuild](../msbuild/msbuild.md)
