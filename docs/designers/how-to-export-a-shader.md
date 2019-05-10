---
title: 'Vorgehensweise: Exportieren eines Shaders'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d0a962fe941f676369c4c3575647610df809d58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844396"
---
# <a name="how-to-export-a-shader"></a>Vorgehensweise: Exportieren eines Shaders

Dieser Artikel zeigt, wie Sie mit dem **Shader-Designer** einen DGSL-Shader (Directed Graph Shader Language) exportieren, um ihn in Ihrer App zu verwenden.

## <a name="export-a-shader"></a>Exportieren eines Shaders

Nachdem Sie einen Shader mithilfe des Shader-Designers erstellt haben, und bevor Sie ihn in Ihrer Anwendung verwenden können, müssen Sie den Shader in einem Format exportieren, das Ihre Grafik-API versteht. Sie können einen Shader auf unterschiedliche Weisen für andere Anforderungen exportieren.

1. Öffnen Sie in Visual Studio eine DGSL-Datei vom Typ **visuelles Shaderdiagramm**.

     Wenn keine **DGSL**-Datei (Visual Shader Graph) zum Öffnen vorhanden ist, erstellen Sie eine. Gehen Sie hierzu vor, wie unter [Vorgehensweise: Erstellen eines einfachen Farbshaders](../designers/how-to-create-a-basic-color-shader.md) beschrieben.

2. Klicken Sie auf der Symbolleiste des **Shader-Designers** auf **Erweitert** > **Exportieren** > **Exportieren als**. Das Dialogfeld **Shader exportieren** wird angezeigt.

3. Wählen Sie in der Dropdownliste **Dateityp** das Format aus, in das Sie exportieren möchten.

     Sie können die folgende Formate auswählen:

     **HLSL-Pixelshader (\*.hlsl):** Exportiert den Shader als HLSL-Quellcode (High Level Shader Language). Diese Option ermöglicht es, den Shader später zu ändern, auch nachdem er in einer Anwendung bereitgestellt wird. Dies kann das Debuggen und Patchen des Codes aufgrund der Probleme bei dem Endbenutzer vereinfachen, erleichtert es dem Benutzer aber genau so Ihren Shader auf ungewünschter Weise zu verändern, z.B. um einen unfairen Vorteil in einem wetteifernden Spiel zu erhalten. Es kann auch die Ladezeiten des Shaders erhöhen.

     **Kompilierter Pixelshader (\*.cso):** Exportiert den Shader als HLSL-Bytecode. Diese Option ermöglicht es, den Shader später zu ändern, auch nachdem er in einer Anwendung bereitgestellt wird. Dies erleichtert das Debuggen und Patchen des Codes aufgrund der Probleme beim Endbenutzer. Da der Shader jedoch vorkompiliert ist, verursacht es keinen zusätzlichen Mehraufwand bei der Laufzeit, wenn der Shader von der Anwendung geladen wird. Ausreichend erfahrene Benutzer können weiterhin den Shader auf unerwünschter Weise ändern, aber das Kompilieren des Shaders erschwert das Ganze erheblich.

     **C++-Header (\*.h):** Exportiert den Shader als Header im C-Stil, der ein Bytearray definiert, das HLSL-Bytecode enthält. Diese Option kann das Debuggen und Patchen des Codes aufgrund der Probleme beim Endnutzer zeitaufwändiger gestalten, da die App erneut kompiliert werden muss, um den Fix zu testen. Da diese Option es jedoch schwierig, aber nicht unmöglich macht, den Shader nach seiner Bereitstellung in einer App zu verändern, bereitet es für einen Benutzer, der den Shader auf unerwünschte Weise verändern möchte, die meisten Probleme.

4. Geben Sie im Kombinationsfeld **Dateiname** einen Namen für den exportierten Shader an, und klicken Sie auf die Schaltfläche **Speichern**

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen eines einfachen Farbshaders](../designers/how-to-create-a-basic-color-shader.md)
- [Shader-Designer](../designers/shader-designer.md)