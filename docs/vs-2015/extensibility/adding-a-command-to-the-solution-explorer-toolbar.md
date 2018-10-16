---
title: Ajout d’une commande à la barre d’outils de l’Explorateur de solutions | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f32cc47b796ea7d32207448e7888c17a1d40a73a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254377"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Ajout d’une commande à la barre d’outils de l’Explorateur de solutions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment ajouter un bouton à la **l’Explorateur de solutions** barre d’outils.  
  
 N’importe quelle commande dans un menu ou une barre d’outils est appelée un bouton dans Visual Studio. Lorsque le bouton est activé, le code dans le Gestionnaire de commandes est exécuté. En règle générale, les commandes associées sont regroupés pour former un groupe. Menus ou barres d’outils agissent comme des conteneurs pour les groupes. Priorité détermine l’ordre dans lequel les commandes individuelles dans un groupe apparaissent dans le menu ou la barre d’outils. Vous pouvez empêcher un bouton de s’afficher sur la barre d’outils ou dans le menu en contrôlant sa visibilité. Une commande qui est répertoriée dans un `<VisibilityConstraints>` section du fichier .vsct apparaît uniquement dans le contexte associé. La visibilité ne peut pas être appliquée aux groupes.  
  
 Pour plus d’informations sur les menus, les commandes de barre d’outils et les fichiers .vsct, consultez [commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Utilisez les fichiers XML Command Table (.vsct) au lieu de fichiers de configuration (.ctc) de table de commande pour définir comment les menus et commandes apparaissent dans vos VSPackages. Pour plus d'informations, consultez [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Création d’une extension avec une commande de menu  
 Créez un projet VSIX nommé `SolutionToolbar`. Ajouter un modèle d’élément commande menu nommé **ToolbarButton**. Pour savoir comment procéder, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Ajout d’un bouton à la barre d’outils de l’Explorateur de solutions  
 Cette section de la procédure pas à pas montre comment ajouter un bouton à la **l’Explorateur de solutions** barre d’outils. Lorsque le bouton est activé, le code dans la méthode de rappel est exécuté.  
  
1.  Dans le fichier ToolbarButtonPackage.vsct, accédez à la `<Symbols>` section. Le `<GuidSymbol>` nœud contient le groupe de menus et la commande qui a été généré par le modèle de package. Ajouter un `<IDSymbol>` élément à ce nœud pour déclarer le groupe qui contiendra votre commande.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  Dans la `<Groups>` section, après l’entrée de groupe existant, définir le nouveau groupe que vous avez déclaré à l’étape précédente.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Définissant le parent paire GUID : ID `guidSHLMainMenu` et `IDM_VS_TOOL_PROJWIN` place ce groupe sur le **l’Explorateur de solutions** barre d’outils et la définition d’une valeur de priorité élevée place après les autres groupes de commandes.  
  
3.  Dans le `<Buttons>` section, modifier l’ID parent généré `<Button>` entrée afin de refléter le groupe que vous avez définie à l’étape précédente. Modifié `<Button>` élément doit ressembler à ceci :  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
     Le **l’Explorateur de solutions** barre d’outils doit afficher le nouveau bouton de commande à droite des boutons existants. L’icône du bouton est barré.  
  
5.  Cliquez sur le bouton Nouveau.  
  
     Une boîte de dialogue qui contient le message **ToolbarButtonPackage à l’intérieur de SolutionToolbar.ToolbarButton.MenuItemCallback()** doit être affiché.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Contrôle de la visibilité d’un bouton  
 Cette section de la procédure pas à pas montre comment contrôler la visibilité d’un bouton sur une barre d’outils. En définissant un contexte à un ou plusieurs projets dans la `<VisibilityConstraints>` section du fichier SolutionToolbar.vsct, vous limitez un bouton pour apparaissent uniquement lorsqu’un ou plusieurs projets sont ouverts.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Pour afficher un bouton quand un ou plusieurs projets sont ouverts  
  
1.  Dans le `<Buttons>` section de ToolbarButtonPackage.vsct, ajouter deux indicateurs de commande à le `<Button>` élément, entre le `<Strings>` et `<Icons>` balises.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     Le `DefaultInvisible` et `DynamicVisibility` indicateurs doivent être définis, ainsi que les entrées dans la `<VisibilityConstraints>` section peut entrer en vigueur.  
  
2.  Créer un `<VisibilityConstraints>` section qui comporte deux `<VisibilityItem>` entrées. Placer la nouvelle section juste après la fermeture `</Commands>` balise.  
  
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
  
3.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
     Le **l’Explorateur de solutions** barre d’outils ne contient pas le bouton Barré.  
  
4.  Ouvrez une solution qui contient un projet.  
  
     Le bouton Barré apparaît sur la barre d’outils à droite des boutons existants.  
  
5.  Sur le **fichier** menu, cliquez sur **fermer la Solution**. Le bouton disparaît de la barre d’outils.  
  
 La visibilité du bouton est contrôlée par [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jusqu'à ce que le VSPackage est chargé. Une fois le VSPackage est chargé, la visibilité du bouton est contrôlée par le VSPackage.  Pour plus d’informations, consultez [MenuCommands et. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)

