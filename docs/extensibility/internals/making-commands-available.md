---
title: Rendre les commandes disponibles | Microsoft Docs
description: Découvrez comment contrôler la disponibilité des commandes ajoutées à l’IDE de Visual Studio dans les VSPackages, en utilisant le chargement différé, le contexte et la visibilité.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d17fd0b63438183b10b1ecb0e5eb6abb9f5d7f46
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204536"
---
# <a name="making-commands-available"></a>Rendre les commandes disponibles

Lorsque plusieurs VSPackages sont ajoutés à Visual Studio, l’interface utilisateur (IU) peut être surmunie de commandes. Vous pouvez programmer votre package pour éviter ce problème, comme suit :

- Programmer le package afin qu’il soit chargé uniquement lorsqu’un utilisateur en a besoin.

- Programmez le package de sorte que ses commandes s’affichent uniquement lorsqu’elles peuvent être requises dans le contexte de l’état actuel de l’environnement de développement intégré (IDE).

## <a name="delayed-loading"></a>Chargement différé

La méthode habituelle pour activer le chargement différé consiste à concevoir le VSPackage afin que ses commandes soient affichées dans l’interface utilisateur, mais le package lui-même n’est pas chargé tant qu’un utilisateur n’a pas cliqué sur l’une des commandes. Pour ce faire, dans le fichier. vsct, créez des commandes qui n’ont pas d’indicateur de commande.

L’exemple suivant illustre la définition d’une commande de menu à partir d’un fichier. vsct. Il s’agit de la commande générée par le modèle de package Visual Studio lorsque l’option de **commande de menu** dans le modèle est sélectionnée.

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

Dans l’exemple, si le groupe parent, `MyMenuGroup` , est un enfant d’un menu de niveau supérieur tel que le menu **Outils** , la commande est visible dans ce menu, mais le package qui exécute la commande n’est pas chargé tant que l’utilisateur n’a pas cliqué sur la commande. Toutefois, en programmant la commande permettant d’implémenter l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, vous pouvez activer le chargement du package lorsque le menu qui contient la commande est développé pour la première fois.

Notez que le chargement différé peut également améliorer les performances de démarrage.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexte actuel et visibilité des commandes

Vous pouvez programmer des commandes VSPackage pour qu’elles soient visibles ou masquées, en fonction de l’état actuel des données du VSPackage ou des actions qui sont actuellement pertinentes. Vous pouvez activer le VSPackage pour définir l’état de ses commandes, en général à l’aide d’une implémentation de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> méthode à partir de l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, mais cela nécessite le chargement du VSPackage avant de pouvoir exécuter le code. Au lieu de cela, nous vous recommandons d’activer l’IDE pour gérer la visibilité des commandes sans charger le package. Pour ce faire, dans le fichier. vsct, associez les commandes à un ou plusieurs contextes d’interface utilisateur spéciaux. Ces contextes d’interface utilisateur sont identifiés par un GUID appelé *GUID de contexte de commande*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] surveille les modifications qui résultent des actions de l’utilisateur, telles que le chargement d’un projet ou le passage de la modification à la génération. À mesure que des modifications se produisent, l’apparence de l’IDE est automatiquement modifiée. Le tableau suivant présente les quatre contextes principaux de la modification de l’IDE que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] surveille.

| Type de contexte | Description |
|-------------------------| - |
| Type de projet actif | Pour la plupart des types de projets, cette `GUID` valeur est la même que celle du GUID du VSPackage qui implémente le projet. Toutefois, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] les projets utilisent le type de projet `GUID` comme valeur. |
| Fenêtre active | En règle générale, il s’agit de la dernière fenêtre de document active qui établit le contexte d’interface utilisateur actuel pour les combinaisons de touches. Toutefois, il peut également s’agir d’une fenêtre outil qui a une table de combinaisons de touches qui ressemble au navigateur Web interne. Pour les fenêtres de document à plusieurs onglets telles que l’éditeur HTML, chaque onglet possède un contexte de commande différent `GUID` . |
| Service de langage actif | Service de langage associé au fichier qui est actuellement affiché dans un éditeur de texte. |
| Fenêtre outil Active | Fenêtre outil qui est ouverte et a le focus. |

La cinquième zone de contexte majeure est l’état de l’interface utilisateur de l’IDE. Les contextes d’interface utilisateur sont identifiés par les s du contexte de commande actif `GUID` , comme suit :

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Ces GUID sont marqués comme actifs ou inactifs, en fonction de l’état actuel de l’environnement de développement intégré (IDE). Plusieurs contextes d’interface utilisateur peuvent être actifs en même temps.

### <a name="hide-and-display-commands-based-on-context"></a>Masquer et afficher les commandes en fonction du contexte

Vous pouvez afficher ou masquer une commande de package dans l’IDE sans charger le package lui-même. Pour ce faire, définissez la commande dans le fichier. vsct du package à l’aide des `DefaultDisabled` `DefaultInvisible` indicateurs de commande, et, `DynamicVisibility` puis ajoutez un ou plusieurs éléments [VisibilityItem](../../extensibility/visibilityitem-element.md) à la section [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) . Quand un contexte de commande spécifié `GUID` devient actif, la commande s’affiche sans charger le package.

### <a name="custom-context-guids"></a>GUID de contexte personnalisé

Si aucun GUID de contexte de commande approprié n’est déjà défini, vous pouvez en définir un dans votre VSPackage, puis le programmer pour qu’il soit actif ou inactif en fonction des besoins afin de contrôler la visibilité de vos commandes. Utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service pour :

- Inscrire des GUID de contexte (en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> méthode).

- Obtenir l’état d’un contexte `GUID` (en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode).

- Activez ou `GUID` désactivez le contexte (en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> méthode).

    > [!CAUTION]
    > Assurez-vous que votre VSPackage n’affecte pas l’état d’un GUID de contexte existant, car d’autres VSPackages peuvent en dépendre.

## <a name="example"></a> Exemple

L’exemple suivant d’une commande VSPackage illustre la visibilité dynamique d’une commande qui est gérée par des contextes de commande sans charger le VSPackage.

La commande est configurée pour être activée et affichée chaque fois qu’une solution existe ; autrement dit, chaque fois que l’un des GUID de contexte de commande suivants est actif :

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Dans l’exemple, Notez que chaque indicateur de commande est un élément d' [indicateur de commande](../../extensibility/command-flag-element.md) distinct.

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

Notez également que tous les contextes d’interface utilisateur doivent être fournis dans un `VisibilityItem` élément distinct, comme suit.

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

- [Ajouter une commande à la barre d’outils Explorateur de solutions](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routage des commandes dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Ajout dynamique d’éléments de menu](../../extensibility/dynamically-adding-menu-items.md)
