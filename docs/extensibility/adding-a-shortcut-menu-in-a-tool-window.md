---
title: Ajout d’un menu contextuel dans une fenêtre outil | Microsoft Docs
description: Découvrez comment ajouter un menu contextuel à une fenêtre outil dans Visual Studio qui apparaît lorsqu’un utilisateur clique avec le bouton droit sur un bouton, une zone de texte ou un arrière-plan de fenêtre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3ba0eb2324812ca7536b361d602bb683d627c743
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097615"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Ajouter un menu contextuel dans une fenêtre outil
Cette procédure pas à pas permet de placer un menu contextuel dans une fenêtre outil. Un menu contextuel est un menu qui s’affiche lorsqu’un utilisateur clique avec le bouton droit sur un bouton, une zone de texte ou un arrière-plan de fenêtre. Les commandes d’un menu contextuel se comportent comme des commandes sur d’autres menus ou barres d’outils. Pour prendre en charge un menu contextuel, spécifiez-le dans le fichier *. vsct* et affichez-le en réponse à un clic droit de la souris.

Une fenêtre outil se compose d’un contrôle utilisateur WPF dans une classe de fenêtre outil personnalisée qui hérite de <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

Cette procédure pas à pas montre comment créer un menu contextuel en tant que menu Visual Studio, en déclarant les éléments de menu dans le fichier *. vsct* , puis en utilisant l’infrastructure de package managée pour les implémenter dans la classe qui définit la fenêtre outil. Cette approche facilite l’accès aux commandes Visual Studio, aux éléments d’interface utilisateur et au modèle objet Automation.

Sinon, si votre menu contextuel n’accède pas aux fonctionnalités de Visual Studio, vous pouvez utiliser la <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriété d’un élément XAML dans le contrôle utilisateur. Pour plus d’informations, consultez [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Prérequis
À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Créer le package du menu contextuel de la fenêtre outil

1. Créez un projet VSIX nommé `TWShortcutMenu` et ajoutez-lui un modèle de fenêtre outil nommé **MenuContextuel** . Pour plus d’informations sur la création d’une fenêtre outil, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Spécification du menu contextuel
Un menu contextuel, tel que celui illustré dans cette procédure pas à pas, permet à l’utilisateur d’effectuer une sélection dans une liste de couleurs qui sont utilisées pour remplir l’arrière-plan de la fenêtre outil.

1. Dans *ShortcutMenuPackage. vsct*, recherchez dans l’élément GuidSymbol nommé guidShortcutMenuPackageCmdSet, puis déclarez le menu contextuel, le groupe de menus contextuels et les options de menu. L’élément GuidSymbol doit maintenant ressembler à ceci :

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

2. Juste avant l’élément Buttons, créez un élément menus, puis définissez le menu contextuel dans celui-ci.

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

    Un menu contextuel n’a pas de parent, car il ne fait pas partie d’un menu ou d’une barre d’outils.

3. Créez un élément Groups avec un élément Group qui contient les éléments de menu contextuel et associez le groupe au menu contextuel.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Dans l’élément Buttons, définissez les commandes individuelles qui s’affichent dans le menu contextuel. L’élément Buttons doit ressembler à ceci :

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

5. Dans *ShortcutMenuCommand. cs*, ajoutez les définitions pour le GUID du jeu de commandes, le menu contextuel et les éléments de menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Il s’agit des mêmes ID de commande que ceux définis dans la section Symbols du fichier *ShortcutMenuPackage. vsct* . Le groupe de contexte n’est pas inclus ici, car il n’est requis que dans le fichier *. vsct* .

## <a name="implementing-the-shortcut-menu"></a>Implémentation du menu contextuel
 Cette section implémente le menu contextuel et ses commandes.

1. Dans *MenuContextuel. cs*, la fenêtre outil peut accéder au service de commande de menu, mais le contrôle qu’il contient ne le peut pas. Les étapes suivantes montrent comment rendre le service de commande de menu accessible au contrôle utilisateur.

2. Dans *MenuContextuel. cs*, ajoutez les directives d’utilisation suivantes :

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Substituez la méthode Initialize () de la fenêtre outil pour récupérer le service de commande de menu et ajouter le contrôle en passant le service de commande de menu au constructeur :

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. Dans le constructeur de fenêtre de l’outil MenuContextuel, supprimez la ligne qui ajoute le contrôle. Le constructeur doit maintenant ressembler à ceci :

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. Dans *ShortcutMenuControl. Xaml. cs*, ajoutez un champ privé pour le service de commande de menu et modifiez le constructeur de contrôle pour qu’il prenne le service de commande de menu. Utilisez ensuite le service de commande de menu pour ajouter les commandes de menu contextuel. Le constructeur ShortcutMenuControl doit maintenant ressembler au code suivant. Le gestionnaire de commandes sera défini ultérieurement.

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

6. Dans *ShortcutMenuControl. Xaml*, ajoutez un <xref:System.Windows.UIElement.MouseRightButtonDown> événement à l’élément de niveau supérieur <xref:System.Windows.Controls.UserControl> . Le fichier XAML doit maintenant ressembler à ceci :

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

7. Dans *ShortcutMenuControl. Xaml. cs*, ajoutez un stub pour le gestionnaire d’événements.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Ajoutez les directives using suivantes au même fichier :

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implémentez l' `MyToolWindowMouseRightButtonDown` événement comme suit.

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

    Cela crée un <xref:System.ComponentModel.Design.CommandID> objet pour le menu contextuel, identifie l’emplacement du clic de souris et ouvre le menu contextuel à cet emplacement à l’aide de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> méthode.

10. Implémentez le gestionnaire de commandes.

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

    Dans ce cas, une seule méthode gère les événements de tous les éléments de menu en identifiant <xref:System.ComponentModel.Design.CommandID> et en définissant la couleur d’arrière-plan en conséquence. Si les éléments de menu contenaient des commandes non liées, vous auriez créé un gestionnaire d’événements distinct pour chaque commande.

## <a name="test-the-tool-window-features"></a>Tester les fonctionnalités de la fenêtre outil

1. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

2. Dans l’instance expérimentale, cliquez sur **affichage/autres fenêtres**, puis sur **MenuContextuel**. Cela permet d’afficher la fenêtre outil.

3. Cliquez avec le bouton droit dans le corps de la fenêtre outil. Un menu contextuel contenant une liste de couleurs doit s’afficher.

4. Cliquez sur une couleur dans le menu contextuel. La couleur d’arrière-plan de la fenêtre outil doit être remplacée par la couleur sélectionnée.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
- [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)
