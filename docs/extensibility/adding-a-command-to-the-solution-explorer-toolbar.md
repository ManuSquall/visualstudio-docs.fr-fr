---
title: Ajout d’une commande à la barre d’outils Solution Explorer (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740332"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Ajouter une commande à la barre d’outils Solution Explorer
Ce pas-à-porter montre comment ajouter un bouton à la barre d’outils **Solution Explorer.**

 Toute commande sur une barre d’outils ou un menu est appelée un bouton dans Visual Studio. Lorsque le bouton est cliqué, le code du gestionnaire de commande est exécuté. En règle générale, les commandes connexes sont regroupées pour former un seul groupe. Les menus ou les barres d’outils servent de conteneurs pour les groupes. La priorité détermine l’ordre dans lequel les commandes individuelles d’un groupe apparaissent dans le menu ou sur la barre d’outils. Vous pouvez empêcher qu’un bouton ne s’affiche sur la barre d’outils ou le menu en contrôlant sa visibilité. Une commande qui est `<VisibilityConstraints>` répertoriée dans une section du fichier *.vsct* n’apparaît que dans le contexte associé. La visibilité ne peut pas être appliquée aux groupes.

 Pour plus d’informations sur les menus, les commandes de barres d’outils et les fichiers *.vsct,* voir [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Utilisez les fichiers XML Command Table (*.vsct*) au lieu de la configuration de la table de commande *(.ctc)* pour définir comment les menus et les commandes apparaissent dans vos VSPackages. Pour plus d’informations, voir [Visual Studio Command Table (. Vsct) fichiers](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Créer une extension avec une commande de menu
 Créer un projet `SolutionToolbar`VSIX nommé . Ajoutez un modèle d’élément de commande de menu nommé **ToolbarButton**. Pour plus d’informations sur la façon de le faire, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Ajoutez un bouton à la barre d’outils Solution Explorer
 Cette section de la procédure pas à pas montre comment ajouter un bouton à la barre d’outils **Solution Explorer.** Lorsque le bouton est cliqué, le code de la méthode de rappel est exécuté.

1. Dans le fichier *ToolbarButtonPackage.vsct,* rendez-vous à la `<Symbols>` section. Le `<GuidSymbol>` nœud contient le groupe de menu et la commande qui a été générée par le modèle de paquet. Ajoutez `<IDSymbol>` un élément à ce nœud pour déclarer le groupe qui tiendra votre commande.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. Dans `<Groups>` la section, après l’entrée de groupe existante, définissez le nouveau groupe que vous avez déclaré dans l’étape précédente.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     La configuration de la paire `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` GUID: ID parente et met ce groupe sur la barre d’outils **Solution Explorer,** et la fixation d’une valeur hautement prioritaire le met après les autres groupes de commande.

3. Dans `<Buttons>` la section, modifiez la `<Button>` pièce d’identité parente de l’entrée générée pour refléter le groupe que vous avez défini dans l’étape précédente. L’élément modifié `<Button>` devrait ressembler à ceci :

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

     La **barre d’outils Solution Explorer** doit afficher le nouveau bouton de commande à droite des boutons existants. L’icône du bouton est la strikethrough.

5. Cliquez sur le nouveau bouton.

     Une boîte de dialogue qui a le message **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback()** doit être affichée.

## <a name="control-the-visibility-of-a-button"></a>Contrôler la visibilité d’un bouton
 Cette section de la procédure pas à pas montre comment contrôler la visibilité d’un bouton sur une barre d’outils. En définissant un contexte à `<VisibilityConstraints>` un ou plusieurs projets dans la section du fichier *SolutionToolbar.vsct,* vous limitez un bouton à apparaître uniquement lorsqu’un projet ou un projet est ouvert.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Pour afficher un bouton lorsqu’un ou plusieurs projets sont ouverts

1. Dans `<Buttons>` la section de *ToolbarButtonPackage.vsct*, ajoutez `<Button>` deux drapeaux `<Strings>` `<Icons>` de commande à l’élément existant, entre les étiquettes et les étiquettes.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Les `DefaultInvisible` `DynamicVisibility` drapeaux et les drapeaux doivent `<VisibilityConstraints>` être définis afin que les entrées de la section puissent entrer en vigueur.

2. Créez `<VisibilityConstraints>` une section `<VisibilityItem>` qui comporte deux entrées. Placez la nouvelle section `</Commands>` juste après l’étiquette de clôture.

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

    Chaque élément de visibilité représente une condition dans laquelle le bouton spécifié est affiché. Pour appliquer plusieurs conditions, vous devez créer plusieurs entrées pour le même bouton.

3. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

    La barre d’outils **Solution Explorer** ne contient pas le bouton strikethrough.

4. Ouvrez toute solution contenant un projet.

    Le bouton strikethrough apparaît sur la barre d’outils à droite des boutons existants.

5. Dans le menu **Fichier** , cliquez sur **Fermer la solution**. Le bouton disparaît de la barre d’outils.

   La visibilité du bouton est [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contrôlée jusqu’à ce que le VSPackage soit chargé. Une fois le VSPackage chargé, la visibilité du bouton est contrôlée par le VSPackage.  Pour plus d’informations, voir [MenuCommands vs OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
