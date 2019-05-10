---
title: 'Schritt 4: Hinzufügen ein Click-Ereignishandlers zu jeder Bezeichnung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 763aa2c73effdb1f7daf86c18e6033f03bef5108
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434036"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Schritt 4: Hinzufügen eines Click-Ereignishandlers zu jeder Bezeichnung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Vergleichsspiel funktioniert wie folgt:  
  
1. Wenn ein Spieler eines der Quadrate mit einem ausgeblendeten Symbol wählt, zeigt das Programm dem Spieler das Symbol an, indem es die Symbolfarbe in Schwarz ändert.  
  
2. Dann wählt der Spieler ein anderes ausgeblendetes Symbol.  
  
3. Wenn die Symbole übereinstimmen, bleiben sie sichtbar. Falls nicht, werden beide Symbole wieder ausgeblendet.  
  
   Damit das Programm sich wie beschrieben verhält, fügen Sie einen Click-Ereignishandler hinzu, der die Farbe des gewählten Bezeichnungsfelds ändert.  
  
### <a name="to-add-a-click-event-handler-to-each-label"></a>So fügen Sie jeder Bezeichnung einen Click-Ereignishandler hinzu  
  
1. Öffnen Sie das Formular im Windows Forms-Designer. Wählen Sie Form1.cs oder Form1.vb im Projektmappen-Explorer. Wählen Sie in der Menüleiste **Ansicht**, **Designer**.  
  
2. Wählen Sie das erste Bezeichnungsfeld-Steuerelement, um es zu markieren. Halten Sie dann die STRG-TASTE gedrückt, während Sie nacheinander die anderen Bezeichnungsfelder wählen. Achten Sie darauf, dass jede Bezeichnung ausgewählt wird.  
  
3. Wählen Sie die Schaltfläche **Ereignisse** auf der Symbolleiste im Fenster **Eigenschaften**, um die Seite **Ereignisse** im Fenster **Eigenschaften** anzuzeigen. Führen Sie einen Bildlauf nach unten bis zum **Click**-Ereignis durch, und geben Sie **label_Click** ein, wie in der folgenden Abbildung dargestellt.  
  
     ![Anzeige des Click-Ereignisses im Eigenschaftenfenster](../ide/media/express-labelclick.png "Express_labelClick")  
Anzeige des Click-Ereignisses im Eigenschaftenfenster  
  
4. Wählen Sie anschließend die EINGABETASTE. Die IDE fügt dem Code einen Click-Ereignishandler mit dem Namen `label_Click()` hinzu und verknüpft diesen mit jedem Bezeichnungsfeld im Formular.  
  
5. Fügen Sie den Rest des Codes wie folgt ein:  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#4)]  
  
    > [!NOTE]
    > Wenn Sie den `label_Click()`-Codeblock nicht manuell eingeben, sondern ihn kopieren und einfügen, achten Sie darauf, den vorhandenen `label_Click()`-Code zu ersetzen. Andernfalls erhalten Sie einen doppelten Codeblock.  
  
    > [!NOTE]
    > Wie Sie möglicherweise bemerkt haben, ist `object sender` am Anfang des Ereignishandlers derselbe wie in [Tutorial 2: Erstellen eines Mathequiz](../ide/tutorial-2-create-a-timed-math-quiz.md) Tutorial. Da Sie verschiedene Click-Ereignisse von Bezeichnungsfeld-Steuerelementen mit einer einzelnen Ereignishandlermethode verknüpft haben, wird immer diese Methode aufgerufen, unabhängig davon, welches Bezeichnungsfeld der Benutzer wählt. Die Ereignishandlermethode muss wissen, welche Bezeichnung ausgewählt wurde, und verwendet den **Sender**-Namen, um das Steuerelement zu identifizieren. Die erste Zeile der Methode teilt dem Programm mit, dass es sich nicht nur um ein generisches Objekt handelt, sondern ausdrücklich um ein Bezeichnungsfeld-Steuerelement, und dass zum Zugreifen auf dessen Eigenschaften und Methoden der Name **clickedLabel** verwendet wird.  
  
     Diese Methode überprüft zuerst, ob **clickedLabel** erfolgreich von einem Objekt in ein Bezeichnungsfeld-Steuerelement umgewandelt wurde. Falls hierbei ein Fehler auftritt, lautet der Wert `null` (C#) bzw. `Nothing` (Visual Basic). Der Rest des Codes in der Methode soll dann nicht mehr ausgeführt werden. Als Nächstes überprüft die Methode mithilfe der **ForeColor**-Eigenschaft die Textfarbe des gewählten Bezeichnungsfelds. Wenn die Textfarbe des Bezeichnungsfelds Schwarz ist, wurde das Symbol bereits ausgewählt und die Methode muss abgebrochen werden. (Dies ist Aufgabe der `return`-Anweisung: Sie weist das Programm an, die Ausführung der Methode zu beenden.) Andernfalls ist das Symbol nicht ausgewählt worden, und das Programm ändert die Textfarbe des Bezeichnungsfelds in Schwarz.  
  
6. Wählen Sie in der Menüleiste **Datei** die Option **Alle speichern**, um Ihre Arbeit zu speichern, und wählen Sie dann in der Menüleiste **Debuggen** die Option **Debuggen starten**, um das Programm auszuführen. Es wird ein leeres Formular mit einem blauen Hintergrund angezeigt. Wählen Sie eine der Zellen im Formular, und eines der Symbole sollte sichtbar werden. Setzten Sie die Auswahl mit anderen Stellen im Formular fort. Wenn Sie die Symbole wählen, sollten diese angezeigt werden.  
  
### <a name="to-continue-or-review"></a>So fahren Sie fort oder überprüfen die Angaben  
  
- Den nächsten Schritt des Tutorials finden Sie unter [Schritt 5: Hinzufügen von Bezeichnungsverweisen](../ide/step-5-add-label-references.md).  
  
- Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 3: Zuweisen ein zufällig ausgewählten Symbols zu jeder Bezeichnung](../ide/step-3-assign-a-random-icon-to-each-label.md).
