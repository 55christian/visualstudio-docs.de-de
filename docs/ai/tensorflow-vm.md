---
title: Ausführen eines TensorFlow-Modells in der Cloud
description: Ausführen eines TensorFlow-Modells auf einem virtuellen Azure-Computer für Deep Learning
keywords: KI, Visual Studio, virtuelle Computer für Deep Learning
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: tutorial
ms.devlang: python
ms.workload:
- multiple
ms.openlocfilehash: adb3720f1624f355b99d75bfe446fafab1c5e0ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62427575"
---
# <a name="train-a-tensorflow-model-in-the-cloud"></a>Trainieren eines TensorFlow-Modells in der Cloud

In diesem Tutorial wird ein TensorFlow-Modell mithilfe des [MNIST-Datasets](http://yann.lecun.com/exdb/mnist/) auf einem virtuellen Azure-Computer mit [Deep Learning](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview) trainiert.

Die MNIST-Datenbank enthält 60.000 Trainingsbeispiele und 10.000 Testbeispiele für handgeschriebene Ziffern.

## <a name="prerequisites"></a>Erforderliche Komponenten
Stellen Sie vor Beginn sicher, dass Sie Folgendes installiert und konfiguriert haben:

### <a name="setup-azure-deep-learning-virtual-machine"></a>Einrichten des virtuellen Azure-Computers mit Deep Learning

> [!NOTE]
> Legen Sie den **Betriebssystemtyp** auf „Linux“ fest.

Weitere Anweisungen zum Einrichten eines virtuellen Computers mit Deep Learning finden Sie [hier](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-deep-learning-dsvm).

### <a name="remove-comment-in-parens"></a>Entfernen des Kommentars in Klammern

```bash
echo -e ". /etc/profile\n$(cat ~/.bashrc)" > ~/.bashrc
```

### <a name="download-sample-code"></a>Herunterladen von Beispielcode

Laden Sie dieses [GitHub-Repository](https://github.com/Microsoft/samples-for-ai) herunter, das Beispiele für die ersten Schritte mit Deep Learning in TensorFlow, CNTK, Theano usw. enthält.

## <a name="open-project"></a>Öffnen des Projekts

- Starten Sie Visual Studio, und klicken Sie auf **Datei > Öffnen> Projekt/Projektmappe**.

- Öffnen Sie den Ordner **Tensorflow Examples** (TensorFlow-Beispiele) aus dem heruntergeladenen Beispielrepository, und öffnen Sie die Datei **TensorflowExamples.sln**.

   ![Öffnen des Projekts](media/tensorflow-local/open-project.png)

   ![Öffnen der Projektmappe](media/tensorflow-local/open-solution.png)

## <a name="add-azure-remote-vm"></a>Hinzufügen eines virtuellen Azure-Remotecomputers

Klicken Sie im Server-Explorer mit der rechten Maustaste auf den Knoten **Remotecomputer** unter dem Knoten „KI-Tools“, und klicken Sie auf „Hinzufügen...“. Geben Sie den Anzeigenamen, IP-Host, SSH-Port, Benutzernamen und die Kennwort-/Schlüsseldatei des Remotecomputers ein.

![Hinzufügen eines neuen Remotecomputers](media/tensorflow-vm/add-remote-vm.png)

## <a name="submit-job-to-azure-vm"></a>Übermitteln eines Auftrags an einen virtuellen Azure-Computer
Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das MNIST-Projekt und dann auf **Auftrag übermitteln**.

![Übermittlung des Auftrags an einen Remotecomputer](media/tensorflow-vm/job-submission.png)

Führen Sie im Übermittlungsfenster Folgendes aus:

- Wählen Sie den Remotecomputer (mit dem Präfix „rm:“) aus der Liste **Cluster verwenden** aus, an den der Auftrag übermittelt werden soll.

- Geben Sie einen **Auftragsnamen** ein.

- Klicken Sie auf **Senden**.

## <a name="check-status-of-job"></a>Überprüfen des Auftragsstatus
Erweitern Sie den virtuellen Computer im **Server-Explorer**, dem Sie den Auftrag übermittelt haben, um den Status und die Details des Auftrags anzuzeigen. Doppelklicken Sie auf **Aufträge**.

![Auftragsbrowser](media/tensorflow-vm/job-browser.png)

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Beenden Sie den virtuellen Computer, wenn Sie diesen in naher Zukunft verwenden möchten. Wenn Sie dieses Tutorial abgeschlossen haben, führen Sie folgenden Befehl aus, um Ihre Ressourcen zu bereinigen:

```azurecli-interactive
az group delete --name myResourceGroup
```
