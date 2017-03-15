---
title: "Disposition des commandes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menus (Visual Studio SDK), commandes"
  - "meilleures pratiques, les commandes de menu et barre d'outils"
  - "barres d'outils (Visual Studio), meilleures pratiques"
  - "commandes de menu, meilleures pratiques"
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 35
---
# Disposition des commandes
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsque plusieurs packages VS sont ajoutés à Visual Studio, l'interface utilisateur \(IU\) peut devenir trop avec les commandes. Vous pouvez programmer votre package afin de réduire ce problème, comme suit :  
  
-   Le programme du package afin qu'il est chargé uniquement lorsqu'un utilisateur le requiert.  
  
-   Le package du programme afin que ses commandes sont affichent uniquement lorsqu'il peuvent être nécessaire dans le contexte de l'état actuel de l'environnement de développement intégré \(IDE\).  
  
## Chargement différé  
 La méthode classique utilisée pour activer le chargement différé consiste à concevoir le VSPackage afin que ses commandes sont affichés dans l'interface utilisateur, mais le package lui\-même n'est pas chargé tant qu'un utilisateur clique sur une des commandes. Pour ce faire, dans le fichier .vsct, créer des commandes qui n'ont aucun indicateur de commande.  
  
 L'exemple suivant montre la définition d'une commande de menu à partir d'un fichier .vsct. La commande est générée par le modèle de Package Visual Studio lorsque le **commande de Menu** option est sélectionnée dans le modèle.  
  
 [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
 Dans l'exemple, si le groupe parent, `MyMenuGroup`, est un enfant d'un menu de niveau supérieur tels que les **outils** menu, la commande sera visible dans ce menu, mais le package qui exécute la commande ne sera pas chargé jusqu'à ce qu'un utilisateur clique sur la commande. Toutefois, par programmation de la commande pour mettre en œuvre la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, vous pouvez activer le package à charger lorsque le menu qui contient la commande est développé en premier.  
  
 Notez que le chargement différé peut également améliorer les performances de démarrage.  
  
## Contexte actuel et la visibilité des commandes  
 Vous pouvez programmer des commandes VSPackage soient visibles ou masquées, selon l'état actuel des données VSPackage ou les actions qui sont actuellement pertinentes. Vous pouvez activer le VSPackage définir l'état de ses commandes, généralement à l'aide d'une implémentation de la <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> méthode à partir de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface, mais cela requiert le VSPackage à charger avant de pouvoir exécuter le code. Au lieu de cela, nous vous recommandons d'activer l'IDE gérer la visibilité des commandes sans charger le package. Pour ce faire, dans le fichier .vsct, associer des commandes avec un ou plusieurs contextes d'interface utilisateur spéciales. Les contextes d'interface utilisateur sont identifiés par un GUID connu comme un *GUID de contexte de commande*.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] surveille les modifications qui résultent d'actions utilisateur telles que le chargement d'un projet ou envisagez de modifier de construction. Lorsque des modifications se produisent, l'apparence de l'IDE est automatiquement modifié. Le tableau suivant présente quatre contextes principales de l'IDE modifier [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] moniteurs.  
  
|Type de contexte|Description|  
|----------------------|-----------------|  
|Type du projet actif|Pour la plupart des types de projet, cela `GUID` valeur est le même que le GUID du package VS qui implémente le projet. Toutefois, [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] projets utilisent le Type de projet `GUID` comme valeur.|  
|Fenêtre active|En règle générale, il s'agit de la dernière fenêtre de document actif qui établit le contexte actuel de l'interface utilisateur pour les combinaisons de touches. Toutefois, il peut également être une fenêtre outil qui a une table de clé de liaison qui ressemble le navigateur Web interne. Pour les fenêtres de document à plusieurs onglets tels que l'éditeur HTML chaque onglet possède un contexte de commande `GUID`.|  
|Service de langage actif|Le service de langage qui est associé au fichier qui est actuellement affiché dans un éditeur de texte.|  
|Fenêtre outil Active|Une fenêtre outil qui est ouvert et a le focus.|  
  
 Une cinquième zone majeure de contexte est l'état de l'interface utilisateur de l'IDE. Contextes d'interface utilisateur sont identifiés par le contexte de commande actif `GUID`s, comme suit :  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 Ces GUID est marquées comme active ou inactive, selon l'état actuel de l'IDE. Plusieurs contextes d'interface utilisateur peuvent être actives à la fois.  
  
### Masquage et affichage des commandes basées sur le contexte  
 Vous pouvez afficher ou masquer un package dans l'IDE sans charger le package lui\-même. Pour ce faire, définissez la commande dans le fichier .vsct du package à l'aide de la `DefaultDisabled`, `DefaultInvisible`, et `DynamicVisibility` commande indicateurs et ajouter un ou plusieurs [VisibilityItem](../../extensibility/visibilityitem-element.md) éléments à la [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) section. Lorsqu'un contexte de la commande spécifiée `GUID` devient actif, la commande est affichée sans le chargement du package.  
  
### GUID de contexte personnalisé  
 Si un contexte de la commande appropriée que GUID n'est pas déjà défini, vous pouvez définir dans votre package VS et ensuite qu'il soit actif ou inactif afin de contrôler la visibilité des commandes de la programmer. Utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service :  
  
-   Inscrivez les GUID de contexte \(en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> méthode\).  
  
-   Obtenir l'état d'un contexte `GUID` \(en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode\).  
  
-   Activer le contexte `GUID`s et désactiver \(en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> méthode\).  
  
    > [!CAUTION]
    >  Assurez\-vous que votre VSPackage n'affecte pas l'état de n'importe quel contexte existant GUID, car les autres packages VS peuvent dépendre les.  
  
## Exemple  
 L'exemple suivant d'une commande VSPackage montre la visibilité d'une commande qui est gérée par des contextes de commande sans charger le VSPackage dynamique.  
  
 La commande est définie pour être activé et affiche chaque fois qu'il existe une solution ; Autrement dit, chaque fois qu'un du contexte de commande GUID suivant est actif :  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 Dans l'exemple, notez que chaque indicateur de commande est distinct [indicateur de commande](../../extensibility/command-flag-element.md) élément.  
  
 [!CODE [DynamicVisibility#01](DynamicVisibility#01)]  
  
 Notez également que chaque contexte d'interface utilisateur doit figurer dans un distinct `VisibilityItem` élément, comme suit.  
  
 [!CODE [DynamicVisibility#02](DynamicVisibility#02)]  
  
## Voir aussi  
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routage des commandes dans les packages VS](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Ajouter dynamiquement des éléments de Menu](../../extensibility/dynamically-adding-menu-items.md)