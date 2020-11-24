---
title: Ajout d’un contrôleur de menu à une barre d’outils | Microsoft Docs
description: Apprenez à créer un contrôleur de menu et à l’ajouter à une barre d’outils de la fenêtre outil dans Visual Studio, puis à implémenter les commandes du contrôleur de menu et à le tester.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 3ce14999913a3928cbe25d9f034c8288651629a3
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597819"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Ajouter un contrôleur de menu à une barre d’outils
Cette procédure pas à pas s’appuie sur la procédure pas à pas [Ajouter une barre d’outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) et montre comment ajouter un contrôleur de menu à la barre d’outils de la fenêtre outil. Les étapes décrites ici peuvent également être appliquées à la barre d’outils créée dans la procédure pas à pas [Ajouter une barre d’outils](../extensibility/adding-a-toolbar.md) .

Un contrôleur de menu est un contrôle de fractionnement. Le côté gauche du contrôleur de menu affiche la dernière commande utilisée et vous pouvez l’exécuter en cliquant dessus. La partie droite du contrôleur de menu est une flèche qui, lorsque vous cliquez dessus, ouvre une liste de commandes supplémentaires. Lorsque vous cliquez sur une commande de la liste, la commande s’exécute et remplace la commande sur le côté gauche du contrôleur de menu. De cette façon, le contrôleur de menu fonctionne comme un bouton de commande qui affiche toujours la dernière commande utilisée dans une liste.

Les contrôleurs de menu peuvent apparaître dans les menus, mais ils sont le plus souvent utilisés sur les barres d’outils.

## <a name="prerequisites"></a>Prérequis
À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Créer un contrôleur de menu

1. Suivez les procédures décrites dans [Ajouter une barre d’outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) pour créer une fenêtre outil avec une barre d’outils.

2. Dans *TWTestCommandPackage. vsct*, accédez à la section Symbols. Dans l’élément GuidSymbol nommé **guidTWTestCommandPackageCmdSet**, déclarez votre contrôleur de menu, le groupe de contrôleurs de menu et trois éléments de menu.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Dans la section menus, après la dernière entrée de menu, définissez le contrôleur de menu en tant que menu.

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

    Les `TextChanges` `TextIsAnchorCommand` indicateurs et doivent être inclus pour permettre au contrôleur de menu de refléter la dernière commande sélectionnée.

4. Dans la section groupes, après la dernière entrée de groupe, ajoutez le groupe de contrôleurs de menu.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    En définissant le contrôleur de menu en tant que parent, toutes les commandes placées dans ce groupe apparaissent dans le contrôleur de menu. L' `priority` attribut est omis, ce qui lui affecte la valeur par défaut 0, car il s’agit du seul groupe sur le contrôleur de menu.

5. Dans la section Buttons, après la dernière entrée du bouton, ajoutez un élément Button pour chacun de vos éléments de menu.

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

6. À ce stade, vous pouvez examiner le contrôleur de menu. Générez le projet et commencez le débogage. Vous devez voir l’instance expérimentale.

   1. Dans le menu **affichage/autres fenêtres** , ouvrez **test ToolWindow**.

   2. Le contrôleur de menu apparaît dans la barre d’outils de la fenêtre outil.

   3. Cliquez sur la flèche sur le côté droit du contrôleur de menu pour afficher les trois commandes possibles.

      Notez que lorsque vous cliquez sur une commande, le titre du contrôleur de menu change pour afficher cette commande. Dans la section suivante, nous allons ajouter le code permettant d’activer ces commandes.

## <a name="implement-the-menu-controller-commands"></a>Implémenter les commandes de contrôleur de menu

1. Dans *TWTestCommandPackageGuids.cs*, ajoutez des ID de commande pour vos trois éléments de menu après les ID de commande existants.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. Dans *TWTestCommand.cs*, ajoutez le code suivant en haut de la `TWTestCommand` classe.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. Dans le constructeur TWTestCommand, après le dernier appel à la `AddCommand` méthode, ajoutez du code pour acheminer les événements pour chaque commande via les mêmes gestionnaires.

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

4. Ajoutez un gestionnaire d’événements à la classe **TWTestCommand** pour marquer la commande sélectionnée comme activée.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Ajoutez un gestionnaire d’événements qui affiche un MessageBox quand l’utilisateur sélectionne une commande sur le contrôleur de menu :

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
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

1. Générez le projet et commencez le débogage. Vous devez voir l’instance expérimentale.

2. Ouvrez la vue de **test** dans le menu **affichage/autres fenêtres** .

    Le contrôleur de menu s’affiche dans la barre d’outils de la fenêtre outil et affiche l' **élément MC 1**.

3. Cliquez sur le bouton de contrôleur de menu à gauche de la flèche.

    Vous devez voir trois éléments, le premier étant sélectionné et une zone de surbrillance autour de son icône. Cliquez sur **MC Item 3**.

    Une boîte de dialogue s’affiche avec le message **que vous avez sélectionné élément de contrôleur de menu 3**. Notez que le message correspond au texte du bouton du contrôleur de menu. Le bouton de contrôleur de menu affiche maintenant l' **élément MC 3**.

## <a name="see-also"></a>Voir aussi
- [Ajout d’une barre d’outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md)
