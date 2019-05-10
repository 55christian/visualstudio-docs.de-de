---
title: 'Vorgehensweise: Ändern des Pivotpunkts eines 3D-Modells | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a89e06fad1e47e3c2fd7be565acab9d94e3f29d5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434434"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Vorgehensweise: Ändern des Pivotpunkts eines 3D-Modells
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dokument wird gezeigt, wie der Modell-Editor zum Ändern des *Pivotpunkts* eines 3D-Modells verwendet wird. Der Pivotpunkt ist der Punkt im Raum, der das mathematische Zentrum des Objektes für Rotation und Skalierung definiert.  
  
 In diesem Dokument wird die folgende Aktivität veranschaulicht:  
  
- Ändern der Pivotpunkt eines Objekts  
  
## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>Ändern der Pivotpunkt eines 3D-Modells  
 Sie können den Ursprung eines 3D-Modells durch Ändern seines Pivotpunkts neu definieren.  
  
 Stellen Sie sicher, dass das Fenster **Eigenschaften** und die **Toolbox** angezeigt werden.  
  
#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>So ändern Sie den Pivotpunkt eines 3D-Modells  
  
1. Beginnen Sie mit einer vorhandenen 3D-Modell wie diejenige, die in beschriebenen [Vorgehensweise: Erstellen ein 3D-Basismodells](../designers/how-to-create-a-basic-3-d-model.md).  
  
2. Gehen Sie in den Pivot-Modus. Klicken Sie zum Aktivieren des Pivot-Modus auf der Symbolleiste **Model-Editor-Modus** auf **Pivot-Modus**. Es erscheint ein Feld um die Schaltfläche **Pivot-Modus**, der angibt, dass der Modell-Editor sich nun im Pivot-Modus befindet. Vorgänge wie die Verschiebung beeinflussen im Pivot-Modus den Pivotpunkt des Objektes anstatt der Struktur des Objektes im Raum.  
  
3. Ändern Sie den Pivotpunkt des Objekts. Klicken Sie im Modus **Auswählen** auf das Objekt und anschließend auf der Symbolleiste des **Modell-Viewers** auf das Tool **Verschieben**. Ein Feld, das den Pivotpunkt darstellt, wird auf der Entwurfsoberfläche angezeigt. Verschieben Sie das Feld, um den Pivotpunkt des Objekts zu ändern.  
  
    Durch das Verschieben des Felds können Sie den Pivopunkt in alle drei Dimensionen verschieben. Zum Verschieben des Pivotpunkts entlang einer Achse, verschieben Sie den Pfeil, der dieser Ache entspricht Das Feld und die Pfeile wechseln in eine gelbe Farbe, um die Achse anzugeben, die von der Verschiebung betroffen sind.  
  
    Sie können auch den Pivotpunkt angeben, indem Sie die Eigenschaft **Pivot-Bewegung** im Fenster **Eigenschaften** verwenden.  
  
   > [!TIP]
   > Sie können den Effekt des neuen Pivotpunkts durch Rotieren des Objekts betrachten. Verwenden Sie zum Drehen des Objekts das Tool **Drehen**, oder ändern Sie die Eigenschaft **Drehung**.  
  
   Hier finden Sie ein Modell, dass einen geänderten Pivotpunkt hat:  
  
   ![Modell eines Hauses mit einem geänderten Pivotpunkt](../designers/media/digit-modified-model.png "Digit-Modified-Model")  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen eines 3D-Basismodells](../designers/how-to-create-a-basic-3-d-model.md)   
 [Modell-Editor](../designers/model-editor.md)
