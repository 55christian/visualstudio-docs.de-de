---
title: Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 05a7b50c15c3bc1953e4be3d13809fd9db64f052
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435016"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die Elemente und Beziehungen in Ebenenmodellen beschrieben, die Sie mithilfe von Programmcode durchsuchen und aktualisieren können. Weitere Informationen zu Ebenendiagrammen aus Sicht des Benutzers, finden Sie unter [Ebenendiagramme: Verweis](../modeling/layer-diagrams-reference.md) und [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md).  
  
 Das in diesem Thema beschriebene <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer>-Modell ist eine Fassade eines allgemeineren <xref:Microsoft.VisualStudio.GraphModel>-Modells. Wenn Sie schreiben eine [menüerweiterung Befehls- oder Gestenhandlerprojekts](../modeling/add-commands-and-gestures-to-layer-diagrams.md), verwenden Sie die `Layer` Modell. Wenn Sie schreiben eine [layer validierungserweiterung](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), es ist einfacher zu verwenden die `GraphModel`.  
  
## <a name="transactions"></a>Transaktionen  
 Erwägen Sie beim Aktualisieren eines Modells die Änderungen in eine `ILinkedUndoTransaction` einzuschließen. Auf diese Weise werden die Änderungen zu einer Transaktion gruppiert. Wenn eine der Änderungen fehlschlägt, wird die gesamte Transaktion zurückgesetzt. Wenn der Benutzer eine Änderung rückgängig macht, werden alle Änderungen zusammen rückgängig gemacht.  
  
 Weitere Informationen finden Sie unter [Link UML-modellaktualisierungen mithilfe von Transaktionen](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Kapselung  
 ![ILayer und ILayerModel können beide ILAYER enthalten. ](../modeling/media/layerapi-containment.png "LayerApi_Containment")  
  
 Ebenen (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) und das Ebenenmodell (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) können Kommentare und Ebenen enthalten.  
  
 Eine Ebene (`ILayer`) kann in einem Ebenenmodell (`ILayerModel`) enthalten sein oder in einer anderen `ILayer` geschachtelt werden.  
  
 Verwenden Sie die Erstellungsmethoden für den entsprechenden Container, um einen Kommentar oder eine Ebene zu erstellen.  
  
## <a name="dependency-links"></a>Abhängigkeitslinks  
 Ein Abhängigkeitslink wird durch ein Objekt dargestellt. Er kann in beide Richtungen navigiert werden:  
  
 ![Ein ILayerDependencyLink verbindet zwei ILAYER. ](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")  
  
 Rufen Sie `source.CreateDependencyLink(target)` auf, um einen Abhängigkeitslink zu erstellen.  
  
## <a name="comments"></a>Kommentare  
 Kommentare können auf Ebenen oder im Ebenenmodell enthalten sein. Zudem können sie mit beliebigen anderen Ebenenelementen verknüpft werden:  
  
 ![Kommentare können jedem Ebenenelement angefügt werden. ](../modeling/media/layerapi-comments.png "LayerApi_Comments")  
  
 Ein Kommentar kann mit einer beliebigen Anzahl von Elementen sowie auch mit keinem Element verknüpft werden.  
  
 Verwenden Sie Folgendes, um die Kommentare abzurufen, die einem Ebenenelement zugeordnet sind:  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
> Die `Comments`-Eigenschaft einer `ILayer` ruft die Kommentare ab, die in `ILayer` enthalten sind. Es werden nicht die mit ihr verknüpften Kommentare abgerufen.  
  
 Erstellen Sie einen Kommentar, indem Sie `CreateComment()` im entsprechenden Container aufrufen.  
  
 Erstellen Sie einen Link, indem Sie `CreateLink()` auf den Kommentar anwenden.  
  
## <a name="layer-elements"></a>Ebenenelemente  
 Alle Elementtypen, die in einem Modell enthalten sein können, sind Ebenenelemente:  
  
 ![Ebene Diagramm Inhalt sind ILayerElements. ](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Eigenschaften  
 Jedes `ILayerElement` verfügt über ein Zeichenfolgenwörterbuch namens `Properties`. Über dieses Wörterbuch können Sie willkürliche Informationen an ein beliebiges Ebenenelement anfügen.  
  
## <a name="artifact-references"></a>Artefaktverweise  
 Ein Artefaktverweis (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) stellt den Link zwischen einer Ebene und einem Projektelement dar, z. B. einer Datei, einer Klasse oder einem Ordner. Der Benutzer erstellt Artefakte, wenn er eine Ebene erstellt oder dieser Elemente hinzufügt, indem er Elemente aus dem Projektmappen-Explorer, der Klassenansicht oder dem Objektkatalog in ein Ebenendiagramm zieht. Mit einer Ebene kann eine beliebige Anzahl von Artefaktverweisen verknüpft werden.  
  
 Jede Zeile im Ebenen-Explorer zeigt einen Artefaktverweis an. Weitere Informationen finden Sie unter [Erstellen von Ebenendiagrammen aus Ihrem Code](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Folgende hauptsächliche Typen und Methoden sind von Artefaktverweisen betroffen:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Die Eigenschaft "Kategorien" gibt an, welche Art von Artefakt referenziert wird, z. B. Klasse, ausführbare Datei oder Assembly. Die Kategorien bestimmen, wie der Bezeichner das Zielartefakt identifiziert.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> erstellt einen Artefaktverweis über ein <xref:EnvDTE.Project> oder <xref:EnvDTE.ProjectItem>. Das ist ein asynchroner Vorgang. Daher stellen Sie normalerweise einen Rückruf bereit, der nach Abschluss der Erstellung aufgerufen wird.  
  
 Ebenenartefaktverweise dürfen nicht mit Artefakten in Anwendungsfalldiagrammen verwechselt werden.  
  
## <a name="shapes-and-diagrams"></a>Formen und Diagramme  
 Es werden zwei Objekte verwendet, um die einzelnen Elemente in einem Ebenenmodell darzustellen: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> und <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` stellt Position und Größe der Form auf dem Diagramm dar. In Ebenenmodellen verfügt jedes `ILayerElement` über ein `IShape`, und jedes `IShape` in einem Ebenendiagramm besitzt ein `ILayerElement`. `IShape` wird auch für UML-Modelle verwendet. Daher verfügt nicht jedes `IShape` über ein Ebenenelement.  
  
 Auf dieselbe Weise wird <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> für ein <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> angezeigt.  
  
 Im Code eines benutzerdefinierten Befehl- oder Gestenhandlers können Sie das aktuelle Diagramm und die aktuelle Formenauswahl aus dem `DiagramContext`-Import abrufen:  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Jedes ILayerElement wird durch eine IShape angegeben. ](../modeling/media/layerapi-shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> und <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> werden auch zum Anzeigen von UML-Modellen verwendet. Weitere Informationen finden Sie unter [anzeigen ein UML-Modells in Diagrammen](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Befehlen und Bewegungen zu Ebenendiagrammen](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Hinzufügen einer benutzerdefinierten architekturvalidierung zu Ebenendiagrammen](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Fügen Sie benutzerdefinierter Eigenschaften zu Ebenendiagrammen hinzu](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Ebenendiagramme: Referenz](../modeling/layer-diagrams-reference.md)   
 [Ebenendiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)   
 [Erweitern von UML-Modellen und -Diagrammen](../modeling/extend-uml-models-and-diagrams.md)
