---
title: 'Schritt 5: Hinzufügen von Bezeichnungsverweisen'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a1fe8f4e8003da2db0e8a599c3eca504945f3e4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647521"
---
# <a name="step-5-add-label-references"></a>Schritt 5: Hinzufügen von Bezeichnungsverweisen
Das Programm muss nachverfolgen, welches Bezeichnungsfeld der Spieler wählt. Bisher zeigt das Programm alle Bezeichnungsfelder an, die der Spieler ausgewählt hat. Wir werden das ändern. Nachdem das erste Bezeichnungsfeld gewählt wurde, sollte das Programm das Symbol im Bezeichnungsfeld anzeigen. Nachdem das zweite Bezeichnungsfeld ausgewählt ist, sollte das Programm beide Symbole für eine kurze Zeit anzeigen und dann beide wieder ausblenden. Das Programm verfolgt nun mithilfe von *Verweisvariablen*, welches Bezeichnungsfeld zuerst und welches danach gewählt wird.

## <a name="to-add-label-references"></a>So fügen Sie Bezeichnungsverweise hinzu

1. Fügen Sie dem Formular Bezeichnungsverweise hinzu, indem Sie den folgenden Code verwenden.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > Verwenden Sie das Programmiersprachensteuerelement oben rechts auf dieser Seite, um entweder den C#-Codeausschnitt oder den Visual Basic-Codeausschnitt anzuzeigen.<br><br>![Programmiersprachensteuerelement auf docs.microsoft.com](../ide/media/docs-programming-language-control.png)

     Diese Verweisvariablen ähneln im Aussehen den Anweisungen, mit denen Sie zuvor dem Formular Objekte (wie <xref:System.Windows.Forms.Timer>, <xref:System.Collections.Generic.List%601> und <xref:System.Random>) hinzugefügt haben. Diese Anweisungen bewirken jedoch nicht, dass im Formular zwei zusätzliche Bezeichnungsfelder angezeigt werden, da das Schlüsselwort `new` in keiner der beiden Anweisungen enthalten ist. Ohne das `new`-Schlüsselwort wird kein Objekt erstellt. Deshalb werden `firstClicked` und `secondClicked` als Verweisvariablen bezeichnet: weil sie einfach Bezeichnungsobjekte nachverfolgen (oder auf diese verweisen).

     Wenn eine Variable keinen Verweis auf ein Objekt enthält, wird sie auf einen besonderen Wert festgelegt: `null` in C# und `Nothing` in Visual Basic. Beim Starten des Programms erhalten also sowohl `firstClicked` als auch `secondClicked` den Wert `null` bzw. `Nothing`. Dies bedeutet, dass die Variablen keine Objektverweise enthalten.

2. Ändern Sie den <xref:System.Windows.Forms.Control.Click>-Ereignishandler so, dass er die neue `firstClicked`-Verweisvariable verwendet. Entfernen Sie die letzte Anweisung in der `label_Click()`-Ereignishandlermethode (`clickedLabel.ForeColor = Color.Black;`), und ersetzen Sie diese durch die `if`-Anweisung, die darauf folgt. (Achten Sie darauf, den Kommentar und die gesamte `if`-Anweisung einzufügen.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Speichern Sie das Programm, und führen Sie es aus. Wählen Sie eines der Bezeichnungsfelder. Das entsprechende Symbol wird angezeigt.

4. Wählen Sie das nächste Bezeichnungsfeld. Sie werden bemerken, dass nichts passiert. Das Programm merkt sich bereits das erste Bezeichnungsfeld, auf das der Spieler geklickt hat, `firstClicked` entspricht also nicht `null` (in C#) bzw. `Nothing` (in Visual Basic). Wenn die `if`-Anweisung `firstClicked` darauf überprüft, ob sie `null` oder `Nothing` entspricht, stellt sie fest, dass dies nicht der Fall ist. Die Anweisungen in der `if`-Anweisung werden also nicht ausgeführt. Deshalb wird nur die Farbe für das erste gewählte Symbol in Schwarz geändert. Die anderen Symbole bleiben ausgeblendet. Dies ist in der folgenden Abbildung dargestellt.

     ![Anzeige eines Symbols im Vergleichsspiel](../ide/media/express_tut4step5.png)<br/>
***Anzeigen eines Symbols*** *im Vergleichsspiel*

     Sie beheben diese Situation im nächsten Tutorialschritt, indem Sie ein **Timer**-Steuerelement hinzufügen.

## <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben

- Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 6: Hinzufügen von Timern](../ide/step-6-add-a-timer.md)** .

- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 4: Hinzufügen eines Click-Ereignishandlers zu jeder Bezeichnung](../ide/step-4-add-a-click-event-handler-to-each-label.md).
