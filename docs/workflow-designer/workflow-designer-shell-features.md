---
title: Workflow-Designer-Shellfunktionen
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4519be8ec5c5d4ba8a611df1880ae770a83cf981
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433863"
---
# <a name="workflow-designer-shell-features"></a>Workflow-Designer-Shellfunktionen

Workflow-Designer besteht aus drei wesentlichen Bereiche der Benutzeroberfläche: der Designeroberfläche, der Breadcrumb-Leiste darüber und der Shell darunter. Die Breadcrumb-Leiste am oberen Fensterrand dient zur Anzeige der Vorgängerliste für die aktuelle Stammaktivität. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden der Brotkrümelnavigation](../workflow-designer/how-to-use-breadcrumb-navigation.md). Die Designeroberfläche im mittleren Bereich dient zum Erstellen von Workflows. Die Shell am unteren Fensterrand enthält eine Reihe von Schaltflächen zum Verwalten der aktuellen Ansicht.

## <a name="shell-features"></a>Shell-Funktionen
 Auf der rechten Seite der Shell-Leiste befinden sich Schaltflächen zum Vergrößern bzw. Verkleinern der Workflowgrafik, zum Anpassen des Workflowinhalts an die Bildschirmgröße und zum Einblenden bzw. Ausblenden der Übersichtskarte. Sie können die Workflowgrafik auch mit den Tastenkombinationen STRG++ und STRG+- vergrößern bzw. verkleinern.

## <a name="overview-map"></a>Übersichtskarte
 Die Übersichtskarte zeigt eine kleine Version der gesamten Aktivität des aktuellen Breadcrumb-Stamms an, einschließlich aller untergeordneten Elemente mit erweiterten untergeordneten Elementen. Der aktuell im Editor angezeigte Teil der Aktivität wird in einem Ansichtsfenster, einem Rechteck mit orangefarbenem Rahmen, hervorgehoben. Durch Ziehen des Rechtecks auf der Übersichtskarte können Sie im Workflow-Designer einen Bildlauf durchführen und die Ansicht des Editors ändern.

> [!NOTE]
> Die Workflow-Designer-Benutzeroberfläche ist virtualisiert. Die Aktivitätsdesigner werden nur nach Bedarf gerendert. Die Teile des Workflows, die auf der Designeroberfläche nicht gezeichnet wurden, werden in der Übersichtskarte weiß angezeigt. Um den Workflow vollständig zu zeichnen, führen Sie einen Bildlauf auf der Übersichtskarte durch.

## <a name="copying-or-saving-workflows-as-images"></a>Kopieren und Speichern von Workflows als Bilder
 Workflows können im Bitmapformat kopiert und im Bitmap- oder Vektorformat gespeichert werden. Das Kopieren bzw. Speichern eines Bilds bietet die Möglichkeit, eine Ansicht der gesamten Aktivität des aktuellen Breadcrumb-Stamms in ein anderes Programm zu exportieren, einschließlich aller untergeordneten Elemente und zugehörigen erweiterten untergeordneten Elemente.

 Um als Bild zu kopieren, mit der rechten Maustaste an einer beliebigen Stelle im Designer, und wählen Sie **als Bild kopieren**. Um als Bild speichern, mit der rechten Maustaste an einer beliebigen Stelle im Designer, und wählen Sie **als Bild speichern**. Workflows können in den Formaten JPG, PNG, GIF und XPS gespeichert werden. Das Format ausgewählt ist, auf die **speichern unter** im Dialogfeld die **Dateityp:** Dropdownliste am unteren Rand des Fensters.

## <a name="fonts-and-colors"></a>Schriftarten und Farben

Die im Workflow-Designer in Visual Studio verwendeten Schriftarten werden von der Umgebungsschriftart gesteuert. Die Farben im Workflow-Designer ändern, wenn Sie ein Farbschema für hohen Kontrast für Ihr Betriebssystem Design verwenden. Sie müssen Visual Studio neu starten, nach einer Änderung an den Schriftart- oder farbeinstellungen vorgenommen, bevor die Änderungen im Workflow-Designer wirksam.