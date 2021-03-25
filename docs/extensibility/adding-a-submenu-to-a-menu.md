---
title: Ajout d’un sous-menu à un menu | Microsoft Docs
description: Apprenez à créer un sous-menu, à l’ajouter à la barre de menus de Visual Studio et à ajouter une nouvelle commande au sous-menu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc6d521e699beb2345ba76e2e617ff749886eee9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094898"
---
# <a name="add-a-submenu-to-a-menu"></a>Ajouter un sous-menu à un menu
Cette procédure pas à pas s’appuie sur la démonstration dans [Ajouter un menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) en montrant comment ajouter un sous-menu au menu **TestMenu** .

 Un sous-menu est un menu secondaire qui apparaît dans un autre menu. Un sous-menu peut être identifié par la flèche qui suit son nom. Le fait de cliquer sur le nom entraîne l’affichage du sous-menu et de ses commandes.

 Cette procédure pas à pas crée un sous-menu dans un menu de la barre de menus de Visual Studio et place une nouvelle commande dans le sous-menu. La procédure pas à pas implémente également la nouvelle commande.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Ajouter un sous-menu à un menu

1. Suivez les étapes de la section [Ajouter un menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) pour créer le projet et l’élément de menu. Les étapes de cette procédure pas à pas supposent que le nom du projet VSIX est `TopLevelMenu` .

2. Ouvrez *TestCommandPackage. vsct*. Dans la `<Symbols>` section, ajoutez un `<IDSymbol>` élément pour le sous-menu, un pour le groupe de sous-menu et un pour la commande, le tout dans le `<GuidSymbol>` nœud nommé « guidTopLevelMenuCmdSet ». Il s’agit du même nœud que celui qui contient l' `<IDSymbol>` élément pour le menu de niveau supérieur.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Ajoutez le sous-menu nouvellement créé à la `<Menus>` section.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     La paire GUID/ID du parent spécifie le groupe de menus qui a été généré dans [Ajouter un menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)et est un enfant du menu de niveau supérieur.

4. Ajoutez le groupe de menus défini à l’étape 2 à la `<Groups>` section et définissez-le comme un enfant du sous-menu.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Ajoutez un nouvel `<Button>` élément à la `<Buttons>` section pour définir la commande créée à l’étape 2 en tant qu’élément dans le sous-menu.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Générez la solution et commencez le débogage. Vous devez voir l’instance expérimentale.

7. Cliquez sur **TestMenu** pour afficher un nouveau sous-menu nommé **sous-** menu. Cliquez sur **sous-menu** pour ouvrir le sous-menu et afficher une nouvelle commande, **tester la sous-commande**. Notez que le fait de cliquer sur la **sous-commande test** n’a aucun effet.

## <a name="add-a-command"></a>Ajouter une commande

1. Ouvrez *test. cs* et ajoutez l’ID de commande suivant après l’ID de commande existant.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Ajoutez la sous-commande. Recherchez le constructeur de commande. Ajoutez les lignes suivantes juste après l’appel à la `AddCommand` méthode.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Le `SubItemCallback` Gestionnaire de commandes sera défini ultérieurement. Le constructeur doit maintenant ressembler à ceci :

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Ajoutez `SubItemCallback()`. Il s’agit de la méthode qui est appelée lorsque l’utilisateur clique sur la nouvelle commande dans le sous-menu.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        IVsUIShell uiShell = this.package.GetService<SVsUIShell, IVsUIShell>();
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.

5. Dans le menu **TestMenu** , cliquez sur **sous-menu** , puis sur **commande tester la sous-commande**. Une boîte de message doit apparaître et afficher le texte « commande test dans test. SubItemCallback () ».

## <a name="see-also"></a>Voir aussi

- [Ajouter un menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
