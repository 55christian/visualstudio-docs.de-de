---
title: Menu-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79a8fafc748274015dac7f8f0938bba37ba5a8bc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959260"
---
# <a name="menu-element"></a>Menu-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiert ein Menüelement. Dies sind die sechs Arten von Menüs: Kontext, Menüs, MenuController, MenuControllerLatched, Symbolleisten und ToolWindowToolbar.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. GUID der Befehls-ID der GUID-ID.|  
|id|Erforderlich. ID des Befehls-ID der GUID-ID.|  
|priority|Dies ist optional. Ein numerischer Wert, der angibt, die relative Position eines Menüs in einer Gruppe von Menüs.|  
|ToolbarPriorityInBand|Dies ist optional. Ein numerischer Wert, der die relative Position einer Symbolleiste in einem Band angibt, wenn das Fenster angedockt wird.|  
|Typ|Dies ist optional. Ein Enumerationswert, der die Art des Elements angibt.<br /><br /> Wenn Sie nicht vorhanden ist, ist der Standardtyp Menü aus.<br /><br /> Kontext<br /> Ein Kontextmenü, das angezeigt wird, wenn ein Benutzer ein Fenster mit der rechten Maustaste. Ein Kontextmenü weist folgende Merkmale auf:<br /><br /> -Die übergeordnete und die Priorität-Felder wird nicht verwendet werden, wenn das Menü wird als ein Kontextmenü angezeigt werden soll.<br />– Sie können als Untermenü sowie als Kontextmenü verwendet werden. In diesem Fall werden sowohl Gruppen-ID und Prioritätsfeldern eingehalten.<br />– Dies ist nicht immer zur Verfügung.<br /><br /> Ein Kontextmenü wird nur angezeigt, wenn die folgenden Bedingungen erfüllt sind:<br /><br /> -Das Fenster, das als Host dienende wird angezeigt.<br />– Ein Mauszeiger-Handler im VSPackage erkennt eine mit der rechten Maustaste auf das Fenster und ruft dann eine Methode, die den Befehl behandelt.<br />-Das Kontextmenü wird angezeigt, durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> Methode (empfohlen) oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> Methode.<br /><br /> Menü<br /> Stellt ein Dropdown-Menü. Ein Dropdown-Menü weist folgende Merkmale auf:<br /><br /> -Das übergeordnete Element in der zugehörigen Definition respektiert.<br />-Muss es sich um eine übergeordnete Gruppe oder einem CommandPlacement zu einer Gruppe aufweisen.<br />– Ein Untermenü in eine andere Art von Menü Sie können sein.<br />– Wird automatisch angezeigt, bei jedem übergeordneten Menü angezeigt wird.<br />– Die Implementierung des VSPackage von Code erleichtern angezeigt ist nicht erforderlich werden.<br /><br /> MenuController<br /> Stellt eine unterteilte Schaltfläche des Dropdown-Menü, der in Symbolleisten in der Regel verwendet wird. Ein Menü MenuController weist folgende Merkmale auf:<br /><br /> -Muss in einem anderen Menü über übergeordnete oder CommandPlacement enthalten sein.<br />-Das übergeordnete Element in der zugehörigen Definition respektiert.<br />– Sie können jede Art von Menü als übergeordnetes Element haben.<br />– Wird automatisch zur Verfügung gestellt bei jedem übergeordneten Menü angezeigt wird.<br />– Programmgesteuerte Unterstützung im angezeigten Menü vornehmen ist nicht erforderlich werden.<br /><br /> Ein Befehl im Menü der unterteilten Schaltfläche wird auf die Menüschaltfläche angezeigt. Der Befehl angezeigt hat einen der folgenden Merkmale:<br /><br /> – Es ist mit dem letzten Befehl, der verwendet wurde, wenn der Befehl weiterhin angezeigt, und aktiviert ist.<br />– Es ist mit dem ersten angezeigten-Befehl.<br /><br /> MenuControllerLatched<br /> Stellt eine unterteilte Schaltfläche des Dropdown-Menü, das für die ein Befehl als Standardauswahl angegeben werden kann durch markieren den Befehl aus, wie ein Latchtyp zugeordnet.<br /><br /> Ein eingerastet Befehl ist ein Befehl, der im Menü als ausgewählt, in der Regel markiert ist, indem ein Häkchen angezeigt. Ein Befehl kann gekennzeichnet werden, wie ein Latchtyp zugeordnet, wenn sie die OLECMDF_LATCHED verfügt flagssatz darauf in einer Implementierung von der `QueryStatus` -Methode der der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Ein Menü MenuControllerLatched weist folgende Merkmale auf:<br /><br /> -Muss in einem anderen Menü über eine übergeordnete Gruppe oder ein CommandPlacement enthalten sein.<br />-Das übergeordnete Element in der zugehörigen Definition respektiert.<br />– Sie können jede Art von Menü als übergeordnetes Element haben.<br />– Dies ist zur Verfügung gestellt, wenn die übergeordneten Menü angezeigt wird.<br />– Programmgesteuerte Unterstützung im angezeigten Menü vornehmen ist nicht erforderlich werden.<br /><br /> Ein Befehl im Menü der unterteilten Schaltfläche wird auf die Menüschaltfläche angezeigt. Der Befehl angezeigt hat einen der folgenden Merkmale:<br /><br /> – Es ist mit dem ersten angezeigten Befehl, der ein Latchtyp zugeordnet ist.<br />– Es ist mit dem ersten angezeigten-Befehl.<br /><br /> Symbolleiste<br /> Enthält eine Symbolleiste an. Eine Symbolleiste weist folgende Merkmale auf:<br /><br /> -Das übergeordnete Element in der zugehörigen Definition ignoriert.<br />-Kann kein Untermenü der Gruppe "alle", auch nicht mithilfe von CommandPlacement vorgenommen werden.<br />– Sie können immer angezeigt werden, indem Sie auf **Symbolleisten** auf die **Ansicht** Menü.<br />– Sie können angezeigt werden, indem eine [VisibilityItem](../extensibility/visibilityitem-element.md).<br />-Code zu erstellen erfordert keine. Ein Beispiel dazu, wie Sie eine Symbolleiste erstellen, finden Sie unter [Hinzufügen einer Symbolleiste](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Enthält eine Symbolleiste, die mit einem bestimmten Toolfenster, verbunden ist, wie eine Symbolleiste mit der Entwicklungsumgebung verbunden ist.<br /><br /> -Das übergeordnete Element in der zugehörigen Definition ignoriert.<br />-Kann kein Untermenü der Gruppe "alle", auch nicht mithilfe von CommandPlacement vorgenommen werden.<br />– Wird nur angezeigt, wenn das Toolfenster, das die Symbolleiste hostet angezeigt wird, und das VSPackage wird explizit die Symbolleiste, um das Fenster hinzugefügt. Dies erfolgt normalerweise, wenn das Toolfenster erstellt wird, durch die Toolbar-Host-Eigenschaft abrufen (dargestellt durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> Schnittstelle) aus der Toolfensterrahmen aufrufen und anschließend die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> Methode.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element|Dies ist optional. Das übergeordnete Element des Menüelements.|  
|CommandFlag|Erforderlich. Finden Sie unter [Befehl Commandflag-Element](../extensibility/command-flag-element.md). Gültige Werte für ein Menü CommandFlag sind wie folgt aus:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -dieses Flag hat keine Auswirkungen auf die Anzeige von Symbolleisten.<br />-   **DontCache**<br />-   **DynamicVisibility** -dieses Flag hat keine Auswirkungen auf die Anzeige von Symbolleisten.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|Zeichenfolgen|Erforderlich. Finden Sie unter [Zeichenfolgen Element](../extensibility/strings-element.md). Das untergeordnete Element `ButtonText` Element definiert werden muss.|  
|Anmerkung|Optionaler Kommentar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Menus-Element](../extensibility/menus-element.md)|Definiert die Menüs aus, denen eine VSPackage implementiert.|  
  
## <a name="example"></a>Beispiel  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)