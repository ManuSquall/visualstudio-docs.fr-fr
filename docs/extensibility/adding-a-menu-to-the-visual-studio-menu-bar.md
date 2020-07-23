---
title: Ajout d’un menu à la barre de menus de Visual Studio | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61321555a6896fad926d2ee38c5d73d50801d6b9
ms.sourcegitcommit: cb0c6e55ae560960a493df9ab56e3e9d9bc50100
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972346"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Ajouter un menu à la barre de menus de Visual Studio

Cette procédure pas à pas montre comment ajouter un menu à la barre de menus de l’environnement de développement intégré (IDE) de Visual Studio. La barre de menus IDE contient des catégories de menu telles que **fichier**, **Edition**, **affichage**, **fenêtre**et **aide**.

Avant d’ajouter un nouveau menu à la barre de menus de Visual Studio, déterminez si vos commandes doivent être placées dans un menu existant. Pour plus d’informations sur l’emplacement des commandes, consultez [menus et commandes pour Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Les menus sont déclarés dans le fichier *. vsct* du projet. Pour plus d’informations sur les menus et les fichiers *. vsct* , consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

En suivant cette procédure pas à pas, vous pouvez créer un menu nommé **test** qui contient une commande.

:::moniker range=">=vs-2019"
> [!NOTE]
> À compter de Visual Studio 2019, les menus de niveau supérieur fournis par les extensions sont placés dans le menu **Extensions** .
:::moniker-end

## <a name="prerequisites"></a>Prérequis

À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Créer un projet VSIX avec un modèle d’élément de commande personnalisé

1. Créez un projet VSIX nommé `TopLevelMenu` . Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** en recherchant « VSIX ».  Pour plus d’informations, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

::: moniker range="vs-2017"

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **test**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >   **un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à **Visual C#/extensibilité** et sélectionnez **commande personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par *TestCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **test**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >   **un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à **Visual C#/extensibilité** et sélectionnez **commande**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par *TestCommand.cs*.

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Créer un menu dans la barre de menus de l’IDE

::: moniker range="vs-2017"

1. Dans **Explorateur de solutions**, ouvrez *TestCommandPackage. vsct*.

    À la fin du fichier se trouve un `<Symbols>` nœud qui contient plusieurs `<GuidSymbol>` nœuds. Dans le nœud nommé `guidTestCommandPackageCmdSet` , ajoutez un nouveau symbole, comme suit :

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Créez un `<Menus>` nœud vide dans le `<Commands>` nœud, juste avant `<Groups>` . Dans le `<Menus>` nœud, ajoutez un `<Menu>` nœud, comme suit :

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    Les `guid` `id` valeurs et du menu spécifient le jeu de commandes et le menu spécifique dans le jeu de commandes.

    Les `guid` `id` valeurs et du parent positionnent le menu sur la section de la barre de menus de Visual Studio qui contient les menus outils et compléments.

    L' `<ButtonText>` élément spécifie que le texte doit apparaître dans l’élément de menu.

3. Dans la `<Groups>` section, recherchez le `<Group>` et modifiez l' `<Parent>` élément pour qu’il pointe vers le menu que nous venons d’ajouter :

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Cela fait de la partie groupe du nouveau menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans **Explorateur de solutions**, ouvrez *TopLevelMenuPackage. vsct*.

    À la fin du fichier se trouve un `<Symbols>` nœud qui contient plusieurs `<GuidSymbol>` nœuds. Dans le nœud nommé `guidTopLevelMenuPackageCmdSet` , ajoutez un nouveau symbole, comme suit :

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Créez un `<Menus>` nœud vide dans le `<Commands>` nœud, juste avant `<Groups>` . Dans le `<Menus>` nœud, ajoutez un `<Menu>` nœud, comme suit :

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    Les `guid` `id` valeurs et du menu spécifient le jeu de commandes et le menu spécifique dans le jeu de commandes.

    Les `guid` `id` valeurs et du parent positionnent le menu sur la section de la barre de menus de Visual Studio qui contient les menus outils et compléments.

    L' `<ButtonText>` élément spécifie que le texte doit apparaître dans l’élément de menu.

3. Dans la `<Groups>` section, recherchez le `<Group>` et modifiez l' `<Parent>` élément pour qu’il pointe vers le menu que nous venons d’ajouter :

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Cela fait de la partie groupe du nouveau menu.

::: moniker-end

4. Dans la `<Buttons>` section, recherchez le `<Button>` nœud. Ensuite, dans le `<Strings>` nœud, remplacez l' `<ButtonText>` élément par `Test Command` .

    Notez que le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de package a généré un `Button` élément dont le parent a la valeur `MyMenuGroup` . Par conséquent, cette commande s’affiche dans votre menu.

## <a name="build-and-test-the-extension"></a>Générer et tester l’extension

1. Générez le projet et commencez le débogage. Une instance de l’instance expérimentale doit apparaître.

::: moniker range="vs-2017"

2. La barre de menus de l’instance expérimentale doit contenir un menu de **menu de test** .

::: moniker-end

::: moniker range=">=vs-2019"

2. Le menu **Extensions** de l’instance expérimentale doit contenir un menu de **menu test** .

::: moniker-end

3. Dans le menu **test** , cliquez sur **commande de test**.

    Une boîte de message doit apparaître et afficher le message « test dans TopLevelMenu. test. MenuItemCallback () ».

## <a name="see-also"></a>Voir aussi

- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
