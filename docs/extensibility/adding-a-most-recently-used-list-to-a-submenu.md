---
title: Ajout d’une liste la plus récemment utilisée à un Submenu (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740302"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Ajouter une liste plus récemment utilisée à un sous-mois
Ce pas-là s’appuie sur les démonstrations dans [Ajouter un sous-mois à un menu](../extensibility/adding-a-submenu-to-a-menu.md), et montre comment ajouter une liste dynamique à un sous-mois. La liste dynamique constitue la base de la création d’une liste la plus récemment utilisée (MRU).

Une liste de menu dynamique commence par un placeholder sur un menu. Chaque fois que le menu est affiché, l’environnement de développement intégré Visual Studio (IDE) demande au VSPackage toutes les commandes qui doivent être affichées au lieuholder. Une liste dynamique peut se produire n’importe où sur un menu. Cependant, les listes dynamiques sont généralement stockées et affichées par elles-mêmes sur le sous-genre ou au bas des menus. En utilisant ces modèles de conception, vous permettez à la liste dynamique des commandes de s’étendre et de contracter sans affecter la position d’autres commandes sur le menu. Dans cette procédure pas à pas, la liste MRU dynamique est affichée au bas d’un sous-mois existant, séparé du reste du sous-régime par une ligne.

Techniquement, une liste dynamique peut également être appliquée à une barre d’outils. Cependant, nous décourageons cette utilisation parce qu’une barre d’outils doit rester inchangée à moins que l’utilisateur ne prenne des mesures spécifiques pour la modifier.

Cette procédure pas à pas crée une liste MRU de quatre éléments qui changent leur commande chaque fois que l’un d’eux est sélectionné (l’élément sélectionné se déplace vers le haut de la liste).

Pour plus d’informations sur les menus et les fichiers *.vsct,* voir [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prérequis
Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Créer une extension

- Suivez les procédures dans [l’ajout d’un sous-mois à un menu](../extensibility/adding-a-submenu-to-a-menu.md) pour créer le sous-mois qui est modifié dans les procédures suivantes.

  Les procédures dans cette procédure pas à pas supposent `TopLevelMenu`que le nom de la VSPackage est , qui est le nom qui est utilisé dans [Ajouter un menu à la barre de menu Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Créer une commande dynamique de liste d’éléments

1. Open *TestCommandPackage.vsct*.

2. Dans `Symbols` la section, `GuidSymbol` dans le nœud nommé guidTestCommandPackageCmdSet, ajoutez le symbole pour le `MRUListGroup` groupe et la `cmdidMRUList` commande, comme suit.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Dans `Groups` la section, ajouter le groupe déclaré après les entrées de groupe existantes.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. Dans `Buttons` la section, ajoutez un nœud pour représenter la commande nouvellement déclarée, après les entrées de bouton existantes.

    ```csharp
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"
        type="Button" priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />
        <CommandFlag>DynamicItemStart</CommandFlag>
        <Strings>
            <CommandName>cmdidMRUList</CommandName>
            <ButtonText>MRU Placeholder</ButtonText>
        </Strings>
    </Button>
    ```

    Le `DynamicItemStart` drapeau permet de générer la commande de façon dynamique.

5. Construisez le projet et commencez à débogage pour tester l’affichage de la nouvelle commande.

    Sur le menu **TestMenu,** cliquez sur le nouveau sous-menu submenu, **Sous-menu**, pour afficher la nouvelle commande, **MRU Placeholder**. Une fois qu’une liste dynamique de commandes MRU sera mise en œuvre dans la procédure suivante, cette étiquette de commande sera remplacée par cette liste chaque fois que le sous-marin est ouvert.

## <a name="filling-the-mru-list"></a>Remplir la liste MRU

1. Dans *TestCommandPackageGuids.cs*, ajouter les lignes suivantes après les cartes `TestCommandPackageGuids` de commande existantes dans la définition de classe.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. Dans *TestCommand.cs* ajouter l’instruction suivante à l’aide.

    ```csharp
    using System.Collections;
    ```

3. Ajoutez le code suivant dans le constructeur TestCommand après le dernier appel AddCommand. Le `InitMRUMenu` sera défini plus tard

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Ajoutez le code suivant dans la classe TestCommand. Ce code est parascatifisé la liste des chaînes qui représentent les éléments à montrer sur la liste MRU.

    ```csharp
    private int numMRUItems = 4;
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;
    private ArrayList mruList;

    private void InitializeMRUList()
    {
        if (null == this.mruList)
        {
            this.mruList = new ArrayList();
            if (null != this.mruList)
            {
                for (int i = 0; i < this.numMRUItems; i++)
                {
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,
                        "Item {0}", i + 1));
                }
            }
        }
    }
    ```

5. Après `InitializeMRUList` la méthode, `InitMRUMenu` ajouter la méthode. Ceci initialise les commandes de menu de liste MRU.

    ```csharp
    private void InitMRUMenu(OleMenuCommandService mcs)
    {
        InitializeMRUList();
        for (int i = 0; i < this.numMRUItems; i++)
        {
            var cmdID = new CommandID(
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);
            var mc = new OleMenuCommand(
                new EventHandler(OnMRUExec), cmdID);
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);
            mcs.AddCommand(mc);
        }
    }
    ```

    Vous devez créer un objet de commande de menu pour chaque élément possible de la liste MRU. L’IDE `OnMRUQueryStatus` appelle la méthode pour chaque élément de la liste MRU jusqu’à ce qu’il n’y ait plus d’éléments. Dans le code géré, la seule façon pour l’IDE de savoir qu’il n’y a plus d’éléments est de créer tous les éléments possibles en premier. Si vous le souhaitez, vous pouvez marquer des `mc.Visible = false;` éléments supplémentaires comme il n’est pas visible au début en utilisant après la commande du menu est créé. Ces éléments peuvent ensuite être `mc.Visible = true;` rendus `OnMRUQueryStatus` visibles plus tard en utilisant dans la méthode.

6. Après `InitMRUMenu` la méthode, `OnMRUQueryStatus` ajoutez la méthode suivante. C’est le gestionnaire qui définit le texte pour chaque élément MRU.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Après `OnMRUQueryStatus` la méthode, `OnMRUExec` ajoutez la méthode suivante. Il s’agit du gestionnaire pour la sélection d’un article MRU. Cette méthode déplace l’élément sélectionné en haut de la liste, puis affiche l’élément sélectionné dans une boîte de message.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
                for (int i = MRUItemIndex; i > 0; i--)
                {
                    this.mruList[i] = this.mruList[i - 1];
                }
                this.mruList[0] = selection;
                System.Windows.Forms.MessageBox.Show(
                    string.Format(CultureInfo.CurrentCulture,
                                  "Selected {0}", selection));
            }
        }
    }

    ```

## <a name="testing-the-mru-list"></a>Test de la liste MRU

1. Générez le projet et commencez le débogage.

2. Sur le menu **TestMenu,** cliquez sur **Invoke TestCommand**. Cela affiche une boîte de message qui indique que la commande a été sélectionnée.

    > [!NOTE]
    > Cette étape est nécessaire pour forcer le VSPackage à charger et à afficher correctement la liste MRU. Si vous sautez cette étape, la liste MRU n’est pas affichée.

3. Sur le menu **du menu Du menu Test,** cliquez sur Sous **Menu**. Une liste de quatre éléments est affichée à la fin du sous-mois, en dessous d’un séparateur. Lorsque vous cliquez sur **l’élément 3**, une boîte de message doit apparaître et afficher le texte, **Élément Sélectionné 3**. (Si la liste des quatre éléments n’est pas affichée, assurez-vous d’avoir suivi les instructions dans l’étape précédente.)

4. Ouvrez à nouveau le sous-mois. Notez que **l’article 3** est maintenant en haut de la liste et les autres éléments ont été poussés vers le bas d’une position. Cliquez à nouveau **sur l’élément 3** et remarquez que la boîte de message affiche toujours **l’élément 3 sélectionné**, ce qui indique que le texte s’est correctement déplacé vers la nouvelle position avec l’étiquette de commande.

## <a name="see-also"></a>Voir aussi
- [Ajout dynamique d’éléments de menu](../extensibility/dynamically-adding-menu-items.md)
