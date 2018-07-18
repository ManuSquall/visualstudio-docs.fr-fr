---
title: Disposition des commandes | Documents Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e20fd9b1b13dfc8159181ee2cb8f5d8966f6faf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134111"
---
# <a name="making-commands-available"></a>Disposition des commandes
Lorsque plusieurs packages VS sont ajoutés à Visual Studio, l’interface utilisateur (IU) peut devenir trop avec les commandes. Vous pouvez programmer votre package afin de réduire ce problème, comme suit :

-   Le programme du package afin qu’il est chargé uniquement lorsqu’un utilisateur le requiert.

-   Le package du programme afin que ses commandes sont affichées uniquement quand ils peuvent être nécessaires dans le contexte de l’état actuel de l’environnement de développement intégré (IDE).

## <a name="delayed-loading"></a>Chargement différé
 La manière classique pour activer le chargement différé consiste à concevoir le VSPackage afin que ses commandes sont affichées dans l’interface utilisateur, mais le package lui-même n’est pas chargé tant qu’un utilisateur clique sur une des commandes. Pour ce faire, dans le fichier .vsct, créer des commandes qui n’ont aucun indicateur de commande.

 L’exemple suivant montre la définition d’une commande de menu à partir d’un fichier .vsct. Ceci est la commande qui est générée par le modèle de Package Visual Studio lorsque le **commande de Menu** option est sélectionnée dans le modèle.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>

```

 Dans l’exemple, si le groupe parent, `MyMenuGroup`, est un enfant d’un menu de niveau supérieur telles que la **outils** menu, la commande sera visible dans ce menu, mais le package qui exécute la commande ne sera pas chargé tant que l’utilisateur clique sur la commande par un utilisateur. Toutefois, par programmation la commande pour mettre en œuvre la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, vous pouvez activer le package à charger lorsque le menu qui contient la commande est développé en premier.

 Notez que le chargement différé peut également améliorer les performances de démarrage.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexte actuel et la visibilité des commandes
 Vous pouvez programmer VSPackage commandes soient visibles ou masquées, selon l’état actuel des données VSPackage ou les actions qui sont actuellement pertinentes. Vous pouvez activer le VSPackage pour définir l’état de ses commandes, généralement à l’aide d’une implémentation de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> méthode à partir de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, mais cela nécessite le VSPackage doit être chargé avant de pouvoir exécuter le code. Au lieu de cela, nous vous recommandons d’activer l’IDE gérer la visibilité des commandes sans chargement du package. Pour ce faire, dans le fichier .vsct, associer des commandes avec un ou plusieurs contextes d’interface utilisateur spéciales. Les contextes d’interface utilisateur sont identifiés par un GUID connu comme un *GUID de contexte de commande*.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] surveille les modifications qui résultent des actions telles que le chargement d’un projet ou allant de modification pour la génération de l’utilisateur. Lorsque des modifications sont apportées, modifier l’apparence de l’IDE est automatiquement. Le tableau suivant montre quatre contextes principales de l’IDE change qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moniteurs.

|Type de contexte|Description|
|---------------------|-----------------|
|Type de projet actif|Pour la plupart des types de projet, cela `GUID` valeur est le même que le GUID du VSPackage qui implémente le projet. Toutefois, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projets utilisent le Type de projet `GUID` comme valeur.|
|Fenêtre active|En règle générale, il s’agit de la dernière fenêtre de document actif qui établit le contexte actuel de l’interface utilisateur pour les combinaisons de touches. Toutefois, il peut également être une fenêtre outil qui a une table de clé de liaison qui ressemble à du navigateur Web interne. Pour les fenêtres de document d’à plusieurs onglets tels que l’éditeur HTML, chaque onglet dispose d’un contexte autre commande `GUID`.|
|Service de langage Active|Le service de langage qui est associé au fichier qui est actuellement affiché dans un éditeur de texte.|
|Fenêtre outil Active|Une fenêtre outil qui est ouvert et a le focus.|

 Une zone de contexte principales cinquième est l’état de l’interface utilisateur de l’IDE. Contextes d’interface utilisateur sont identifiés par le contexte de commande active `GUID`s, comme suit :

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

 Ces GUID est marqués comme active ou inactive, selon l’état actuel de l’IDE. Plusieurs contextes d’interface utilisateur peuvent être actives à la fois.

### <a name="hiding-and-displaying-commands-based-on-context"></a>Masquage et affichage des commandes en fonction de contexte
 Vous pouvez afficher ou masquer un package dans l’IDE sans charger le package lui-même. Pour ce faire, définissez la commande dans le fichier .vsct du package à l’aide de la `DefaultDisabled`, `DefaultInvisible`, et `DynamicVisibility` commande indicateurs et ajouter un ou plusieurs [VisibilityItem](../../extensibility/visibilityitem-element.md) éléments à la [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) section. Lorsqu’un contexte de la commande spécifiée `GUID` devient actif, la commande est affichée sans le chargement du package.

### <a name="custom-context-guids"></a>GUID de contexte personnalisé
 Si un contexte de la commande appropriée que GUID n’est pas déjà défini, vous pouvez définir un dans votre VSPackage et puis qu’il soit actif ou inactif afin de contrôler la visibilité des commandes de votre programme. Utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service :

-   Inscrivez les GUID de contexte (en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> méthode).

-   Obtenir l’état d’un contexte `GUID` (en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode).

-   Activer le contexte `GUID`s et désactiver (en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> méthode).

    > [!CAUTION]
    > Assurez-vous que votre VSPackage n’affecte pas l’état de n’importe quel contexte existant GUID, car d’autres packages VS dépendent les.

## <a name="example"></a>Exemple
 L’exemple suivant d’une commande VSPackage montre la visibilité dynamique d’une commande qui est gérée par des contextes de commande sans charger le VSPackage.

 La commande est définie pour être activé et affiche chaque fois qu’il existe une solution ; Autrement dit, chaque fois qu’un du contexte de la commande suivante GUID est actif :

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>

Dans l’exemple, notez que chaque indicateur de commande est distinct [indicateur de commande](../../extensibility/command-flag-element.md) élément.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Notez également que chaque contexte d’interface utilisateur doit figurer dans un distinct `VisibilityItem` élément, comme suit.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Voir aussi

- [MenuCommands et OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routage des commandes dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Ajout dynamique d’éléments de menu](../../extensibility/dynamically-adding-menu-items.md)