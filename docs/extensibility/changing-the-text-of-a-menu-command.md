---
title: Modification du texte d’une commande de menu | Microsoft Docs
description: Découvrez comment modifier l’étiquette de texte d’une commande de menu à l’aide du service IMenuCommandService en examinant cet exemple de code.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 541acf1bcf448541fe6c440eb2aada687cfbe0e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904989"
---
# <a name="change-the-text-of-a-menu-command"></a>Modifier le texte d’une commande de menu
Les étapes suivantes montrent comment modifier l’étiquette de texte d’une commande de menu à l’aide du <xref:System.ComponentModel.Design.IMenuCommandService> service.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Modification d’une étiquette de commande de menu avec IMenuCommandService

1. Créez un projet VSIX nommé `MenuText` à l’aide d’une commande de menu nommée **ChangeMenuText**. Pour plus d’informations, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Dans le fichier *. vsct* , ajoutez l' `TextChanges` indicateur à votre commande de menu, comme indiqué dans l’exemple suivant.

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

3. Dans le fichier *ChangeMenuText. cs* , créez un gestionnaire d’événements qui sera appelé avant l’affichage de la commande de menu.

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

    Vous pouvez également mettre à jour l’état de la commande de menu dans cette méthode en modifiant les <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> Propriétés, et <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> sur l' <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objet.

4. Dans le constructeur ChangeMenuText, remplacez l’initialisation de la commande d’origine et le code de placement par du code qui crée un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (au lieu d’un `MenuCommand` ) qui représente la commande de menu, ajoute le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire d’événements et donne la commande de menu au service de commande de menu.

    Voici à quoi elle doit ressembler :

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.

6. Dans le menu **Outils** , vous devez voir une commande appelée **appeler ChangeMenuText**.

7. Cliquez sur la commande. La boîte de message s’affiche pour annoncer que **MenuItemCallback** a été appelé. Lorsque vous fermez la boîte de message, vous devez voir que le nom de la commande dans le menu outils est désormais **nouveau texte**.
