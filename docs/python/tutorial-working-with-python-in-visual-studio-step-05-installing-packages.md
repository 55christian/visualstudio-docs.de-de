---
title: 'Tutorial „Python in Visual Studio“, Schritt 5: Installieren von Paketen'
titleSuffix: ''
description: Dies ist Schritt 5 einer grundlegenden Einführung in die Arbeit mit Python in Visual Studio, in dem die Features von Visual Studio zum Verwalten von Paketen in einer Python-Umgebung veranschaulicht werden.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bf38def7be9607868df8f9c116266632ffcad710
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831200"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Schritt 5: Installieren von Paketen in Ihrer Python-Umgebung

**Vorheriger Schritt: [Ausführen von Code im Debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Die Python-Entwicklercommunity hat Tausende von nützlichen Paketen erzeugt, die Sie in Ihre eigenen Projekte integrieren können. Visual Studio bietet eine Benutzeroberfläche für das Verwalten von Paketen in Ihren Python-Umgebungen.

1. Wählen Sie den Menübefehl **Ansicht** > **Weitere Fenster** > **Python-Umgebungen** aus. Das Fenster **Python-Umgebungen** wird als Peer für den **Projektmappen-Explorer** geöffnet und zeigt die verschiedenen Umgebungen an, die für Sie verfügbar sind. Die Liste enthält die Umgebungen, die Sie mithilfe des Visual Studio-Installers installiert haben und die, die Sie separat installiert haben. Die Umgebung in Fettdruck ist die Standardumgebung, die für neue Projekte verwendet wird.

   ![Fenster „Python-Umgebungen“](media/environments/environments-default-view-blue.png)

2. Die Registerkarte **Übersicht** der Umgebung bietet schnellen Zugriff auf ein **interaktives** Fenster für diese Umgebung zusammen mit dem Installationsordner und den Interpretern der Umgebung. Klicken Sie beispielsweise auf **Interaktives Fenster öffnen**, und ein **interaktives** Fenster für diese bestimmte Umgebung wird in Visual Studio angezeigt.

3. Klicken Sie auf die Registerkarte **Pakete**, und Ihnen wird eine Liste der Pakete angezeigt, die derzeit in der Umgebung installiert sind.

   ![In einer Umgebung installierte Pakete](media/environments/environments-installed-packages-blue.png)

4. Installieren Sie `matplotlib`, indem Sie den Namen in das Suchfeld eingeben und dann **pip-Installation** auswählen.

   ![Installieren von matplotlib in der Umgebung](media/environments/environments-add-matplotlib1.png)

5. Stimmen Sie zu, wenn Sie zur Erhöhung der Rechte aufgefordert werden.

6. Nachdem das Paket installiert ist, wird es im Fenster der **Python-Umgebung** angezeigt. Über das **X** auf der rechten Seite des Pakets kann dieses deinstalliert werden.

   ![Abschließen der Installation von matplotlib in der Umgebung](media/environments/environments-add-matplotlib2.png)

   Unterhalb der Umgebung wird möglicherweise eine kleine Statusanzeige eingeblendet, um darauf hinzuweisen, dass Visual Studio die IntelliSense-Datenbank für neu installierte Pakete erstellt. Die Registerkarte **IntelliSense** zeigt ausführlichere Informationen an. Beachten Sie, dass IntelliSense-Funktionen wie die automatische Vervollständigung und die Syntaxüberprüfung für dieses Paket nicht im Editor aktiv sind, bis die Datenbank vollständig erstellt ist.

   Beachten Sie, dass Visual Studio 2017 Version 15.6 und höher eine andere und schnellere Methode für die Arbeit mit IntelliSense verwendet, und zeigen Sie eine diesbezügliche Meldung auf der **IntelliSense**-Registerkarte an.

7. Erstellen Sie ein Projekt, indem Sie auf **Datei** > **Neu** > **Projekt** klicken und die Vorlage **Python-Anwendung** auswählen. Fügen Sie folgenden Code in die angezeigte Codedatei ein. Dadurch wird eine Kosinuswelle wie in den vorherigen Schritten des Tutorials erstellt, die dieses Mal jedoch grafisch dargestellt wird:

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

8. Führen Sie das Programm mit (**F5**) oder ohne Debugger (**STRG**+**F5**) aus, um die Ausgabe anzuzeigen:

   ![Ausgabe des matplotlib-Beispiels](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Arbeiten mit Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Ausführlichere Informationen

- [Python-Umgebungen](managing-python-environments-in-visual-studio.md)
