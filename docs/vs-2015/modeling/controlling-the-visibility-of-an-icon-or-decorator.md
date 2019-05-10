---
title: Steuern der Sichtbarkeit eines Symbols oder Decorator-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8d4dc21c2c6329730d678fa574f11d86bed8cdc4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107176"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Steuern der Sichtbarkeit eines Symbols oder Decorator-Elements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein *Decorator-Elements* ist ein Symbol oder eine Textzeile, die für eine Form in einer domänenspezifischen Sprache (DSL) angezeigt wird. Sie können das Decorator-angezeigt und nicht mehr angezeigt, abhängig von der Zustand der Eigenschaften im Modell. Für eine Form, die eine Person darstellt, können Sie z. B. unterschiedliche Symbole haben, die je nach Geschlecht der Person, die Anzahl der untergeordneten Elemente angezeigt werden und so weiter.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Steuern der Sichtbarkeit eines Symbols oder Decorator-Element  
 Das folgende Verfahren wird davon ausgegangen, dass Sie bereits eine Form vom Typ und seine Zuordnung zu einer Domänenklasse definiert haben. Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Steuern der Sichtbarkeit des ein Symbol oder Text-Decorator-Element  
  
1. Fügen Sie in der DSL-Definitionsdiagramm hinzu, die Shape-Klasse, die Symbole oder Text-Decorator-Elemente, die angezeigt werden sollen.  
  
   1. Mit der rechten Maustaste der formklasse, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf den erforderlichen Typ des Decorator-Elements.  
  
   2. Festlegen des Decorator-Elements **Position** Eigenschaft. Mehr als ein Decorator-Element kann die gleiche Position verfügen. Beispielsweise können Sie Symbole für "Männlich" und "weiblich", die gemeinsame Nutzung der gleichen Position haben.  
  
   3. Legen Sie die **Standardsymbol** Eigenschaft ein Symbol für Decorator-Elements.  
  
2. Wählen Sie die diagrammelementzuordnung, d.h. die graue Linie zwischen der Shape-Klasse und der Domänenklasse im DSL-Definitionsdiagramm.  
  
3. Im Fenster "DSL-Details" in der **Decorator-Zuordnungen** wählen ein Decorator-Element. Beispiel: die MaleDecorator.  
  
4. Überprüfen Sie die **Sichtbarkeitsfilter** Feld.  
  
5. Wenn die Eigenschaft "Domain", die die Sichtbarkeit zu steuern, sollten in der unmittelbaren Domänenklasse ist, lassen Sie **Pfad zur Filter-Eigenschaft** leer.  
  
    Andernfalls klicken Sie auf das Dropdownmenü, und navigieren Sie zu die Beziehung oder eine Klasse, die auf dem sich die Eigenschaft befindet.  
  
   - Um einen Fehlerbericht zu vermeiden, sollten Sie nicht über eine Beziehung mit markierten navigieren "*" in das Navigationstool.  
  
6. Legen Sie die **Filtereigenschaft** an einer Domäneneigenschaft. Beispielsweise Geschlecht.  
  
7. In der **Sichtbarkeitseinträge** aufzulisten, fügen Sie die Werte dieser Domäneneigenschaft, die für die das Decorator-Element angezeigt werden. Beispiel: "Männlich".  
  
8. Wiederholen Sie die Schritte für jedes Symbol ein.  
  
9. **Alle Vorlagen transformieren**, erstellen und auszuführen, und öffnen Sie ein Diagramm.  
  
10. Wenn Sie steuern den Wert der Eigenschaft ändern, sollte die Decorator-Elemente angezeigt werden und nicht mehr angezeigt.  
  
    In vielen Fällen möchten Sie die Sichtbarkeit durch eine komplexere Formel als einen einfachen Satz von Werten gesteuert werden. Beispielsweise ist ein Symbol auf der Anzahl der Links von einem bestimmten Typ abhängig sind, oder vereinfachen abhängig, ob eine Zahl in einem bestimmten Bereich. In diesem Fall verwenden Sie das folgende Verfahren an.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Um die Sichtbarkeit eines Decorator-Elements anhand einer Formel zu steuern.  
  
1. Fügen Sie eine berechnete Domäneneigenschaft, mit der Domänenklasse. In der **Eigenschaften** legen die folgenden Werte:  
  
     **IsBrowsable =**`False`**– Dadurch wird die Eigenschaft vom Benutzer ausgeblendet.**  
  
     **Art =**`Calculated`**– Dies bedeutet, dass Sie Code bereitstellen, die den Wert berechnet.**  
  
     **Namen** z. B. **DecoratorControl**  
  
     **Typ** = `Boolean`  
  
     Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).  
  
2. Stellen Sie die neue Eigenschaft, die die Decorator-Sichtbarkeit zu steuern.  
  
    1. Wählen Sie die diagrammelementzuordnung, d. h. die graue Linie aus der Domänenklasse mit der Form. In der **DSL-Details** geöffnete Fenster die **DecoratorMap** Registerkarte.  
  
    2. Überprüfen Sie die **Sichtbarkeitsfilter** Feld.  
  
    3. In **Filtereigenschaft**, wählen Sie die Steuerelementeigenschaft **DecoratorControl**.  
  
    4. Klicken Sie unter **Sichtbarkeitseinträge**, geben Sie `True`.  
  
3. Klicken Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer.  
  
4. Klicken Sie auf **Projektmappe** auf die **erstellen** Menü.  
  
5. Doppelklicken Sie auf den Fehlerbericht, der angezeigt wurde: "*Ihreklasse* enthält keine Definition für GetDecoratorControlValue...".  
  
     Text-Editor wird auf Dsl\GeneratedCode\DomainClasses.cs geöffnet. Über den hervorgehobenen Fehler befindet sich ein Kommentar, der Sie zum Hinzufügen einer Methode anfordert.  
  
6. Beachten Sie den Namespace, Klasse und Methode, die fehlen.  Beispiel: Company.FamilyTree.Person.GetDecoratorControlValue().  
  
7. Schreiben Sie in einer separaten Codedatei eine partielle Klassendefinition, die die fehlende Methode enthält. Zum Beispiel:  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     Weitere Informationen zum Anpassen des Modells mit Programmcode finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
8. Neu, und führen Sie die Projektmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von Formen und Konnektoren](../modeling/defining-shapes-and-connectors.md)   
 [Festlegen eines Hintergrundbilds in einem Diagramm](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Schreiben von Code zum Anpassen einer domänenspezifischen Sprache](../modeling/writing-code-to-customise-a-domain-specific-language.md)
