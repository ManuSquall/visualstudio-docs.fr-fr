---
title: "Ajout d&#39;un contr&#244;leur de Menu &#224; une barre d&#39;outils | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barres d'outils (Visual Studio), ajout de contrôleurs de menu"
  - "menus, ajouter des contrôleurs de menu aux barres d'outils"
  - "contrôleurs de menu, ajouter aux barres d'outils"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# Ajout d&#39;un contr&#244;leur de Menu &#224; une barre d&#39;outils
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas s'appuie sur le [Ajout d'une barre d'outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) procédure pas à pas et vous montre comment ajouter un contrôleur de menu à la barre d'outils de la fenêtre outil. Les étapes ci\-après peuvent également être appliqués à la barre d'outils qui est créé dans le [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md) procédure pas à pas.  
  
 Un contrôleur de menu est un contrôle partagé. Le côté gauche du contrôleur de menu affiche la commande utilisé en dernier, et il peut être exécuté en cliquant dessus. Le côté droit du contrôleur de menu est une flèche qui, lorsqu'on clique dessus, ouvre une liste de commandes supplémentaires. Lorsque vous cliquez sur une commande dans la liste, la commande s'exécute, et il remplace la commande sur le côté gauche du contrôleur de menu. De cette façon, le contrôleur de menu fonctionne comme un bouton de commande qui affiche la commande utilisés en dernier dans la liste.  
  
 Contrôleurs de menu peuvent apparaître dans les menus, mais elles sont souvent utilisées dans les barres d'outils.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d'un contrôleur de Menu  
  
#### Pour créer un contrôleur de menu  
  
1.  Suivez la procédure décrite dans [Ajout d'une barre d'outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) pour créer une fenêtre outil qui a une barre d'outils.  
  
2.  Dans TWTestCommandPackage.vsct, accédez à la section de symboles. Dans l'élément GuidSymbol **guidTWTestCommandPackageCmdSet**, déclarez votre contrôleur de menu, groupe de contrôleurs de menu et trois éléments de menu.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  Dans la section de Menus, après la dernière entrée de menu, définissez le contrôleur de menu sous forme de menu.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Le `TextChanges` et `TextIsAnchorCommand` indicateurs doivent être inclus pour permettre le contrôleur de menu afin de refléter la dernière commande sélectionnée.  
  
4.  Dans les groupes de section, après la dernière entrée de groupe, ajoutez le groupe de contrôleurs de menu.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     En définissant le contrôleur menu comme parent, toutes les commandes placées dans ce groupe seront affiche dans le contrôleur de menu. Le `priority` attribut est omis, ce qui lui affecte la valeur par défaut 0, car il s'agit du groupe uniquement sur le contrôleur de menu.  
  
5.  Dans la section boutons, après la dernière entrée du bouton, ajoutez un élément de bouton pour chacun de vos éléments de menu.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  À ce stade, vous pouvez consulter le contrôleur de menu. Générez le projet et commencez le débogage. Vous devez voir l'instance expérimentale.  
  
    1.  Sur le **affichage \/ autres fenêtres** menu, ouvrez **Test \(fenêtre outil\)**.  
  
    2.  Le contrôleur de menu s'affiche dans la barre d'outils dans la fenêtre outil.  
  
    3.  Cliquez sur la flèche à droite du contrôleur menu pour voir les trois commandes possibles.  
  
     Notez que lorsque vous cliquez sur une commande, le titre du contrôleur de menu change pour afficher cette commande. Dans la section suivante, nous allons ajouter le code pour activer ces commandes.  
  
## Implémentation des commandes de contrôleur de Menu  
  
1.  Dans TWTestCommandPackageGuids.cs, ajoutez les ID de commande pour vos trois éléments de menu après l'ID de commande existante.  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  Dans TWTestCommand.cs, ajoutez le code suivant en haut de la classe TWTestCommand.  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  Dans le constructeur TWTestCommand, après le dernier appel à la `AddCommand` \(méthode\), ajoutez le code pour acheminer les événements pour chaque commande via les gestionnaires de mêmes.  
  
    ```c#  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Ajoutez un gestionnaire d'événements à la classe TWTestCommand pour marquer la commande sélectionnée comme activé.  
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Ajoutez un gestionnaire d'événements qui affiche un MessageBox lorsque l'utilisateur sélectionne une commande sur le contrôleur de menu :  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## Test du contrôleur de Menu  
  
1.  Générez le projet et commencez le débogage. Vous devez voir l'instance expérimentale.  
  
2.  Ouvrez le **Test \(fenêtre outil\)** sur le **affichage \/ autres fenêtres** menu.  
  
     Le contrôleur de menu s'affiche dans la barre d'outils dans la fenêtre outil et affiche **MC élément 1**.  
  
3.  Cliquez sur le bouton de contrôleur de menu à gauche de la flèche.  
  
     Vous devez voir trois éléments, le premier d'entre eux est sélectionné et comprend une zone de surbrillance autour de son icône. Cliquez sur **élément MC 3**.  
  
     Une boîte de dialogue s'affiche avec le message **vous avez sélectionné le contrôleur de Menu Item 3**. Notez que le message correspond au texte sur le bouton de contrôleur de menu. Contrôleur maintenant affiche **MC élément 3**.  
  
## Voir aussi  
 [Ajout d'une barre d'outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md)