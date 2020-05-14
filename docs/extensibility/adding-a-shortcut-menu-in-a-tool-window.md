---
title: Ajout d’un menu raccourci dans une fenêtre d’outil (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740281"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Ajouter un menu raccourci dans une fenêtre d’outils
Cette procédure pas à pas met un menu raccourci dans une fenêtre d’outils. Un menu raccourci est un menu qui apparaît lorsqu’un utilisateur clique à droite sur un bouton, une boîte texte ou un arrière-plan de fenêtre. Les commandes d’un menu raccourci se comportent de la même façon que les commandes sur d’autres menus ou barres d’outils. Pour prendre en charge un menu raccourci, spécifiez-le dans le fichier *.vsct* et affichez-le en réponse au clic droit de la souris.

Une fenêtre d’outil se compose d’un contrôle d’utilisateur WPF dans une classe de fenêtre d’outil personnalisée qui hérite de <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.

Ce pas-fort montre comment créer un menu raccourci comme un menu Visual Studio, en déclarant des éléments de menu dans le fichier *.vsct,* puis en utilisant le cadre de paquet géré pour les implémenter dans la classe qui définit la fenêtre d’outils. Cette approche facilite l’accès aux commandes Visual Studio, aux éléments d’interface utilisateur et au modèle d’objet Automation.

Alternativement, si votre menu raccourci n’accédera pas aux <xref:System.Windows.FrameworkElement.ContextMenu%2A> fonctionnalités Visual Studio, vous pouvez utiliser la propriété d’un élément XAML dans le contrôle de l’utilisateur. Pour plus d’informations, voir [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Prérequis
A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Créez le forfait de menu raccourci de fenêtre d’outil

1. Créez un projet `TWShortcutMenu` VSIX nommé et ajoutez un modèle de fenêtre d’outil nommé **ShortcutMenu.** Pour plus d’informations sur la création d’une fenêtre d’outil, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Spécifier le menu raccourci
Un menu raccourci comme celui indiqué dans cette procédure pas à pas permet à l’utilisateur de choisir parmi une liste de couleurs qui sont utilisées pour remplir l’arrière-plan de la fenêtre d’outils.

1. Dans *ShortcutMenuPackage.vsct*, trouver dans l’élément GuidSymbol nommé guidShortcutMenuPackageCmdSet, et déclarer le menu raccourci, le groupe de menu raccourci, et les options de menu. L’élément GuidSymbol devrait maintenant ressembler à ceci :

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Juste avant l’élément Boutons, créez un élément Menus et définissez ensuite le menu raccourci en elle.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Un menu raccourci n’a pas de parent parce qu’il ne fait pas partie d’un menu ou d’une barre d’outils.

3. Créez un élément Groupes avec un élément groupe qui contient les éléments de menu raccourci et associez le groupe au menu raccourci.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Dans l’élément Boutons, définissez les commandes individuelles qui apparaîtront sur le menu des raccourcis. L’élément Boutons devrait ressembler à ceci :

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. Dans *ShortcutMenuCommand.cs*, ajoutez les définitions pour l’ensemble de commande GUID, le menu raccourci et les éléments du menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Ce sont les mêmes Œd de commande qui sont définis dans la section Symboles du fichier *ShortcutMenuPackage.vsct.* Le groupe de contexte n’est pas inclus ici parce qu’il n’est requis que dans le fichier *.vsct.*

## <a name="implementing-the-shortcut-menu"></a>Mise en œuvre du menu raccourci
 Cette section implémente le menu raccourci et ses commandes.

1. Dans *ShortcutMenu.cs,* la fenêtre d’outil peut obtenir le service de commande de menu, mais le contrôle qu’il contient ne peut pas. Les étapes suivantes montrent comment rendre le service de commande du menu accessible au contrôle de l’utilisateur.

2. Dans *ShortcutMenu.cs*, ajouter ce qui suit en utilisant des directives:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Remplacer la méthode Initialize() de la fenêtre d’outil pour obtenir le service de commande du menu et ajouter le contrôle, en passant le service de commande du menu au constructeur :

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. Dans le constructeur de fenêtre d’outils ShortcutMenu, retirez la ligne qui ajoute le contrôle. Le constructeur devrait maintenant ressembler à ceci:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. Dans *ShortcutMenuControl.xaml.cs,* ajoutez un champ privé pour le service de commande du menu et modifiez le constructeur de contrôle pour prendre le service de commande du menu. Ensuite, utilisez le service de commande du menu pour ajouter les commandes de menu contextuelle. Le constructeur ShortcutMenuControl devrait maintenant ressembler au code suivant. Le gestionnaire de commande sera défini plus tard.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. Dans *ShortcutMenuControl.xaml*, <xref:System.Windows.UIElement.MouseRightButtonDown> ajouter un <xref:System.Windows.Controls.UserControl> événement à l’élément de haut niveau. Le fichier XAML devrait maintenant ressembler à ceci:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. En *ShortcutMenuControl.xaml.cs,* ajoutez un talon pour le gestionnaire de l’événement.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Ajoutez les directives suivantes à l’aide d’un même fichier :

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Mettre `MyToolWindowMouseRightButtonDown` en œuvre l’événement comme suit.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Cela crée <xref:System.ComponentModel.Design.CommandID> un objet pour le menu raccourci, identifie l’emplacement du clic de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> souris, et ouvre le menu raccourci à cet endroit en utilisant la méthode.

10. Implémenter le gestionnaire de commande.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    Dans ce cas, une seule méthode gère les événements <xref:System.ComponentModel.Design.CommandID> pour tous les éléments du menu en identifiant et en définissant la couleur de fond en conséquence. Si les éléments du menu contenaient des commandes non liées, vous auriez créé un gestionnaire d’événement distinct pour chaque commande.

## <a name="test-the-tool-window-features"></a>Testez les fonctionnalités de la fenêtre de l’outil

1. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

2. Dans le cas expérimental, cliquez sur **View / Other Windows**, puis cliquez sur **ShortcutMenu**. Cela devrait afficher votre fenêtre d’outil.

3. Clic droit dans le corps de la fenêtre de l’outil. Un menu raccourci qui a une liste de couleurs doit être affiché.

4. Cliquez sur une couleur sur le menu raccourci. La couleur de fond de fenêtre d’outil doit être changée pour la couleur choisie.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
- [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)
