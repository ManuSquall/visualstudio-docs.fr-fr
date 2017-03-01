---
title: "Ajout d’un Menu contextuel dans une fenêtre outil | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ab921bec73528be7207baebdf9cb31885e2253fd
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Ajout d’un Menu contextuel dans une fenêtre outil
Cette procédure pas à pas place un menu contextuel dans une fenêtre outil. Un menu contextuel est un menu qui s’affiche lorsqu’un utilisateur clique sur un bouton, une zone de texte ou un arrière-plan de la fenêtre. Commandes du menu contextuel comportent comme des commandes d’autres menus ou les barres d’outils. Pour prendre en charge un menu contextuel, spécifiez-le dans le fichier .vsct et l’afficher en réponse à un clic droit de la souris.  
  
 Une fenêtre outil est constitué d’un contrôle utilisateur WPF dans une classe de fenêtre Outil personnalisée qui hérite de <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
 Cette procédure pas à pas montre comment créer un menu contextuel sous forme de menu Visual Studio, en déclarant les éléments de menu dans le fichier .vsct, puis en utilisant Managed Package Framework leur implémentation dans la classe qui définit la fenêtre outil. Cette approche facilite l’accès aux commandes de Visual Studio, des éléments de l’interface utilisateur et le modèle objet Automation.  
  
 Si le menu contextuel pas à accéder à des fonctionnalités de Visual Studio, vous pouvez également utiliser le <xref:System.Windows.FrameworkElement.ContextMenu%2A>propriété d’un élément XAML dans le contrôle utilisateur.</xref:System.Windows.FrameworkElement.ContextMenu%2A> Pour plus d’informations, consultez [ContextMenu](http://msdn.microsoft.com/Library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d).  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Création du Package de Menu de raccourci de fenêtre outil  
  
1.  Créez un projet VSIX nommé `TWShortcutMenu` et ajoutez un modèle de fenêtre outil nommé **menu de raccourcis** à celui-ci. Pour plus d’informations sur la création d’une fenêtre outil, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Spécifier le Menu contextuel  
 Un menu contextuel comme celle illustrée dans cette procédure pas à pas permet à l’utilisateur sélectionner dans une liste de couleurs qui sont utilisées pour remplir l’arrière-plan de la fenêtre outil.  
  
1.  Dans ShortcutMenuPackage.vsct, recherchez dans l’élément GuidSymbol nommé guidShortcutMenuPackageCmdSet et déclarez le menu contextuel, groupe de menus contextuels et options de menu. L’élément GuidSymbol doit maintenant ressembler à ceci :  
  
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
  
2.  Juste avant l’élément de boutons, créez un élément de Menus, puis définir le menu contextuel dans celui-ci.  
  
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
  
3.  Créer un élément Groups avec un élément de groupe qui contient les éléments de menu contextuel et associez le groupe avec le menu contextuel.  
  
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
  
5.  Dans ShortcutMenuPackageGuids.cs, ajoutez que les définitions de la commande définir le GUID, le menu contextuel et les éléments de menu.  
  
    ```c#  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Il s’agit du même ID de commande qui sont définis dans la section Symbols du fichier ShortcutMenuPackage.vsct. Le groupe de contexte n’est pas inclus ici car elle est requise uniquement dans le fichier .vsct.  
  
## <a name="implementing-the-shortcut-menu"></a>L’implémentation du Menu contextuel  
 Cette section implémente le menu contextuel et ses commandes.  
  
1.  Dans ShortcutMenu.cs, la fenêtre outil peut obtenir le service de commande de menu, mais le contrôle qu’il contient ne peuvent pas. Les étapes suivantes montrent comment rendre le service de commande de menu disponibles pour le contrôle utilisateur.  
  
2.  Dans ShortcutMenu.cs, ajoutez les instructions using :  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Remplacez la méthode Initialize() de la fenêtre outil pour obtenir le service de commande de menu et ajouter le contrôle, en passant le service de commande de menu pour le constructeur :  
  
    ```c#  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  Dans le constructeur de fenêtre outil du menu de raccourcis, supprimez la ligne qui ajoute le contrôle. Le constructeur doit maintenant ressembler à ceci :  
  
    ```c#  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  Dans ShortcutMenuControl.xaml.cs, ajoutez un champ privé pour le service de commande de menu et modifiez le constructeur du contrôle pour prendre le service de commande de menu. Puis utilisez le service de commande de menu pour ajouter les commandes de menu contextuel. Le constructeur ShortcutMenuControl doit maintenant ressembler à du code suivant. Le Gestionnaire de commande est défini ultérieurement.  
  
    ```c#  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  Dans ShortcutMenuControl.xaml, ajoutez un <xref:System.Windows.UIElement.MouseRightButtonDown>événements au niveau supérieur <xref:System.Windows.Controls.UserControl>élément.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.UIElement.MouseRightButtonDown> Le fichier XAML doit ressembler à ceci :  
  
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
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Ajoutez le code suivant à l’aide des instructions dans le même fichier :  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implémentez la `MyToolWindowMouseRightButtonDown` événement comme suit.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     Cela crée un <xref:System.ComponentModel.Design.CommandID>objet pour le menu contextuel, identifie l’emplacement de la souris et ouvre le menu contextuel dans cet emplacement à l’aide de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>méthode.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> </xref:System.ComponentModel.Design.CommandID>  
  
10. Implémenter le Gestionnaire de commandes.  
  
    ```c#  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     Dans ce cas, une méthode gère les événements de tous les éléments de menu en identifiant les <xref:System.ComponentModel.Design.CommandID>et définir la couleur d’arrière-plan en conséquence.</xref:System.ComponentModel.Design.CommandID> Si les éléments de menu contenait des commandes sans rapport, c’êtes que vous avez créé un gestionnaire d’événements distinct pour chaque commande.  
  
## <a name="testing-the-tool-window-features"></a>Tester les fonctions de fenêtre outil  
  
1.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
2.  Dans l’instance expérimentale, cliquez sur **affichage / autres fenêtres**, puis cliquez sur **menu de raccourcis**. Cette opération doit afficher la fenêtre outil.  
  
3.  Avec le bouton droit dans le corps de la fenêtre outil. Un menu contextuel qui contient une liste de couleurs doit être affiché.  
  
4.  Cliquez sur une couleur dans le menu contextuel. La couleur d’arrière-plan de fenêtre outil doit être remplacée par la couleur sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)   
 [À l’aide et fournir des Services](../extensibility/using-and-providing-services.md)
