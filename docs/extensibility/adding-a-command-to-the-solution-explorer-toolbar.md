---
title: Ajout d’une commande à la barre d’outils Explorateur de solutions | Microsoft Docs
description: Découvrez comment ajouter un bouton qui exécute une commande à la barre d’outils Explorateur de solutions dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0aa75bd1a229be147e3462845a61266a650e072e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900237"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Ajouter une commande à la barre d’outils Explorateur de solutions
Cette procédure pas à pas montre comment ajouter un bouton à la barre d’outils **Explorateur de solutions** .

 Une commande dans une barre d’outils ou un menu est appelée un bouton dans Visual Studio. Lorsque l’utilisateur clique sur le bouton, le code du gestionnaire de commandes est exécuté. En règle générale, les commandes associées sont regroupées pour former un groupe. Les menus et les barres d’outils jouent le rôle de conteneurs pour les groupes. La priorité détermine l’ordre dans lequel les commandes individuelles d’un groupe apparaissent dans le menu ou dans la barre d’outils. Vous pouvez empêcher l’affichage d’un bouton dans la barre d’outils ou dans le menu en contrôlant sa visibilité. Une commande qui est listée dans une `<VisibilityConstraints>` section du fichier *. vsct* s’affiche uniquement dans le contexte associé. Impossible d’appliquer la visibilité à des groupes.

 Pour plus d’informations sur les menus, les commandes de barre d’outils et les fichiers *. vsct* , consultez [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Utilisez les fichiers de table de commandes XML (*. vsct*) à la place des fichiers de configuration de table de commandes (*. CTC*) pour définir le mode d’affichage des menus et des commandes dans vos VSPackages. Pour plus d’informations, consultez [table de commandes Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Créer une extension avec une commande de menu
 Créez un projet VSIX nommé `SolutionToolbar` . Ajoutez un modèle d’élément de commande de menu nommé **ToolBarButton**. Pour plus d’informations sur la façon de procéder, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Ajouter un bouton à la barre d’outils Explorateur de solutions
 Cette section de la procédure pas à pas montre comment ajouter un bouton à la barre d’outils **Explorateur de solutions** . Lorsque l’utilisateur clique sur le bouton, le code de la méthode de rappel est exécuté.

1. Dans le fichier *ToolbarButtonPackage. vsct* , accédez à la  `<Symbols>` section. Le `<GuidSymbol>`  nœud contient le groupe de menus et la commande qui a été généré par le modèle de package. Ajoutez un `<IDSymbol>` élément à ce nœud pour déclarer le groupe qui contiendra votre commande.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. Dans la `<Groups>` section, après l’entrée de groupe existante, définissez le nouveau groupe que vous avez déclaré à l’étape précédente.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     L’affectation de la valeur à la paire parent GUID : ID à `guidSHLMainMenu` et `IDM_VS_TOOL_PROJWIN` place ce groupe dans la barre d’outils **Explorateur de solutions** , et la définition d’une valeur de priorité élevée le place après les autres groupes de commandes.

3. Dans la `<Buttons>` section, modifiez l’ID parent de l' `<Button>` entrée générée pour refléter le groupe que vous avez défini à l’étape précédente. L' `<Button>` élément modifié doit se présenter comme suit :

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

     La barre d’outils **Explorateur de solutions** doit afficher le nouveau bouton de commande à droite des boutons existants. L’icône du bouton est le barré.

5. Cliquez sur le bouton nouveau.

     Une boîte de dialogue contenant le message **ToolbarButtonPackage dans SolutionToolbar. ToolBarButton. MenuItemCallback ()** doit s’afficher.

## <a name="control-the-visibility-of-a-button"></a>Contrôler la visibilité d’un bouton
 Cette section de la procédure pas à pas montre comment contrôler la visibilité d’un bouton sur une barre d’outils. En définissant un contexte sur un ou plusieurs projets de la `<VisibilityConstraints>` section du fichier *SolutionToolbar. vsct* , vous limitez l’affichage d’un bouton uniquement lorsqu’un projet ou des projets sont ouverts.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Pour afficher un bouton lorsqu’un ou plusieurs projets sont ouverts

1. Dans la `<Buttons>` section de *ToolbarButtonPackage. vsct*, ajoutez deux indicateurs de commande à l' `<Button>` élément existant, entre `<Strings>` les `<Icons>` balises et.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Les `DefaultInvisible` `DynamicVisibility` indicateurs et doivent être définis afin que les entrées de la `<VisibilityConstraints>` section puissent prendre effet.

2. Créez une `<VisibilityConstraints>` section qui a deux `<VisibilityItem>` entrées. Placez la nouvelle section juste après la `</Commands>` balise de fermeture.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    Chaque élément de visibilité représente une condition sous laquelle le bouton spécifié est affiché. Pour appliquer plusieurs conditions, vous devez créer plusieurs entrées pour le même bouton.

3. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

    La barre d’outils **Explorateur de solutions** ne contient pas le bouton barré.

4. Ouvrez une solution qui contient un projet.

    Le bouton barré apparaît dans la barre d’outils à droite des boutons existants.

5. Dans le menu **Fichier** , cliquez sur **Fermer la solution**. Le bouton disparaît de la barre d’outils.

   La visibilité du bouton est contrôlée par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jusqu’au chargement du VSPackage. Une fois le VSPackage chargé, la visibilité du bouton est contrôlée par le VSPackage.  Pour plus d’informations, consultez [MenuCommands et OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)