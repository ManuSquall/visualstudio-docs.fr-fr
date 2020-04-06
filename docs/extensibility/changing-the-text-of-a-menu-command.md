---
title: Modification du texte d’une commande de menu ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739849"
---
# <a name="change-the-text-of-a-menu-command"></a>Modifier le texte d’une commande de menu
Les étapes suivantes montrent comment modifier l’étiquette de <xref:System.ComponentModel.Design.IMenuCommandService> texte d’une commande de menu en utilisant le service.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Modification d’une étiquette de commande de menu avec l’IMenuCommandService

1. Créez un projet `MenuText` VSIX nommé avec une commande de menu nommée **ChangeMenuText**. Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dans le fichier *.vsct,* ajoutez le `TextChanges` drapeau à votre commande de menu, comme indiqué dans l’exemple suivant.

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

3. Dans le *fichier ChangeMenuText.cs,* créez un gestionnaire d’événements qui sera appelé avant que la commande du menu ne soit affichée.

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

    Vous pouvez également mettre à jour l’état <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>de <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>la <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> commande <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> de menu dans cette méthode en changeant le , , et les propriétés sur l’objet.

4. Dans le constructeur ChangeMenuText, remplacez le code d’initialisation <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> et de `MenuCommand`placement de commande d’origine par un code qui crée un (plutôt qu’un ) qui représente la commande du menu, ajoute le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestionnaire d’événements et donne la commande de menu au service de commande du menu.

    Voici à quoi il devrait ressembler:

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

5. Générez le projet et commencez le débogage. L’exemple expérimental de Visual Studio apparaît.

6. Sur le menu **Tools,** vous devriez voir une commande nommée **Invoke ChangeMenuText**.

7. Cliquez sur la commande. Vous devriez voir la boîte de message annonçant que **MenuItemCallback** a été appelé. Lorsque vous rejetez la boîte de message, vous devez voir que le nom de la commande sur le menu Tools est maintenant **nouveau texte**.
