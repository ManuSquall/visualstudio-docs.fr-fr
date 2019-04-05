---
title: Ajout d’un sous-menu à un Menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d90aecf98bf09d9d4312e28d1bdca055cf9792a3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949334"
---
# <a name="adding-a-submenu-to-a-menu"></a>Ajout d’un sous-menu à un menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas s’appuie sur la démonstration dans [Ajout d’un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) en montrant comment ajouter un sous-menu à la **TestMenu** menu.  
  
 Un sous-menu est un menu secondaire qui s’affiche dans un autre menu. Un sous-menu peut être identifié par la flèche qui suit son nom. Cliquant sur le nom provoque le sous-menu et ses commandes à afficher.  
  
 Cette procédure pas à pas crée un sous-menu dans un menu sur la barre de menus de Visual Studio et place une nouvelle commande dans le sous-menu. La procédure pas à pas implémente également la nouvelle commande.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Ajout d’un sous-menu à un menu  
  
1.  Suivez les étapes de [Ajout d’un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) pour créer l’élément de menu et de projet. Cette procédure pas à pas suppose que le nom du projet VSIX est `TopLevelMenu`.  
  
2.  Ouvrez TestCommandPackage.vsct. Dans le `<Symbols>` , ajoutez un `<IDSymbol>` élément pour le sous-menu, un pour le groupe de sous-menu et un pour la commande, tout en la `<GuidSymbol>` nœud nommé « guidTopLevelMenuCmdSet ». Il s’agit du même nœud qui contient le `<IDSymbol>` élément de menu de niveau supérieur.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Ajouter le sous-menu nouvellement créé à le `<Menus>` section.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     La paire GUID/ID du parent Spécifie le groupe de menus a été généré dans [Ajout d’un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), et est un enfant du menu de niveau supérieur.  
  
4.  Ajouter le groupe de menus défini à l’étape 2 pour le `<Groups>` section et définissez-la comme un enfant du sous-menu.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Ajouter un nouveau `<Button>` élément à la `<Buttons>` section pour définir la commande créée à l’étape 2 en tant qu’élément dans le sous-menu.  
  
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
  
6.  Générez la solution et commencez le débogage. Vous devez voir l’instance expérimentale.  
  
7.  Cliquez sur **TestMenu** pour afficher un sous-menu nommé **sous-menu**. Cliquez sur **sous-menu** et une commande, ouvrez le sous-menu **Test sous-commande**. Notez qu’un clic sur **Test sous-commande** ne fait rien.  
  
## <a name="adding-a-command"></a>Ajout d’une commande  
  
1.  Ouvrez TestCommand.cs et ajoutez l’ID de commande suivant après l’ID de commande existant.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Ajoutez la sous-commande. Recherchez le constructeur de la commande. Ajoutez les lignes suivantes juste après l’appel à la `AddCommand` (méthode).  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     Le `SubItemCallback` Gestionnaire de commandes est défini ultérieurement. Le constructeur doit maintenant ressembler à ceci :  
  
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
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Ajouter SubItemCallback(). Il s’agit de la méthode est appelée lorsque l’utilisateur clique sur la nouvelle commande dans le sous-menu.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
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
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.  
  
5.  Sur le **TestMenu** menu, cliquez sur **sous-menu** puis cliquez sur **Test sous-commande**. Une boîte de message doit apparaître et afficher le texte, « Commande de Test à l’intérieur de TestCommand.SubItemCallback() ».  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
