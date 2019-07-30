---
title: 'Schritt 8: Anpassen des Quiz'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1868cd30cc41187ac995e71ee86d81dd0fb83d5a
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416462"
---
# <a name="step-8-customize-the-quiz"></a>Schritt 8: Anpassen des Quiz
Im letzten Teil des Lernprogramms untersuchen Sie mehrere Möglichkeiten, das Quiz anzupassen. Damit erweitern Sie Ihre bereits erworbenen Kenntnisse. Sie können z. B. überlegen, wie das Programm zufällige Divisionsaufgaben erstellt, für die die Antwort nie eine Bruchzahl ist. Um den Lerneffekt zu erhöhen, können Sie für das `timeLabel`-Steuerelement eine andere Farbe festlegen und dem Quizteilnehmer einen Hinweis geben.

## <a name="to-customize-the-quiz"></a>So passen Sie das Quiz an

- Ändern Sie die Farbe des Steuerelements **timeLabel** in Rot, wenn nur noch fünf Sekunden zur Durchführung des Quiz verbleiben. Legen Sie dazu die Eigenschaft **BackColor** für das Steuerelement fest.

```csharp
timeLabel.BackColor = Color.Red;
```

```vb
timeLabel.BackColor = Color.Red
```

Setzen Sie die Farbe zurück, wenn das Quiz vorbei ist.

- Geben Sie dem Quizteilnehmer einen Hinweis, indem Sie einen Sound wiedergeben, wenn in ein <xref:System.Windows.Forms.NumericUpDown>-Steuerelement die richtige Antwort eingegeben wird. (Sie müssen für jedes Steuerelement einen Ereignishandler für das <xref:System.Windows.Forms.NumericUpDown.ValueChanged>-Ereignis schreiben, das ausgelöst wird, wenn der Quizteilnehmer den Wert des Steuerelements ändert.)

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Informationen zum Herunterladen einer vollständigen Version des Quiz finden Sie unter [Complete math quiz tutorial sample (Tutorialbeispiel des vollständigen Mathequiz)](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

- Das nächste Tutorial finden Sie unter [Tutorial 3: Erstellen eines Vergleichsspiels](../ide/tutorial-3-create-a-matching-game.md).

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben](../ide/step-7-add-multiplication-and-division-problems.md).
