---
title: Ajout d’une barre d’outils | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: beb97356daf3c932470bf2598e58e1f5b40ea233
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904076"
---
# <a name="add-a-toolbar"></a>Ajouter une barre d’outils
Cette procédure pas à pas montre comment ajouter une barre d’outils à l’IDE de Visual Studio.

 Une barre d’outils est une bande horizontale ou verticale qui contient des boutons liés à des commandes. En fonction de son implémentation, une barre d’outils de l’IDE peut être repositionnée, ancrée sur n’importe quel côté de la fenêtre principale de l’IDE ou effectuée pour rester devant les autres fenêtres.

 En outre, les utilisateurs peuvent ajouter des commandes à une barre d’outils ou les supprimer à l’aide de la boîte de dialogue **personnaliser** . En règle générale, les barres d’outils dans les VSPackages sont personnalisables par l’utilisateur. L’IDE gère toutes les personnalisations, et le VSPackage répond aux commandes. Le VSPackage n’a pas besoin de savoir où se trouve physiquement une commande.

 Pour plus d’informations sur les menus, consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Créer une extension avec une barre d’outils
 Créez un projet VSIX nommé `IDEToolbar` . Ajoutez un modèle d’élément de commande de menu nommé **ToolbarTestCommand**. Pour plus d’informations sur la façon de procéder, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Créer une barre d’outils pour l’IDE

1. Dans *ToolbarTestCommandPackage. vsct*, recherchez la section Symbols. Dans l’élément GuidSymbol nommé guidToolbarTestCommandPackageCmdSet, ajoutez les déclarations d’une barre d’outils et d’un groupe de barres d’outils, comme suit.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. En haut de la section commandes, créez une section menus. Ajoutez un élément de menu à la section menus pour définir votre barre d’outils.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Les barres d’outils ne peuvent pas être imbriquées comme des sous-menus. Par conséquent, il n’est pas nécessaire d’affecter un groupe parent. En outre, il n’est pas nécessaire de définir une priorité, car l’utilisateur peut déplacer des barres d’outils. En général, le placement initial d’une barre d’outils est défini par programme, mais les modifications ultérieures de l’utilisateur sont conservées.

3. Dans la section [groupes](../extensibility/groups-element.md) , après l’entrée de groupe existante, définissez un élément de [groupe](../extensibility/group-element.md) pour qu’il contienne les commandes de la barre d’outils.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Faites apparaître le bouton dans la barre d’outils. Dans la section Buttons, remplacez le bloc parent dans le bouton par la barre d’outils. Le bloc de bouton résultant doit se présenter comme suit :

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Par défaut, si une barre d’outils n’a pas de commande, elle n’apparaît pas.

5. Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.

6. Cliquez avec le bouton droit sur la barre de menus de Visual Studio pour afficher la liste des barres d’outils. Sélectionnez la **barre d’outils test**.

7. Vous devez maintenant voir votre barre d’outils sous forme d’icône à droite de l’icône Rechercher dans les fichiers. Lorsque vous cliquez sur l’icône, vous devez voir une boîte de message indiquant **ToolbarTestCommandPackage. À l’intérieur de IDEToolbar. ToolbarTestCommand. MenuItemCallback ()**.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
