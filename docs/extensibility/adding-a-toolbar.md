---
title: Ajout d’une barre d’outils Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740223"
---
# <a name="add-a-toolbar"></a>Ajouter une barre d’outils
Ce pas-là montre comment ajouter une barre d’outils à l’IDE Visual Studio.

 Une barre d’outils est une bande horizontale ou verticale qui contient des boutons qui sont liés aux commandes. Selon sa mise en œuvre, une barre d’outils dans l’IDE peut être repositionnée, amarrée de n’importe quel côté de la fenêtre principale de l’IDE, ou faite pour rester devant d’autres fenêtres.

 En outre, les utilisateurs peuvent ajouter des commandes à une barre d’outils ou les supprimer de celui-ci en utilisant la boîte de dialogue **Customize.** En règle générale, les barres d’outils dans VSPackages sont personnalisables par l’utilisateur. L’IDE gère toute personnalisation, et le VSPackage répond aux commandes. Le VSPackage n’a pas besoin de savoir où se trouve physiquement une commande.

 Pour plus d’informations sur les menus, consultez [les commandes, les menus et les barres d’outils.](../extensibility/internals/commands-menus-and-toolbars.md)

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Créer une extension avec une barre d’outils
 Créer un projet `IDEToolbar`VSIX nommé . Ajoutez un modèle d’élément de commande de menu nommé **ToolbarTestCommand**. Pour plus d’informations sur la façon de le faire, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Créer une barre d’outils pour l’IDE

1. Dans *ToolbarTestCommandPackage.vsct*, recherchez la section Symboles. Dans l’élément GuidSymbol nommé guidToolbarTestCommandPackageCmdSet, ajoutez des déclarations pour une barre d’outils et un groupe de barre d’outils, comme suit.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. En haut de la section Commandes, créez une section Menus. Ajoutez un élément de menu à la section Menus pour définir votre barre d’outils.

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

     Les barres d’outils ne peuvent pas être imbriquées comme des sous-hommes. Par conséquent, vous n’avez pas à affecter un groupe parent. En outre, vous n’avez pas à définir une priorité, parce que l’utilisateur peut déplacer les barres d’outils. En règle générale, le placement initial d’une barre d’outils est défini de manière programmatique, mais les modifications ultérieures de l’utilisateur persistent.

3. Dans la section [Groupes,](../extensibility/groups-element.md) après l’entrée de groupe existante, définissez un élément [du Groupe](../extensibility/group-element.md) pour contenir les commandes de la barre d’outils.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Faites apparaître le bouton sur la barre d’outils. Dans la section Boutons, remplacez le bloc Parent dans le bouton à la barre d’outils. Le bloc Bouton résultant devrait ressembler à ceci:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Par défaut, si une barre d’outils n’a pas de commandes, elle n’apparaît pas.

5. Générez le projet et commencez le débogage. L’instance expérimentale devrait apparaître.

6. Cliquez à droite sur la barre de menu Visual Studio pour obtenir la liste des barres d’outils. Sélectionnez **Test Toolbar**.

7. Vous devriez maintenant voir votre barre d’outils comme une icône à droite de l’icône Trouver dans les fichiers. Lorsque vous cliquez sur l’icône, vous devriez voir une boîte de message qui indique **ToolbarTestCommandPackage. À l’intérieur IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
