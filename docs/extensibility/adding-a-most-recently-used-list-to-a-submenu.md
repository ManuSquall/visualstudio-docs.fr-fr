---
title: Ajout d’une liste des derniers fichiers utilisés à un sous-menu | Microsoft Docs
description: Découvrez comment ajouter une liste dynamique qui contient les commandes de menu les plus récemment utilisées à un sous-menu dans l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bdff50655f846ced91e59a93a2d264bb06641ed1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951548"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Ajouter une liste des derniers fichiers utilisés à un sous-menu
Cette procédure pas à pas s’appuie sur les démonstrations dans [Ajouter un sous-menu à un menu](../extensibility/adding-a-submenu-to-a-menu.md)et montre comment ajouter une liste dynamique à un sous-menu. La liste dynamique forme la base de la création d’une liste des derniers fichiers utilisés.

Une liste de menus dynamique commence par un espace réservé dans un menu. Chaque fois que le menu est affiché, l’environnement de développement intégré (IDE) de Visual Studio demande au VSPackage toutes les commandes qui doivent être affichées dans l’espace réservé. Une liste dynamique peut apparaître n’importe où dans un menu. Toutefois, les listes dynamiques sont généralement stockées et affichées par elles-mêmes sur les sous-menus ou en bas des menus. À l’aide de ces modèles de conception, vous activez la liste dynamique des commandes pour développer et contracter sans affecter la position des autres commandes dans le menu. Dans cette procédure pas à pas, la liste des fichiers récents dynamiques s’affiche au bas d’un sous-menu existant, en les séparant du reste du sous-menu par une ligne.

Techniquement, une liste dynamique peut également être appliquée à une barre d’outils. Toutefois, nous déconseillons l’utilisation, car une barre d’outils ne doit pas être modifiée, à moins que l’utilisateur ne prenne des mesures spécifiques pour la modifier.

Cette procédure pas à pas crée une liste MRU de quatre éléments qui modifient leur ordre chaque fois que l’un d’eux est sélectionné (l’élément sélectionné se déplace vers le haut de la liste).

Pour plus d’informations sur les menus et les fichiers *. vsct* , consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prérequis
Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Créer une extension

- Suivez les procédures décrites dans [Ajout d’un sous-menu à un menu](../extensibility/adding-a-submenu-to-a-menu.md) pour créer le sous-menu modifié dans les procédures suivantes.

  Les procédures de cette procédure pas à pas supposent que le nom du VSPackage est `TestCommand` , qui est le nom utilisé dans [Ajouter un menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Créer une commande de liste d’éléments dynamiques

1. Ouvrez *TestCommandPackage. vsct*.

2. Dans la `Symbols` section, dans le `GuidSymbol` nœud nommé guidTestCommandPackageCmdSet, ajoutez le symbole du `MRUListGroup` groupe et de la `cmdidMRUList` commande, comme suit.

    ```xml
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. Dans la `Groups` section, ajoutez le groupe déclaré après les entrées de groupe existantes.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

4. Dans la `Buttons` section, ajoutez un nœud pour représenter la commande nouvellement déclarée, après les entrées de bouton existantes.

    ```xml
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

    L' `DynamicItemStart` indicateur permet de générer la commande dynamiquement.

5. Générez le projet et commencez le débogage pour tester l’affichage de la nouvelle commande.

    Dans le menu **TestMenu** , cliquez sur le nouveau sous-menu, **sous-menu**, pour afficher la nouvelle commande, l' **espace réservé MRU**. Une fois qu’une liste de commandes récentes dynamique est implémentée dans la procédure suivante, cette étiquette de commande est remplacée par cette liste chaque fois que le sous-menu est ouvert.

## <a name="filling-the-mru-list"></a>Remplissage de la liste des fichiers récents

1. Dans *TestCommandPackageGuids.cs*, ajoutez les lignes suivantes après les ID de commande existants dans la `TestCommandPackageGuids` définition de classe.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. Dans *TestCommand.cs* , ajoutez l’instruction using suivante.

    ```csharp
    using System.Collections;
    ```

3. Ajoutez le code suivant dans le constructeur test après le dernier appel AddCommand. La `InitMRUMenu` sera définie ultérieurement

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Ajoutez le code suivant dans la classe test. Ce code initialise la liste de chaînes qui représentent les éléments à afficher dans la liste MRU.

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

5. Après la `InitializeMRUList` méthode, ajoutez la `InitMRUMenu` méthode. Cela initialise les commandes de menu de liste MRU.

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

    Vous devez créer un objet de commande de menu pour chaque élément possible dans la liste des fichiers récents. L’IDE appelle la `OnMRUQueryStatus` méthode pour chaque élément de la liste MRU jusqu’à ce qu’il n’y ait plus d’éléments. Dans le code managé, le seul moyen pour l’IDE de savoir qu’il n’y a plus d’éléments consiste à créer d’abord tous les éléments possibles. Si vous le souhaitez, vous pouvez marquer d’autres éléments comme non visibles au préalable à l’aide de `mc.Visible = false;` après la création de la commande de menu. Ces éléments peuvent ensuite être rendus visibles ultérieurement à l’aide `mc.Visible = true;` de dans la `OnMRUQueryStatus` méthode.

6. Après la `InitMRUMenu` méthode, ajoutez la `OnMRUQueryStatus` méthode suivante. Il s’agit du gestionnaire qui définit le texte de chaque élément MRU.

    ```csharp
    private void OnMRUQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                menuCommand.Text = this.mruList[MRUItemIndex] as string;
            }
        }
    }
    ```

7. Après la `OnMRUQueryStatus` méthode, ajoutez la `OnMRUExec` méthode suivante. Il s’agit du gestionnaire permettant de sélectionner un élément MRU. Cette méthode déplace l’élément sélectionné vers le haut de la liste, puis affiche l’élément sélectionné dans une boîte de message.

    ```csharp
    private void OnMRUExec(object sender, EventArgs e)
    {
        var menuCommand = sender as OleMenuCommand;
        if (null != menuCommand)
        {
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)
            {
                string selection = this.mruList[MRUItemIndex] as string;
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

## <a name="testing-the-mru-list"></a>Test de la liste des fichiers récents

1. Générez le projet et commencez le débogage.

2. Dans le menu **TestMenu** , cliquez sur **appeler test**. Cette action affiche une boîte de message qui indique que la commande a été sélectionnée.

    > [!NOTE]
    > Cette étape est nécessaire pour forcer le téléchargement du VSPackage et l’affichage correct de la liste MRU. Si vous ignorez cette étape, la liste MRU n’est pas affichée.

3. Dans le menu **test** , cliquez sur **sous-menu**. Une liste de quatre éléments s’affiche à la fin du sous-menu, sous un séparateur. Lorsque vous cliquez sur l' **élément 3**, une boîte de message doit apparaître et afficher le texte, l' **élément sélectionné 3**. (Si la liste de quatre éléments n’est pas affichée, vérifiez que vous avez suivi les instructions de l’étape précédente.)

4. Ouvrez à nouveau le sous-menu. Notez que l' **élément 3** est maintenant en haut de la liste et que les autres éléments ont été poussés d’une position. Cliquez à nouveau sur l' **élément 3** et remarquez que la boîte de message affiche toujours l' **élément sélectionné 3**, ce qui indique que le texte a été correctement déplacé vers la nouvelle position avec l’étiquette de commande.

## <a name="see-also"></a>Voir aussi
- [Ajouter dynamiquement des éléments de menu](../extensibility/dynamically-adding-menu-items.md)
