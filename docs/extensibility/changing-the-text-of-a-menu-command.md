---
title: Ändern des Texts eines Menübefehls | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ba19a6536be7f0f5855ee9035e80989c105cbf7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321111"
---
# <a name="change-the-text-of-a-menu-command"></a>Ändern Sie den Text eines Menübefehls
Die folgenden Schritte zeigen, wie Sie mithilfe der Beschriftung eines Menübefehls Ändern der <xref:System.ComponentModel.Design.IMenuCommandService> Service.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Ändern im Menü Befehl Bezeichnung mit dem IMenuCommandService

1. Erstellen Sie ein VSIX-Projekt mit dem Namen `MenuText` mit einem Menübefehl mit dem Namen **ChangeMenuText**. Weitere Informationen finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. In der *VSCT* hinzufügen. die `TextChanges` flag auf den Menübefehl, wie im folgenden Beispiel gezeigt.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. In der *ChangeMenuText.cs* Datei, erstellen Sie einen Ereignishandler, die aufgerufen wird, bevor der Menübefehl im angezeigt wird.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    Sie können auch den Status des Menübefehls in dieser Methode aktualisieren, indem Sie ändern die <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, und <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> Eigenschaften für die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Objekt.

4. Ersetzen Sie den ursprünglichen Befehl Initialisierungs- und Platzierung der Code im Konstruktor ChangeMenuText mit Code, der erstellt eine <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (anstelle eines `MenuCommand`), die den Menübefehl darstellt, fügt die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Ereignishandler, und klicken Sie im Menü Befehl, der dem Menübefehlsdienst.

    So sieht es folgendermaßen aussehen sollte:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

6. Auf der **Tools** Menü sollte einen Befehl mit dem Namen **aufrufen ChangeMenuText**.

7. Klicken Sie auf den Befehl. Daraufhin sollte das Meldungsfeld, die Ankündigung **MenuItemCallback** aufgerufen wurde. Wenn Sie das Meldungsfeld geschlossen haben, sollte angezeigt, dass der Name des Befehls im Menü Extras jetzt **neuen Text**.
