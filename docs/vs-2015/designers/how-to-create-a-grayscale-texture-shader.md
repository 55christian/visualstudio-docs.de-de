---
title: 'Vorgehensweise: Erstellen eines Graustufentextur-Shaders | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b43e7806ebf6d67300fdee7be165c7cd745c4acb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431715"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Vorgehensweise: Erstellen eines Graustufentextur-Shaders
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird gezeigt, wie der Shader-Designer und die Directed Graph Shader Language (DGSL) zum Erstellen eines Graustufentextur-Shaders verwendet wird. Dieser Shader verändert die RGB-Farbwerte des Textursamples und verwendet es anschließend zusammen mit dem unveränderten Alphawert, um die endgültige Farbe festzulegen.  
  
## <a name="creating-a-grayscale-texture-shader"></a>Erstellen eines Graustufentextur-Shaders  
 Sie können einen Graustufentextur-Shader implementieren, indem Sie den Farbwert eines Textursamples ändern, bevor Sie es in die endgültige Ausgabefarbe schreiben.  
  
 Bevor Sie beginnen, stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.  
  
#### <a name="to-create-a-grayscale-texture-shader"></a>So erstellen Sie einen Graustufentextur-Shader  
  
1. Erstellen Sie einen Basistexturshader wie unter [Vorgehensweise: Erstellen eines Basistextur-Shaders](../designers/how-to-create-a-basic-texture-shader.md).  
  
2. Trennen Sie das Terminal **RGB** des Knotens **Textursample** vom Terminal **RGB** des Knotens **Endgültige Farbe**. Klicken Sie im Modus **Auswählen** auf das Terminal **RGB** des Knotens **Textursample** und anschließend auf **Link aufheben**. Dadurch wird Platz für den Knoten geschaffen, der im nächsten Schritt hinzugefügt wird.  
  
3. Fügen Sie einen Knoten **Entsättigen** in das Diagramm ein. Klicken Sie in der **Toolbox** unter **Filter** auf **Entsättigen**, und verschieben Sie es auf die Entwurfsoberfläche.  
  
4. Berechnen Sie den Graustufenwert mithilfe des Knotens **Entsättigen**. Verschieben Sie im Modus **Auswählen** das Terminal **RGB** des Knotens **Textursample** auf das Terminal **RGB** des Knotens **Entsättigen**.  
  
   > [!NOTE]
   > In der Standardeinstellung entsättigt der Knoten **Entsättigen** die Eingabefarbe vollständig und nutzt für die Graustufen-Konvertierung die normale Gewichtung der Leuchtdichte. Sie können ändern, wie sich der Knoten **Entsättigen** verhält, indem Sie entweder den Wert der Eigenschaft **Leuchtdichte** ändern, oder indem Sie die Eingabefarbe teilweise entsättigen. Bestimmen Sie einen Skalarwert im Bereich [0,1) für das Terminal **Prozent** des Knotens **Entsättigen**, um die Eingabefarbe teilweise zu entsättigen.  
  
5. Verbinden Sie den berechneten Graustufenwert mit der endgültige Farbe. Verschieben Sie das Terminal **Ausgabe** des Knotens **Entsättigen** auf das Terminal **RGB** des Knotens **Endgültige Farbe**.  
  
   In der folgenden Abbildung wird das fertige Shader-Diagramm sowie eine Vorschau eines Würfels gezeigt, auf dem der Shader angewandt wurde.  
  
> [!NOTE]
> In dieser Abbildung wird eine Ebene als Vorschauform verwendet, und eine Textur wurde angegeben, um den Effekt des Shaders besser zu veranschaulichen.  
  
 ![Shader-Diagramm und eine Vorschau seiner Effekte](../designers/media/digit-grayscale-effect.png "Digit-Grayscale-Effect")  
  
 Bestimmte Formen sorgen vielleicht für bessere Vorschauen für einige Shader. Weitere Informationen zur Verwendung der Vorschau von Shadern im Shader-Designer finden Sie unter [Shader-Designer](../designers/shader-designer.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anwenden eines Shaders auf ein 3D-Modell](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Vorgehensweise: Exportieren eines Shaders](../designers/how-to-export-a-shader.md)   
 [Bildbearbeitung](../designers/image-editor.md)   
 [Shader-Designer](../designers/shader-designer.md)   
 [Shader-Designer-Knoten](../designers/shader-designer-nodes.md)
