---
title: Ajout d’un contrôleur de menu à une barre d’outils . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740319"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Ajouter un contrôleur de menu à une barre d’outils
Cette procédure pas à pas s’appuie sur la [barre d’outils Ajouter une barre d’outils à une fenêtre d’outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) pas à pas et montre comment ajouter un contrôleur de menu à la barre d’outils de fenêtre d’outil. Les étapes indiquées ici peuvent également être appliquées sur la barre d’outils qui est créé dans le [Add a toolbar](../extensibility/adding-a-toolbar.md) pas à pas.

Un contrôleur de menu est un contrôle fractionné. Le côté gauche du contrôleur de menu affiche la dernière commande utilisée, et vous pouvez l’exécuter en cliquant dessus. Le côté droit du contrôleur de menu est une flèche qui, une fois cliqué, ouvre une liste de commandes supplémentaires. Lorsque vous cliquez sur une commande sur la liste, la commande s’exécute, et elle remplace la commande sur le côté gauche du contrôleur de menu. De cette façon, le contrôleur de menu fonctionne comme un bouton de commande qui affiche toujours la dernière commande utilisée à partir d’une liste.

Les contrôleurs de menu peuvent apparaître sur les menus, mais ils sont le plus souvent utilisés sur les barres d’outils.

## <a name="prerequisites"></a>Prérequis
A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Créer un contrôleur de menu

1. Suivez les procédures décrites dans [Ajouter une barre d’outils à une fenêtre d’outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) pour créer une fenêtre d’outils qui a une barre d’outils.

2. Dans *TWTestCommandPackage.vsct*, rendez-vous à la section Symboles. Dans l’élément GuidSymbol nommé **guidTWTestCommandPackageCmdSet**, déclarez votre contrôleur de menu, le groupe de contrôleur de menu, et trois éléments de menu.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Dans la section Menus, après la dernière entrée du menu, définissez le contrôleur de menu comme un menu.

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

    Le `TextChanges` `TextIsAnchorCommand` et les drapeaux doivent être inclus pour permettre au contrôleur de menu de refléter la dernière commande sélectionnée.

4. Dans la section Groupes, après la dernière entrée de groupe, ajoutez le groupe de contrôleur de menu.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    En définissant le contrôleur de menu en tant que parent, toutes les commandes placées dans ce groupe apparaissent dans le contrôleur de menu. L’attribut `priority` est omis, ce qui le définit à la valeur par défaut de 0, car il est le seul groupe sur le contrôleur de menu.

5. Dans la section Boutons, après la dernière entrée du bouton, ajoutez un élément Bouton pour chacun de vos éléments de menu.

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

6. À ce stade, vous pouvez regarder le contrôleur de menu. Générez le projet et commencez le débogage. Vous devriez voir l’instance expérimentale.

   1. Sur la vue / Autre menu **Windows,** ouvert **Test ToolWindow**.

   2. Le contrôleur de menu apparaît sur la barre d’outils dans la fenêtre de l’outil.

   3. Cliquez sur la flèche sur le côté droit du contrôleur de menu pour voir les trois commandes possibles.

      Notez que lorsque vous cliquez sur une commande, le titre du contrôleur de menu change pour afficher cette commande. Dans la section suivante, nous ajouterons le code pour activer ces commandes.

## <a name="implement-the-menu-controller-commands"></a>Implémenter les commandes de contrôleur de menu

1. Dans *TWTestCommandPackageGuids.cs*, ajoutez des pièces d’ID de commande pour vos trois éléments de menu après les pièces d’ID de commande existantes.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. En *TWTestCommand.cs*, ajoutez le code suivant en `TWTestCommand` haut de la classe.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. Dans le constructeur TWTestCommand, après le `AddCommand` dernier appel à la méthode, ajoutez du code pour acheminer les événements pour chaque commande à travers les mêmes gestionnaires.

    ```csharp
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

4. Ajoutez un gestionnaire d’événements à la classe **TWTestCommand** pour marquer la commande sélectionnée telle qu’elle est vérifiée.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Ajoutez un gestionnaire d’événements qui affiche une Boîte à messages lorsque l’utilisateur sélectionne une commande sur le contrôleur de menu :

    ```csharp
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

## <a name="testing-the-menu-controller"></a>Test du contrôleur de menu

1. Générez le projet et commencez le débogage. Vous devriez voir l’instance expérimentale.

2. Ouvrez le **Test ToolWindow** sur le menu **View / Autres Fenêtres.**

    Le contrôleur de menu apparaît dans la barre d’outils dans la fenêtre de l’outil et affiche **l’article MC 1**.

3. Cliquez sur le bouton du contrôleur de menu à gauche de la flèche.

    Vous devriez voir trois éléments, dont le premier est sélectionné et dispose d’une boîte de surbrillance autour de son icône. Cliquez sur **MC Item 3**.

    Une boîte de dialogue apparaît avec le message **Que vous avez sélectionné l’élément de contrôleur de menu 3**. Notez que le message correspond au texte sur le bouton du contrôleur de menu. Le bouton du contrôleur de menu affiche maintenant **MC Item 3**.

## <a name="see-also"></a>Voir aussi
- [Ajout d’une barre d’outils à une fenêtre d’outils](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md)
