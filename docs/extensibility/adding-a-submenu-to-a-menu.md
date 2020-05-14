---
title: Ajout d’un Submenu à un menu . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740273"
---
# <a name="add-a-submenu-to-a-menu"></a>Ajouter un Submenu à un menu
Ce pas-là s’appuie sur la démonstration dans [Ajouter un menu à la barre de menu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) en montrant comment ajouter un sous-mois au menu **TestMenu.**

 Un sous-mois est un menu secondaire qui apparaît dans un autre menu. Un sous-mois peut être identifié par la flèche qui suit son nom. En cliquant sur le nom provoque l’affichage du sous-marin et de ses commandes.

 Ce pas-là crée un sous-mois dans un menu sur le menu Visual Studio bar et met une nouvelle commande sur le sous-présage. La procédure pas à pas met également en œuvre la nouvelle commande.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Ajouter un Submenu à un menu

1. Suivez les étapes de [l’ajout d’un menu à la barre de menu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) pour créer le projet et l’élément de menu. Les étapes de cette procédure pas à pas supposent `TopLevelMenu`que le nom du projet VSIX est .

2. Open *TestCommandPackage.vsct*. Dans `<Symbols>` la section, `<IDSymbol>` ajouter un élément pour le sous-mois, un pour le groupe `<GuidSymbol>` submenu, et un pour le commandement, le tout dans le nœud nommé "guidTopLevelMenuCmdSet." C’est le même nœud qui contient l’élément `<IDSymbol>` pour le menu de haut niveau.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Ajouter le sous-mois nouvellement créé à la `<Menus>` section.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     La paire GUID/ID du parent spécifie le groupe de menu qui a été généré dans [Ajouter un menu au Visual Studio Menu Bar](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), et est un enfant du menu haut de gamme.

4. Ajouter le groupe de menu défini `<Groups>` à l’étape 2 à la section et en faire un enfant du sous-mois.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Ajoutez un `<Button>` nouvel `<Buttons>` élément à la section pour définir la commande créée dans l’étape 2 comme élément sur le sous-mois.

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

6. Générez la solution et commencez le débogage. Vous devriez voir l’instance expérimentale.

7. Cliquez sur **TestMenu** pour voir un nouveau sous-mois nommé **Sous Menu**. Cliquez sur **Sous Menu** pour ouvrir le sous-mois et voir une nouvelle commande, Test **Sub Command**. Notez que cliquer sur **Test Sub Command** ne fait rien.

## <a name="add-a-command"></a>Ajouter une commande

1. Ouvrez *TestCommand.cs* et ajoutez l’ID de commande suivant après l’ID de commande existant.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Ajouter le sous-commande. Trouvez le constructeur de commande. Ajoutez les lignes suivantes juste `AddCommand` après l’appel à la méthode.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Le `SubItemCallback` gestionnaire de commande sera défini plus tard. Le constructeur devrait maintenant ressembler à ceci:

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

3. Ajoutez `SubItemCallback()`. C’est la méthode qui s’appelle lorsque le nouveau commandement dans le sous-groupe est cliqué.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
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

4. Générez le projet et commencez le débogage. L’instance expérimentale devrait apparaître.

5. Sur le menu **TestMenu,** cliquez sur **Sous Menu,** puis cliquez sur **Test Sub Command**. Une boîte de message doit apparaître et afficher le texte, "Test Command Inside TestCommand.SubItemCallback()".

## <a name="see-also"></a>Voir aussi

- [Ajoutez un menu au menu Visual Studio bar](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
