---
title: Debuggen, indem Sie mit dem Store-Viewer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a76cd9b726e534271937cb67a8d3f946d4eb477
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433194"
---
# <a name="debugging-by-using-the-store-viewer"></a>Debuggen mithilfe der Speicheranzeige
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Store-Viewer, sehen Sie den Status einer *speichern* ein, die [!INCLUDE[dsl](../includes/dsl-md.md)]. Der Store-Viewer zeigt alle Elemente Modell mit der Domäne, die in einem bestimmten Speicher sowie Elementeigenschaften und Links zwischen Elementen sind.  
  
## <a name="opening-store-viewer"></a>Öffnen von Store-Viewer  
 Wenn Sie sind der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] experimentelle "erstellen", Ihren Code an einem Haltepunkt zu beenden, von denen Informationen zum Modell enthält einer Instanz des Speichers. Klicken Sie dann die Store-Viewer öffnen, indem Sie den folgenden Befehl in der **direkt** Fenster:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
> Ersetzen Sie `mystore` mit dem Namen Ihrer Store-Instanz. Wenn Sie den Namespace an Ihrem Code hinzufügen, können Sie auch den Befehl zum Anzeigen von Store-Viewer ohne den vollqualifizierten Namespace eingeben:  
>   
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
> `…`  
>   
> `StoreViewer.Show(mystore);`  
  
 Die `Show` -Methode weist mehrere Überladungen. Sie können eine Instanz von einem Store oder eine Partition als Parameter angeben.  
  
 Als Alternative können Sie die Codezeile, die an einer beliebigen Stelle der Store-Viewer in Ihrem Code zeigt einfügen, in dem der Parameter, die Sie zum Übergeben der `Show` -Methode wird in den Bereich. Diese Aktion wird im Store Viewer aus, wenn die Zeile des Codes als eine Momentaufnahme für den Inhalt des Speichers ausgeführt wird.  
  
### <a name="using-store-viewer"></a>Verwenden von Store-Viewer  
 Wenn der Store-Viewer geöffnet wird, wird ein nicht modales Fenster des Windows Forms als der folgenden Abbildung dargestellt angezeigt.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Store-Viewer  
  
 Der Store-Viewer verfügt über drei Bereiche: den linken Bereich oben rechts im Bereich und unteren rechten Bereich. Der linke Bereich ist eine Strukturansicht der Typen in der `DomainDataDirectory` Member eines Speichers. Wenn Sie erweitern Sie den partitionsknoten, und klicken Sie auf ein Element, werden die Eigenschaften des Elements in der oberen rechten Bereich angezeigt. Wenn das Element an andere Elemente verknüpft ist, werden die zusätzlichen Elemente im Bereich unten rechts angezeigt. Wenn Sie ein Element in der unteren rechten Bereich doppelklicken, wird das Element im linken Bereich hervorgehoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
