---
title: Mise à disposition commandes | Microsoft Docs
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
ms.openlocfilehash: c1292dc3879effa53f3b4a41b87374a3a5f46ff0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857131"
---
# <a name="making-commands-available"></a>Rendre les commandes disponibles
Lorsque plusieurs packages VS sont ajoutés à Visual Studio, l’interface utilisateur (IU) peut devenir trop avec les commandes. Vous pouvez programmer votre package afin de réduire ce problème, comme suit :

-   Programme du package afin qu’il est chargé uniquement lorsqu’un utilisateur en a besoin.

-   Le package du programme afin que ses commandes sont affichées uniquement quand elles peuvent être requises dans le contexte de l’état actuel de l’environnement de développement intégré (IDE).

## <a name="delayed-loading"></a>Chargement différé
 La manière classique pour activer le chargement différé consiste à concevoir le VSPackage afin que ses commandes sont affichées dans l’interface utilisateur, mais le package lui-même n’est pas chargé jusqu'à ce qu’un utilisateur clique sur une des commandes. Pour ce faire, dans le fichier .vsct, créer des commandes qui n’ont aucun indicateur de commande.

 L’exemple suivant montre la définition d’une commande de menu à partir d’un fichier .vsct. Voici la commande qui est générée par le modèle de Package Visual Studio lorsque le **commande de Menu** option est sélectionnée dans le modèle.

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

Dans l’exemple, si le groupe parent, `MyMenuGroup`, est un enfant d’un menu de niveau supérieur tels que le **outils** menu, la commande sera visible dans ce menu, mais le package qui exécute la commande ne sera pas chargé tant que l’utilisateur clique sur la commande par un utilisateur. Toutefois, par programmation de la commande pour implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, vous pouvez activer le package à charger lorsque le menu qui contient la commande est développé en premier.

Notez que le chargement différé peut également améliorer les performances de démarrage.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexte actuel et la visibilité des commandes
 Vous pouvez programmer des commandes VSPackage qui sera affiché ou masqué, selon l’état actuel des données VSPackage ou les actions qui sont actuellement pertinentes. Vous pouvez activer le VSPackage définir l’état de ses commandes, généralement à l’aide d’une implémentation de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> méthode à partir de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, mais cela requiert le VSPackage pour être chargé avant de pouvoir exécuter le code. Au lieu de cela, nous vous recommandons d’activer l’IDE gérer la visibilité des commandes sans charger le package. Pour ce faire, dans le fichier .vsct, associer des commandes à un ou plusieurs contextes d’interface utilisateur spéciales. Ces contextes d’interface utilisateur sont identifiés par un GUID connu sous le nom un *GUID de contexte de commande*.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] surveille les modifications résultant d’actions telles que le chargement d’un projet ou du passage d’édition pour la création de l’utilisateur. Comme les modifications se produisent, modifier l’apparence de l’IDE est automatiquement. Le tableau suivant présente quatre contextes principaux de IDE changer cela [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moniteurs.


| Type de contexte | Description |
|-------------------------| - |
| Type de projet actif | Pour la plupart des types de projets, cela `GUID` valeur est le même que le GUID du VSPackage qui implémente le projet. Toutefois, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projets utilisent le Type de projet `GUID` comme valeur. |
| Fenêtre active | En règle générale, il s’agit de la dernière fenêtre de document actif qui établit le contexte actuel de l’interface utilisateur pour les combinaisons de touches. Toutefois, il peut également être une fenêtre outil qui a une table de la combinaison de touches qui ressemble au navigateur Web interne. Pour les fenêtres de document à plusieurs onglets tels que l’éditeur HTML, chaque onglet possède un contexte de commande différentes `GUID`. |
| Service de langage Active | Le service de langage qui est associé au fichier qui est actuellement affiché dans un éditeur de texte. |
| Fenêtre outil Active | Une fenêtre outil qui est ouvert et a le focus. |

 Une cinquième zone majeure de contexte est l’état de l’interface utilisateur de l’IDE. Contextes d’interface utilisateur sont identifiées par le contexte de commande active `GUID`s, comme suit :

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

Ces GUID est marqués comme active ou inactive, selon l’état actuel de l’IDE. Plusieurs contextes d’interface utilisateur peuvent être actives en même temps.

### <a name="hiding-and-displaying-commands-based-on-context"></a>Masquage et affichage des commandes en fonction du contexte
 Vous pouvez afficher ou masquer une commande de package dans l’IDE sans charger le package lui-même. Pour ce faire, définissez la commande dans le fichier .vsct du package à l’aide de la `DefaultDisabled`, `DefaultInvisible`, et `DynamicVisibility` commande indicateurs et ajouter un ou plusieurs [VisibilityItem](../../extensibility/visibilityitem-element.md) éléments à la [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) section. Quand un contexte de la commande spécifiée `GUID` devient active, la commande est affichée sans le chargement du package.

### <a name="custom-context-guids"></a>GUID de contexte personnalisé
 Si un contexte de la commande appropriée que GUID n’est pas déjà défini, vous pouvez définir un dans votre package Visual Studio et programmez ensuite qu’il soit actif ou inactif, en fonction des besoins pour contrôler la visibilité de vos commandes. Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service :

-   Inscrire le GUID de contexte (en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> méthode).

-   Obtenir l’état d’un contexte `GUID` (en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode).

-   Activer le contexte `GUID`s et désactiver (en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> méthode).

    > [!CAUTION]
    > Assurez-vous que votre VSPackage n’affecte pas l’état de n’importe quel GUID de contexte existant, car d’autres packages VS dépendent les.

## <a name="example"></a>Exemple
 L’exemple suivant d’une commande VSPackage montre la visibilité dynamique d’une commande qui est gérée par les contextes de commande sans charger le VSPackage.

 La commande est définie pour être activé et affiche chaque fois qu’une solution existe ; Autrement dit, chaque fois qu’un de contexte de la commande suivante GUID est actif :

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

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
