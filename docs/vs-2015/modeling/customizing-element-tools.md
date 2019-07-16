---
title: Anpassen von Elementtools | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 72457070c63cdf6c76207bd92521ab7944d4318a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199859"
---
# <a name="customizing-element-tools"></a>Anpassen von Elementtools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einigen DSL-Definitionen stellen Sie ein einmaliges Konzept als eine Gruppe von Elementen dar. Wenn Sie ein Modell erstellen, in dem eine Komponente über einen festen Satz von Ports verfügt, z. B. Sie immer die Ports, die zur gleichen Zeit wie die übergeordnete Komponente erstellt werden. Aus diesem Grund müssen Sie das Tool zur Erstellung von Element anpassen, sodass eine Gruppe von Elementen statt einem erstellt. Um dies zu erreichen, können Sie anpassen, wie das Tool zur Erstellung von Element initialisiert wird.  
  
 Sie können auch überschreiben, was geschieht, wenn das Tool auf das Diagramm oder ein Element gezogen wird.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>Anpassen des Inhalts eines Elementtools  
 Jedes Elementtool wird eine Instanz von einem <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), die eine serialisierte Version des einen oder mehrere Modellelemente und Links enthält. Standardmäßig enthält die EGP eines Elementtools eine Instanz der Klasse, die Sie für das Tool angeben. Sie können dies ändern, indem Sie überschreiben *Ihresprache*`ToolboxHelper.CreateElementToolPrototype`. Diese Methode wird aufgerufen, wenn die DSL-Paket geladen wird.  
  
 Ein Parameter der Methode ist die ID der Klasse, die Sie in der DSL-Definition angegeben. Wenn die Methode mit der Klasse, die Sie interessiert sind aufgerufen wird, können Sie zusätzliche Elemente in der EGP hinzufügen.  
  
 Die EGP muss Einbetten der Links von einem Haupt-Element für die untergeordneten Elemente enthalten. Sie können auch die Ressourcenlinks enthalten.  
  
 Das folgende Beispiel erstellt ein Hauptelement und zwei eingebetteten Elemente. "Main"-Klasse heißt Widerstand, und sie hat zwei einbettende Beziehungen zu Elementen, die mit dem Namen Terminal. Die einbettende Rolleneigenschaften heißen Terminal1 und Terminal2, und beide verfügen über die Multiplizität 1..1.  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Elementerstellung und -verschiebung](../modeling/customizing-element-creation-and-movement.md)
