---
title: 'Schritt 8: Anpassen des Quiz | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6084daea11d981477bbee6f210e1faf718b58d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646920"
---
# <a name="step-8-customize-the-quiz"></a>Schritt 8: Anpassen des Quiz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im letzten Teil des Lernprogramms untersuchen Sie mehrere Möglichkeiten, das Quiz anzupassen. Damit erweitern Sie Ihre bereits erworbenen Kenntnisse. Sie können z. B. überlegen, wie das Programm zufällige Divisionsaufgaben erstellt, für die die Antwort nie eine Bruchzahl ist. Um den Lerneffekt zu erhöhen, können Sie für das `timeLabel`-Steuerelement eine andere Farbe festlegen und dem Quizteilnehmer einen Hinweis geben.

### <a name="to-customize-the-quiz"></a>So passen Sie das Quiz an

- Ändern Sie das Steuerelement **timeLabel** in Rot, wenn nur noch fünf Sekunden zur Durchführung des Quiz verbleiben. Legen Sie dazu die Eigenschaft **BackColor** (`timeLabel.BackColor = Color.Red;`) für das Steuerelement fest. Setzen Sie die Farbe zurück, wenn das Quiz vorbei ist.

- Geben Sie dem Quizteilnehmer einen Hinweis, indem Sie einen Sound wiedergeben, wenn in ein NumericUpDown-Steuerelement die richtige Antwort eingegeben wird. (Sie müssen für jedes Steuerelement einen Ereignishandler für das `ValueChanged()`-Ereignis schreiben, das ausgelöst wird, wenn der Quizteilnehmer den Wert des Steuerelements ändert.)

### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Informationen zum Herunterladen einer vollständigen Version des Quiz finden Sie unter [Tutorialbeispiel des vollständigen Mathequiz](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

- Um zum nächsten Tutorial zu wechseln, klicken Sie auf [Tutorial 3: Erstellen eines Vergleichsspiels](../ide/tutorial-3-create-a-matching-game.md).

- Um zum vorhergehenden Schritt des Tutorials zurückzukehren, klicken Sie auf [Schritt 7: Hinzufügen von Multiplikations- und Divisionsaufgaben](../ide/step-7-add-multiplication-and-division-problems.md).
