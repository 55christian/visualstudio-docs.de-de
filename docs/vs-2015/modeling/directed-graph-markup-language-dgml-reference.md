---
title: Directed Graph Markup Language (DGML) reference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: cc3e4ae7-60fa-4e22-9227-98020b480b73
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16a51c7fc05d51b551884f70dc514e8939962818
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296029"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Referenz zur Directed Graph Markup Language (DGML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Directed Graph Markup Language (DGML) beschreibt die für die Visualisierung und die Komplexitätsanalyse verwendeten Informationen und stellt das zum Beibehalten von Code Maps verwendete Format in Visual Studio dar. DGML beschreibt zyklische und azyklische gerichtete Diagramme mithilfe von einfachem XML. Ein gerichtetes Diagramm ist ein Satz von Knoten, die durch Links bzw. Ränder verbunden sind. Mithilfe von Knoten und Links können Netzwerkstrukturen dargestellt werden, z. B. Elemente in einem Softwareprojekt.

 Note that some versions of Visual Studio support only a subset of DGML capabilities, see [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Wenn Sie eine DGML-Datei bearbeiten, unterstützt Sie IntelliSense beim Auffinden der für die Elemente verfügbaren Attribute und der zugehörigen Werte. Wenn Sie Farben in Attributen angeben möchten, verwenden Sie Namen für allgemeine Farben (z. B. "Blau") oder ARGB-Hexadezimalwerte (z. B. "#ffa0b1c3"). DGML verwendet eine kleine Teilmenge der WPF (Windows Presentation Foundation)-Farbdefinitionsformate. For more information, see [Colors Class](https://go.microsoft.com/fwlink/?LinkId=182345).

## <a name="DGML"></a> DGML syntax
 In der folgenden Tabelle werden verschiedene in DGML verwendete Elementtypen beschrieben:

- `<DirectedGraph></DirectedGraph>`

   Dieses Element ist das Stammelement des Code Map-Dokuments (.dgml). Alle anderen DGML-Elemente werden innerhalb des Bereichs dieses Elements angezeigt.

   In der folgenden Liste werden optionale Attribute beschrieben, die eingeschlossen werden können:

   `Background` – Die Farbe des Code Map-Hintergrunds.

   `BackgroundImage` – Der Speicherort der Bilddatei, die als Code Map-Hintergrund verwendet werden soll.

   `GraphDirection` – Wenn Code Map auf das Strukturlayout festgelegt wird (`Sugiyama`), ordnen Sie die Knoten so an, dass die meisten der Links in die angegebene Richtung fließen: `TopToBottom`, `BottomToTop`, `LeftToRight` oder `RightToLeft`. See [Change the map layout](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` – Legen Sie Code Map auf die folgenden Layouts fest: `None`, `Sugiyama` (Strukturlayout), `ForceDirected` (schnelle Cluster) oder `DependencyMatrix`. See [Change the map layout](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` – Wenn Code Map auf das Strukturlayout oder das schnelle Clusterlayout festgelegt ist, werden nur die Knoten angezeigt, die eine bestimmte Anzahl (1-7) von Links von den ausgewählten Knoten entfernt liegen. See [Change the map layout](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Dieses optionale Element enthält eine Liste von `<Node/>`-Elementen, die Knoten in Code Map definieren. Weitere Informationen finden Sie unter dem `<Node/>`-Element.

  > [!NOTE]
  > Wenn Sie auf einen nicht definierten Knoten in einem `<Link/>`-Element verweisen, wird in Code Map automatisch ein `<Node/>`-Element erstellt.

   Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Dieses Element definiert einen einzelnen Knoten. Es wird in der Liste der `<Nodes><Nodes/>`-Elemente angezeigt.

   Dieses Element muss die folgenden Attribute enthalten:

   `Id` – Der eindeutige Name des Knotens und der Standardwert des `Label`-Attributs, wenn kein separates `Label`-Attribut angegeben ist. Dieser Name muss mit dem `Source`-Attribut oder `Target`-Attribut des Links übereinstimmen, der darauf verweist.

   In der folgenden Liste werden einige optionale Attribute beschrieben, die eingeschlossen werden können:

   `Label` - The display name of the node.

   Formatattribute. Siehe [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` – Der Name einer Kategorie, die Elemente angibt, die dieses Attribut gemeinsam verwenden. Weitere Informationen finden Sie unter dem `<Category/>`-Element.

   `Property` – Der Name einer Eigenschaft, die Elemente angibt, die denselben Eigenschaftswert aufweisen. Weitere Informationen finden Sie unter dem `<Property/>`-Element.

   `Group` – Wenn der Knoten andere Knoten enthält, legen Sie dieses Attribut auf `Expanded` oder `Collapsed` fest, um seinen Inhalt anzuzeigen oder auszublenden. Es muss ein `<Link/>`-Element vorhanden sein, das das `Category="Contains"`-Attribut einschließt und den übergeordneten Knoten als Quellknoten und den untergeordneten Knoten als Zielknoten angibt. See [Group code elements](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` – Legen Sie dieses Attribut auf `Visible`, `Hidden` oder `Collapsed` fest. Verwendet `System.Windows.Visibility`. See [Hide or show nodes and links](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` – Legen Sie dieses Attribut fest, um es mit einem Dokument oder einer URL zu verknüpfen. See [Link documents or URLs to code elements and links](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Dieses Element enthält die Liste von `<Link>`-Elementen, die Links zwischen Knoten definieren. Weitere Informationen finden Sie unter dem `<Link/>`-Element.

   Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Dieses Element definiert einen einzelnen Link, der einen Quellknoten mit einem Zielknoten verbindet. Es wird in der Liste der `<Links></Links>`-Elemente angezeigt.

  > [!NOTE]
  > Wenn dieses Element auf einen nicht definierten Knoten verweist, wird vom Code Map-Dokument automatisch ein Knoten erstellt, der über die angegebenen Attribute (sofern vorhanden) verfügt.

   Dieses Element muss die folgenden Attribute enthalten:

   `Source` – Der Quellknoten des Links.

   `Target` – Der Zielknoten des Links.

   In der folgenden Liste werden einige optionale Attribute beschrieben, die eingeschlossen werden können:

   `Label` – Der Anzeigename des Links.

   Formatattribute. Siehe [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` – Der Name einer Kategorie, die Elemente angibt, die dieses Attribut gemeinsam verwenden. Weitere Informationen finden Sie unter dem `<Category/>`-Element.

   `Property` – Der Name einer Eigenschaft, die Elemente angibt, die denselben Eigenschaftswert aufweisen. Weitere Informationen finden Sie unter dem `<Property/>`-Element.

   Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   In diesem Element ist die Liste der `<Category/>`-Elemente enthalten. Weitere Informationen finden Sie unter dem `<Category/>`-Element.

   Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Dieses Element definiert ein `Category`-Attribut, mit dem Elemente angegeben werden, die dieses Attribut gemeinsam verwenden. Ein `Category`-Attribut kann verwendet werden, um Code Map-Elemente zu organisieren, um gemeinsame Attribute durch Vererbung bereitzustellen oder um weitere Metadaten zu definieren.

   Dieses Element muss die folgenden Attribute enthalten:

   `Id` – Der eindeutige Name der Kategorie und der Standardwert des `Label`-Attributs, wenn kein separates `Label`-Attribut angegeben ist.

   In der folgenden Liste werden einige optionale Attribute beschrieben, die eingeschlossen werden können:

   `Label` – Ein Anzeigename für die Kategorie.

   `BasedOn` – Die übergeordnete Kategorie, von der die `<Category/>` des aktuellen Elements erbt.

   Im Beispiel für dieses Element erbt die Kategorie `FailedTest` ihr `Stroke`-Attribut aus der Kategorie `PassedTest`. See "To create hierarchical categories" in [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Kategorien stellen auch ein bestimmtes grundlegendes Vorlagenverhalten bereit, mit dem die Darstellung von Knoten und Links bei der Anzeige in einer Code Map gesteuert wird. Siehe [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   In diesem Element ist die Liste der `<Property/>`-Elemente enthalten. Weitere Informationen finden Sie unter dem `<Property/>`-Element.

   Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Dieses Element definiert ein `Property`-Attribut, mit dem Sie einem DGML-Element oder -Attribut (einschließlich von Kategorien und anderen Eigenschaften) einen Wert zuweisen können.

   Dieses Element muss die folgenden Attribute enthalten:

  - `Id` – Der eindeutige Name der Eigenschaft und der Standardwert des `Label`-Attributs, wenn kein separates `Label`-Attribut angegeben ist.

  - `DataType` – Der Typ der Daten, die von der Eigenschaft gespeichert werden.

    If you want the property to appear in the **Properties** window, use the `Label` property to specify the property's display name.

    See [Assign categories to code elements and links](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    Beispiel:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="AddAlias"></a> Aliases for commonly-used paths
 Das Ersetzen häufig verwendeter Pfade durch Aliase trägt dazu bei, die Größe der DGML-Datei und die erforderliche Zeit zum Laden und Speichern der Datei zu reduzieren. Fügen Sie zum Erstellen eines Alias am Ende der DGML-Datei einen `<Paths></Paths>`-Abschnitt hinzu. Fügen Sie in diesem Abschnitt ein `<Path/>`-Element hinzu, um einen Alias für den Pfad zu definieren:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

 To reference the alias from an element in the .dgml file, enclose the `Id` of the \<Path/> element with a dollar sign ($) and parentheses (()):

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Siehe auch
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md) [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md)
