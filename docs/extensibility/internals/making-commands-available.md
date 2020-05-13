---
title: Rendre les commandes disponibles . Microsoft Docs
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
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707336"
---
# <a name="making-commands-available"></a>Rendre les commandes disponibles

Lorsque plusieurs VSPackages sont ajoutés à Visual Studio, l’interface utilisateur (interface utilisateur) peut devenir surpeuplée avec des commandes. Vous pouvez programmer votre colis pour aider à réduire ce problème, comme suit :

- Programmez le paquet de sorte qu’il ne soit chargé que lorsqu’un utilisateur l’exige.

- Programmez le paquet de sorte que ses commandes ne soient affichées que lorsqu’elles peuvent être requises dans le contexte de l’état actuel de l’environnement de développement intégré (IDE).

## <a name="delayed-loading"></a>Chargement retardé

La façon typique d’activer le chargement retardé est de concevoir le VSPackage de sorte que ses commandes sont affichées dans l’interface utilisateur, mais le paquet lui-même n’est pas chargé jusqu’à ce qu’un utilisateur clique sur l’une des commandes. Pour ce faire, dans le fichier .vsct, créez des commandes qui n’ont pas de drapeaux de commande.

L’exemple suivant montre la définition d’une commande de menu à partir d’un fichier .vsct. C’est la commande qui est générée par le modèle de paquet de studio visuel lorsque l’option **de commande de menu** dans le modèle est sélectionnée.

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

Dans l’exemple, si `MyMenuGroup`le groupe parent, est un enfant d’un menu de haut niveau tel que le menu **Tools,** la commande sera visible sur ce menu, mais le paquet qui exécute la commande ne sera pas chargé jusqu’à ce que la commande est cliqué par un utilisateur. Toutefois, en programmant <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> la commande pour implémenter l’interface, vous pouvez activer le paquet lorsque le menu qui contient la commande est d’abord élargi.

Notez que le chargement retardé peut également améliorer les performances de démarrage.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexte actuel et visibilité des commandes

Vous pouvez programmer les commandes VSPackage pour être visibles ou cachées, selon l’état actuel des données VSPackage ou les actions qui sont actuellement pertinentes. Vous pouvez activer le VSPackage pour définir l’état de <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> ses commandes, généralement en utilisant une implémentation de la méthode à partir de l’interface, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> mais cela nécessite le VSPackage à charger avant qu’il puisse exécuter le code. Au lieu de cela, nous vous recommandons de permettre à l’IDE de gérer la visibilité des commandes sans charger le paquet. Pour ce faire, dans le fichier .vsct, associer les commandes avec un ou plusieurs contextes spéciaux d’interface utilisateur. Ces contextes d’interface utilisateur sont identifiés par un GUID connu sous le nom de *cadre de commande GUID*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]surveille les changements résultant d’actions utilisateur telles que le chargement d’un projet ou le fait de passer de l’édition au bâtiment. Lorsque des changements se produisent, l’apparence de l’IDE est automatiquement modifiée. Le tableau suivant montre quatre contextes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] majeurs de changement IDE qui surveille.

| Type de contexte | Description |
|-------------------------| - |
| Type de projet actif | Pour la plupart `GUID` des types de projets, cette valeur est la même que la GUID du VSPackage qui met en œuvre le projet. Toutefois, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] les projets `GUID` utilisent le type de projet comme valeur. |
| Fenêtre active | En règle générale, il s’agit de la dernière fenêtre de document active qui établit le contexte actuel de l’interface utilisateur pour les liaisons clés. Cependant, il pourrait également être une fenêtre d’outil qui a une table de liaison clé qui ressemble au navigateur Web interne. Pour les fenêtres de documents multi-tabbed telles que l’éditeur HTML, chaque onglet a un contexte `GUID`de commande différent . |
| Service linguistique actif | Le service linguistique qui est associé au fichier qui est actuellement affiché dans un éditeur de texte. |
| Fenêtre d’outil active | Une fenêtre d’outils qui est ouverte et a la concentration. |

Un cinquième domaine de contexte majeur est l’état de l’assurance-chômage de l’IDE. Les contextes de l’interface `GUID`utilisateur sont identifiés par le contexte de commande actif, comme suit :

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

Ces GUID sont marqués comme actifs ou inactifs, selon l’état actuel de l’IDE. Plusieurs contextes d’interface utilisateur peuvent être actifs en même temps.

### <a name="hide-and-display-commands-based-on-context"></a>Masquer et afficher les commandes en fonction du contexte

Vous pouvez afficher ou masquer une commande de paquet dans l’IDE sans charger le paquet lui-même. Pour ce faire, définissez la commande dans le fichier `DefaultDisabled` `DefaultInvisible`.vsct du paquet en utilisant les drapeaux , et `DynamicVisibility` de commande et en ajoutant un ou plusieurs éléments [VisibilityItem](../../extensibility/visibilityitem-element.md) à la section [VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md) Lorsqu’un contexte `GUID` de commande spécifié devient actif, la commande s’affiche sans charger le paquet.

### <a name="custom-context-guids"></a>GUIDs contexte personnalisé

Si un contexte de commande approprié GUID n’est pas déjà défini, vous pouvez en définir un dans votre VSPackage, puis le programmer pour être actif ou inactif au besoin pour contrôler la visibilité de vos commandes. Utilisez <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> le service pour :

- Enregistrer les GUIDs contextuelles (en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> méthode).

- Obtenez l’état `GUID` d’un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> contexte (en appelant la méthode).

- Allumez `GUID`et éteignez <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> le contexte (en appelant la méthode).

    > [!CAUTION]
    > Assurez-vous que votre VSPackage n’affecte pas l’état de tout contexte existant GUID parce que d’autres VSPackages peuvent en dépendre.

## <a name="example"></a>Exemple

L’exemple suivant d’une commande VSPackage démontre la visibilité dynamique d’une commande gérée par des contextes de commande sans charger le VSPackage.

La commande est définie pour être activée et affichée chaque fois qu’une solution existe ; c’est-à-dire chaque fois que l’un des GUIDs de commandement suivants est actif :

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Dans l’exemple, notez que chaque drapeau de commande est un élément distinct [du drapeau de commandement.](../../extensibility/command-flag-element.md)

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

Notez également que chaque contexte d’assurance-chômage doit être donné dans un élément distinct, `VisibilityItem` comme suit.

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

- [Ajouter une commande à la barre d’outils Solution Explorer](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routage des commandes dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Ajout dynamique d’éléments de menu](../../extensibility/dynamically-adding-menu-items.md)
