---
title: Ajout d’un Menu contextuel dans une fenêtre outil | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4b36800ea291c6f1bc0948a46b67c4e3549f349
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31568667"
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Ajout d’un Menu contextuel dans une fenêtre outil
Cette procédure pas à pas place un menu contextuel dans une fenêtre outil. Un menu contextuel est un menu qui s’affiche lorsqu’un utilisateur clique sur un bouton, une zone de texte ou un arrière-plan de la fenêtre. Commandes du menu contextuel comportent comme des commandes dans les autres menus ou les barres d’outils. Pour prendre en charge un menu contextuel, spécifiez-le dans le fichier .vsct et l’afficher en réponse à un clic droit de la souris.  
  
 Une fenêtre outil est constitué d’un contrôle utilisateur WPF dans une classe de fenêtre outil personnalisé qui hérite de <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 Cette procédure pas à pas montre comment créer un menu contextuel sous forme de menu Visual Studio, en déclarant les éléments de menu dans le fichier .vsct, puis en utilisant Managed Package Framework leur implémentation dans la classe qui définit la fenêtre outil. Cette approche facilite l’accès aux commandes de Visual Studio, les éléments d’interface utilisateur et le modèle objet Automation.  
  
 Si le menu contextuel n’accède pas aux fonctionnalités de Visual Studio, vous pouvez également utiliser le <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriété d’un élément XAML dans le contrôle utilisateur. Pour plus d’informations, consultez [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Création du Package de Menu de raccourci de fenêtre outil  
  
1.  Créez un projet VSIX nommé `TWShortcutMenu` et ajoutez un modèle de fenêtre outil nommé **menu de raccourcis** à celui-ci. Pour plus d’informations sur la création d’une fenêtre outil, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Spécifier le Menu contextuel  
 Un menu contextuel comme celui illustré dans cette procédure pas à pas permet à l’utilisateur sélectionner dans une liste de couleurs qui sont utilisées pour remplir l’arrière-plan de la fenêtre outil.  
  
1.  Dans ShortcutMenuPackage.vsct, recherchez dans l’élément GuidSymbol nommé guidShortcutMenuPackageCmdSet et déclarez le menu contextuel, groupe de menu contextuel et les options de menu. L’élément GuidSymbol doit maintenant ressembler à ceci :  
  
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
  
2.  Juste avant l’élément de boutons, créez un élément de Menus, puis définissez le menu contextuel dans celui-ci.  
  
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
  
     Un menu contextuel n’a pas de parent, car il n’est pas partie d’un menu ou une barre d’outils.  
  
3.  Créez un élément de groupes avec un élément de groupe qui contient les éléments de menu contextuel et associez le groupe avec le menu contextuel.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  Dans l’élément de boutons, définir des commandes individuelles qui apparaîtront dans le menu contextuel. L’élément de boutons doit ressembler à ceci :  
  
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
  
5.  Dans ShortcutMenuCommand.cs, ajoutez que les définitions de la commande définir le GUID, le menu contextuel et les éléments de menu.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Il s’agit du même ID de commande qui sont définis dans la section de symboles du fichier ShortcutMenuPackage.vsct. Le groupe de contexte n’est pas inclus ici, car elle est requise uniquement dans le fichier .vsct.  
  
## <a name="implementing-the-shortcut-menu"></a>Le Menu contextuel de mise en œuvre  
 Cette section implémente le menu contextuel et ses commandes.  
  
1.  Dans ShortcutMenu.cs, la fenêtre outil peut obtenir le service de commande de menu, mais le contrôle qu’il contient ne peut pas. Les étapes suivantes montrent comment rendre le service de commande de menu disponibles pour le contrôle utilisateur.  
  
2.  Dans ShortcutMenu.cs, ajoutez le code suivant à l’aide des instructions :  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Substituez la méthode Initialize() la fenêtre outil pour obtenir le service de commande de menu et ajouter le contrôle, en passant au service de commande de menu pour le constructeur :  
  
    ```csharp  
    protected override void Initialize()  
    {  
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  Dans le constructeur de fenêtre outil du menu de raccourcis, supprimez la ligne qui ajoute le contrôle. Le constructeur doit maintenant ressembler à ceci :  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  Dans ShortcutMenuControl.xaml.cs, ajoutez un champ privé pour le service de commande de menu et modifiez le constructeur du contrôle pour prendre le service de commande de menu. Puis utilisez le service de commande de menu pour ajouter les commandes de menu contextuel. Le constructeur ShortcutMenuControl doit maintenant ressembler au code suivant. Le Gestionnaire de commandes est défini ultérieurement.  
  
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
  
6.  Dans ShortcutMenuControl.xaml, ajoutez un <xref:System.Windows.UIElement.MouseRightButtonDown> événements au niveau supérieur du <xref:System.Windows.Controls.UserControl> élément. Le fichier XAML doit maintenant ressembler à ceci :  
  
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
  
7.  Dans ShortcutMenuControl.xaml.cs, ajoutez un stub pour le Gestionnaire d’événements.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Ajoutez le code suivant à l’aide des instructions dans le même fichier :  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implémentez la `MyToolWindowMouseRightButtonDown` événement comme suit.  
  
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
  
     Cette opération crée un <xref:System.ComponentModel.Design.CommandID> objet pour le menu contextuel, identifie l’emplacement de la souris et ouvre le menu contextuel dans cet emplacement à l’aide de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> (méthode).  
  
10. Implémenter le Gestionnaire de commandes.  
  
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
  
     Dans ce cas, une méthode gère les événements pour tous les éléments de menu en identifiant les <xref:System.ComponentModel.Design.CommandID> et définir la couleur d’arrière-plan en conséquence. Si les éléments de menu contenait des commandes sans rapport, vous devriez avoir créé un gestionnaire d’événements distinct pour chaque commande.  
  
## <a name="testing-the-tool-window-features"></a>Tester les fonctions de fenêtre outil  
  
1.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
2.  Dans l’instance expérimentale, cliquez sur **affichage / autres fenêtres**, puis cliquez sur **menu de raccourcis**. Cette opération doit s’afficher la fenêtre outil.  
  
3.  Avec le bouton droit dans le corps de la fenêtre outil. Un menu contextuel qui contient une liste de couleurs doit être affiché.  
  
4.  Cliquez sur une couleur dans le menu contextuel. La couleur d’arrière-plan de fenêtre outil doit être modifiée pour la couleur sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)