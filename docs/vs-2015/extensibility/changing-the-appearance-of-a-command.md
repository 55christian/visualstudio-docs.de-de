---
title: Ändern der Darstellung eines Befehls | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4741059410e052c571d77088b9cbe109fb651642
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095062"
---
# <a name="changing-the-appearance-of-a-command"></a>Ändern der Darstellung eines Befehls
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Feedback für den Benutzer angeben, durch Ändern der Darstellung eines Befehls. Beispielsweise sollten Sie einen Befehl anders aussehen, wenn sie nicht verfügbar ist. Sie können Befehle stellen, verfügbar oder nicht verfügbar, ausblenden oder anzeigen, oder aktivieren bzw. deaktivieren sie im Menü.  
  
 Um die Darstellung eines Befehls zu ändern, führen Sie eine der folgenden Aktionen:  
  
- Geben Sie den geeigneten Flags in der Befehlsdefinition in der Befehlsdatei für die Tabelle ein.  
  
- Verwenden der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Service.  
  
- Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle und die unformatierte Befehlsobjekte zu ändern.  
  
  Die folgenden Schritte zeigen, wie Sie suchen und aktualisieren Sie die Darstellung eines Befehls mit dem Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>So ändern Sie die Darstellung eines Menübefehls  
  
1. Befolgen Sie die Anweisungen in [Ändern des Texts eines Menübefehls](../extensibility/changing-the-text-of-a-menu-command.md) So erstellen Sie ein Menüelement namens `New Text`.  
  
2. Fügen Sie in der Datei ChangeMenuText.cs die folgenden using-Anweisung:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3. Fügen Sie in der Datei ChangeMenuTextPackageGuids.cs die folgende Zeile hinzu:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4. Ersetzen Sie den Code in der ShowMessageBox-Methode durch den folgenden, in der Datei ChangeMenuText.cs:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5. Abrufen den Befehl, der aktualisiert werden sollen die <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Objekt aus, und legen Sie dann die entsprechenden Eigenschaften für das Command-Objekt. Beispielsweise wird die folgende Methode der angegebenen Befehlssatz aus einem VSPackage-Befehl verfügbar oder nicht verfügbar. Im folgenden Code werden das Menü, das Element mit dem Namen `New Text` nicht verfügbar, nachdem sie bereits geklickt wurde.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio sollte angezeigt werden.  
  
7. Auf der **Tools** Menü klicken Sie auf die **aufrufen ChangeMenuText** Befehl. Zu diesem Zeitpunkt ist der Name des Befehls **aufrufen ChangeMenuText**, sodass die Befehlshandler ChangeMyCommand() nicht aufruft.  
  
8. Auf der **Tools** Menü jetzt angezeigt werden sollte **neuen Text**. Klicken Sie auf **neuen Text**. Der Befehl sollte jetzt abgeblendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Erweitern von Menüs und Befehle](../extensibility/extending-menus-and-commands.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
