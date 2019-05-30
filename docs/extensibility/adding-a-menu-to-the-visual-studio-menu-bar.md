---
title: Ajout d’un Menu à la barre de menus de Visual Studio | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a28e7f69ed8e9a76e11d8892ee677435f75c99b2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349792"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Ajouter un menu dans la barre de menus de Visual Studio

Cette procédure pas à pas montre comment ajouter un menu dans la barre de menus de l’environnement de développement intégré (IDE) Visual Studio. La barre de menus IDE contient des catégories de menu comme **fichier**, **modifier**, **vue**, **fenêtre**, et **aide** .

Avant d’ajouter un nouveau menu à la barre de menus de Visual Studio, considérez si vos commandes doivent être placés dans un menu existant. Pour plus d’informations sur le placement de commande, consultez [Menus et commandes de Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Menus sont déclarés dans le *.vsct* fichier du projet. Pour plus d’informations sur les menus et *.vsct* de fichiers, consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

En fin de cette procédure pas à pas, vous pouvez créer un menu nommé **TestMenu** qui contient une seule commande.

> [!NOTE]
> Dans Visual Studio 2019, les menus de niveau supérieur fournis par les extensions sont placés sous le **Extensions** menu.

## <a name="prerequisites"></a>Prérequis

À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Créez un projet VSIX qui dispose d’un modèle d’élément de commande personnalisée

1. Créez un projet VSIX nommé `TopLevelMenu`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue en recherchant « vsix ».  Pour plus d’informations, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Quand le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisée nommé **commande de test**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** >  **un nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **commande personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom de fichier de commande pour *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Créer un menu dans la barre de menus IDE

::: moniker range="vs-2017"

1. Dans **l’Explorateur de solutions**, ouvrez *TestCommandPackage.vsct*.

    À la fin du fichier, il existe un \<symboles > nœud qui contient plusieurs \<GuidSymbol > nœuds. Dans le nœud nommé guidTestCommandPackageCmdSet, ajoutez un nouveau symbole, comme suit :

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Créer un vide \<Menus > nœud dans le \<commandes > nœud, juste avant \<groupes >. Dans le \<Menus > nœud, ajoutez un \<Menu > nœud, comme suit :

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Le `guid` et `id` valeurs du menu spécifient le jeu de commandes et dans le menu spécifique dans le jeu de commandes.

    Le `guid` et `id` valeurs du parent positionnement le menu sur la section de la barre de menus de Visual Studio qui contient les menus d’outils et compléments.

    La valeur de la `CommandName` chaîne indique que le texte doit apparaître dans l’élément de menu.

3. Dans le \<groupes > section, recherchez le \<groupe > et modifier le \<Parent > élément pour pointer vers le menu que nous venons d’ajouter :

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Cela rend la partie du groupe du nouveau menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans **l’Explorateur de solutions**, ouvrez *TopLevelMenuPackage.vsct*.

    À la fin du fichier, il existe un \<symboles > nœud qui contient plusieurs \<GuidSymbol > nœuds. Dans le nœud nommé guidTopLevelMenuPackageCmdSet, ajoutez un nouveau symbole, comme suit :

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Créer un vide \<Menus > nœud dans le \<commandes > nœud, juste avant \<groupes >. Dans le \<Menus > nœud, ajoutez un \<Menu > nœud, comme suit :

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Le `guid` et `id` valeurs du menu spécifient le jeu de commandes et dans le menu spécifique dans le jeu de commandes.

    Le `guid` et `id` valeurs du parent positionnement le menu sur la section de la barre de menus de Visual Studio qui contient les menus d’outils et compléments.

    La valeur de la `CommandName` chaîne indique que le texte doit apparaître dans l’élément de menu.

3. Dans le \<groupes > section, recherchez le \<groupe > et modifier le \<Parent > élément pour pointer vers le menu que nous venons d’ajouter :

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Cela rend la partie du groupe du nouveau menu.

::: moniker-end

4. Rechercher la `Buttons` section. Notez que le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de Package a généré un `Button` élément qui a son parent la valeur `MyMenuGroup`. Par conséquent, cette commande s’affiche dans votre menu.

## <a name="build-and-test-the-extension"></a>Générer et tester l’extension

1. Générez le projet et commencez le débogage. Une instance de l’instance expérimentale doit apparaître.

::: moniker range="vs-2017"

2. La barre de menus dans l’instance expérimentale doit contenir un **TestMenu** menu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Le **Extensions** menu dans l’instance expérimentale doit contenir un **TestMenu** menu.

::: moniker-end

3. Sur le **TestMenu** menu, cliquez sur **appeler une commande de Test**.

     Une boîte de message doit apparaître et afficher le message « Commande de test Package à l’intérieur de TopLevelMenu.TestCommand.MenuItemCallback() ».

## <a name="see-also"></a>Voir aussi

- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)