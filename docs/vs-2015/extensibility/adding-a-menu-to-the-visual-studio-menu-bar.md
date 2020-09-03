---
title: Ajout d’un menu à la barre de menus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184927"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Ajout d’un menu à la barre de menus de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment ajouter un menu à la barre de menus de l’environnement de développement intégré (IDE) de Visual Studio. La barre de menus IDE contient des catégories de menu telles que **fichier**, **Edition**, **affichage**, **fenêtre**et **aide**.

 Avant d’ajouter un nouveau menu à la barre de menus de Visual Studio, déterminez si vos commandes doivent être placées dans un menu existant. Pour plus d’informations sur l’emplacement des commandes, consultez [menus et commandes pour Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Les menus sont déclarés dans le fichier. vsct du projet. Pour plus d’informations sur les menus et les fichiers. vsct, consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

 En suivant cette procédure pas à pas, vous pouvez créer un menu nommé **TestMenu** qui contient une commande.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Création d’un projet VSIX avec un modèle d’élément de commande personnalisé

1. Créez un projet VSIX nommé `TopLevelMenu` . Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** sous extensibilité **Visual C#**  /  **Extensibility**.  Pour plus d’informations, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **test**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à **Visual C#/extensibilité** et sélectionnez **commande personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Création d’un menu dans la barre de menus de l’IDE

#### <a name="to-create-a-menu"></a>Pour créer un menu

1. Dans **Explorateur de solutions**, ouvrez TestCommandPackage. vsct.

     À la fin du fichier se trouve un \<Symbols> nœud qui contient plusieurs \<GuidSymbol> nœuds. Dans le nœud nommé guidTestCommandPackageCmdSet, ajoutez un nouveau symbole, comme suit :

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. Créez un \<Menus> nœud vide dans le \<Commands> nœud, juste avant \<Groups> . Dans le \<Menus> nœud, ajoutez un \<Menu> nœud, comme suit :

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

     Les `guid` `id` valeurs et du menu spécifient le jeu de commandes et le menu spécifique dans le jeu de commandes.

     Les `guid` `id` valeurs et du parent positionnent le menu sur la section de la barre de menus de Visual Studio qui contient les menus outils et compléments.

     La valeur de la `CommandName` chaîne indique que le texte doit s’afficher dans l’élément de menu.

3. Dans la \<Groups> section, recherchez le \<Group> et modifiez l' \<Parent> élément pour qu’il pointe vers le menu que nous venons d’ajouter :

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Cela fait de la partie groupe du nouveau menu.

4. Recherchez la section `Buttons`. Notez que le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modèle de package a généré un `Button` élément dont le parent a la valeur `MyMenuGroup` . Par conséquent, cette commande s’affiche dans votre menu.

## <a name="building-and-testing-the-extension"></a>Génération et test de l’extension

1. Générez le projet et commencez le débogage. Une instance de l’instance expérimentale doit apparaître.

2. La barre de menus de l’instance expérimentale doit contenir un menu **TestMenu** .

3. Dans le menu **TestMenu** , cliquez sur **appeler la commande de test**.

     Une boîte de message doit apparaître et afficher le message « package test dans TopLevelMenu. test. MenuItemCallback () ». Cela indique que la nouvelle commande fonctionne.

## <a name="see-also"></a>Voir aussi
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
