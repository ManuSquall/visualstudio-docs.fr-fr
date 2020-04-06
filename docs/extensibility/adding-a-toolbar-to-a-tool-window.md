---
title: Ajout d’une barre d’outils à une fenêtre d’outil ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740244"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Ajouter une barre d’outils à une fenêtre d’outils
Ce pas-là montre comment ajouter une barre d’outils à une fenêtre d’outils.

 Une barre d’outils est une bande horizontale ou verticale qui contient des boutons liés aux commandes. La longueur d’une barre d’outils dans une fenêtre d’outil est toujours la même que la largeur ou la hauteur de la fenêtre d’outil, selon l’endroit où la barre d’outils est amarrée.

 Contrairement aux barres d’outils de l’IDE, une barre d’outils dans une fenêtre d’outils doit être amarrée et ne peut pas être déplacée ou personnalisée. Si le VSPackage est écrit en code umanage, la barre d’outils peut être amarré sur n’importe quel bord.

 Pour plus d’informations sur la façon d’ajouter une barre d’outils, voir [Ajouter une barre d’outils](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Créer une barre d’outils pour une fenêtre d’outils

1. Créez un projet `TWToolbar` VSIX nommé qui a à la fois une commande de menu nommée **TWTestCommand** et une fenêtre d’outils nommée **TestToolWindow**. Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md) et créer une extension avec une fenêtre [d’outil](../extensibility/creating-an-extension-with-a-tool-window.md). Vous devez ajouter le modèle d’élément de commande avant d’ajouter le modèle de fenêtre d’outil.

2. Dans *TWTestCommandPackage.vsct*, recherchez la section Symboles. Dans le nœud GuidSymbol nommé guidTWTestCommandPackageCmdSet déclarer une barre d’outils et un groupe de barre d’outils, comme suit.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. En haut de `Commands` la section, créez une `Menus` section. Ajoutez `Menu` un élément pour définir la barre d’outils.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Les barres d’outils ne peuvent pas être imbriquées comme des sous-hommes. Par conséquent, vous n’avez pas à affecter un parent. En outre, vous n’avez pas à définir une priorité, parce que l’utilisateur peut déplacer les barres d’outils. En règle générale, le placement initial d’une barre d’outils est défini de manière programmatique, mais les modifications ultérieures de l’utilisateur persistent.

4. Dans la section Groupes, définissez un groupe pour contenir les commandes de la barre d’outils.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Dans la section Boutons, changez le parent de l’élément Bouton existant au groupe de barre d’outils afin que la barre d’outils soit affichée.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Par défaut, si une barre d’outils n’a pas de commandes, elle n’apparaît pas.

     Étant donné que la nouvelle barre d’outils n’est pas automatiquement ajoutée à la fenêtre d’outils, la barre d’outils doit être ajoutée explicitement. Cette situation est présentée dans la section suivante.

## <a name="add-the-toolbar-to-the-tool-window"></a>Ajouter la barre d’outils à la fenêtre d’outils

1. Dans *TWTestCommandPackageGuids.cs* ajouter les lignes suivantes.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. Dans *TestToolWindow.cs* ajouter l’instruction suivante à l’aide.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. Dans le constructeur TestToolWindow ajouter la ligne suivante.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Testez la barre d’outils dans la fenêtre d’outils

1. Générez le projet et commencez le débogage. L’instance expérimentale Visual Studio devrait apparaître.

2. Sur le **menu View / Other Windows,** cliquez sur Test **ToolWindow** pour afficher la fenêtre de l’outil.

     Vous devriez voir une barre d’outils (il ressemble à l’icône par défaut) en haut à gauche de la fenêtre d’outil, juste en dessous du titre.

3. Sur la barre d’outils, cliquez sur l’icône pour afficher le message **TWTestCommandPackage Inside TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Voir aussi
- [Ajouter une barre d’outils](../extensibility/adding-a-toolbar.md)
