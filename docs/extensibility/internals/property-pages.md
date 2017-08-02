---
title: "Pages de propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "options de configuration, modification des propriétés"
  - "pages de propriétés"
  - "pages de propriétés, modifier les options de configuration"
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Pages de propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les utilisateurs peuvent afficher et modifier le projet selon la configuration et \- les propriétés indépendantes l'aide de pages de propriétés.  Un bouton de **Pages de propriétés** est activé dans la fenêtre de **Propriétés** ou dans la barre d'outils de l'explorateur de solutions pour les objets qui fournissent une vue de la page de propriétés de l'objet sélectionné.  Les pages de propriétés sont créées par l'environnement et sont disponibles pour des solutions et des projets.  Ils peuvent, toutefois, également être rendu disponible pour les éléments de projet qui utilisent des propriétés de configuration.  Cette fonction peut être utilisée lorsque les fichiers dans un projet requièrent plusieurs paramètres de commutateur de compilation pour générer correctement.  
  
## Utilisation des pages de propriétés  
 Si une page de propriétés est déjà affichée et les modifications de sélection \(par exemple, d'une solution à un projet\), les informations affichées dans les pages sont modifiés pour afficher les propriétés de la nouvelle sélection.  S'il n'y a aucune propriété de l'objet qui prennent en charge les pages de propriétés, la page de propriétés est vide.  
  
 Si plusieurs objets sont sélectionnés, la page de propriétés affiche l'intersection des propriétés pour toutes les options sélectionnées.  Si l'élément sélectionné ne contient pas les propriétés de configuration et le bouton de **Pages de propriétés** dans la barre d'outils de l'explorateur de solutions est activé, le focus est modifié dans la fenêtre Propriétés.  Pour plus d'informations sur la fenêtre Propriétés et la sélection, consultez [Étendre les propriétés](../../extensibility/internals/extending-properties.md).  
  
 Si les propriétés sont affichées pour plusieurs objets et vous modifiez une valeur dans une page de propriétés, toutes les valeurs pour les objets sont définis avec la nouvelle valeur même si elles étaient initialement différentes et la page était l'espace lorsque différentes propriétés de l'objet était restitué.  
  
 Il existe deux types généraux de boîtes de dialogue de **ProjetPages de propriétés** disponibles dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Dans le premier, pour les projets Visual Basic, par exemple, les pages de propriétés sont affichées en utilisant un format de champ, comme indiqué dans la capture d'écran suivante.  Dans la deuxième, indiqué plus loin dans cette section, la page de propriétés héberge une grille de propriétés similaire à celle située dans la fenêtre Propriétés.  
  
 ![Pages de propriétés Visual Basic](~/extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Boîte de dialogue pages de propriétés du projet au format et l'arborescence de champ  
  
 L'arborescence dans la boîte de dialogue pages de propriétés n'est pas générée à <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.  L'environnement, selon le nom de niveau passé par <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> et les interfaces d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> , le génère l'erreur.  
  
 Il n'existe que deux catégories de niveau supérieur disponibles sur les pages de propriétés de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :  
  
-   Propriétés communes, qui affiche des informations pas liées de l'objet ou les objets sélectionnés.  En conséquence, lorsque l'un des sous\-catégories des propriétés communes est sélectionné, les options de configuration, de plateforme, et du gestionnaire de configurations entre le haut de la boîte de dialogue sont pas disponibles.  
  
-   Propriétés de configuration, qui contient les informations dépendantes de la configuration concernant les paramètres de débogage, d'optimisation, et de génération de la solution ou le projet.  
  
 Vous ne pouvez créer des catégories de niveau supérieur supplémentaires, mais vous pouvez choisir de ne pas afficher un ou l'autre dans votre implémentation d' `IVsPropertyPage`.  Si, par exemple, vous n'avez aucune propriété configuration\-indépendante à afficher pour un objet, vous pouvez choisir de ne pas afficher la catégorie de propriétés communes.  Vous affichez les propriétés communes si `ISpecifyPropertyPages` est implémenté de l'élément parcourent l'objet et les propriétés de configuration lorsque vous implémentez `ISpecifyPropertyPages` dans l'objet de configuration \(objet qui implémente `IVsCfg`, `IVsProjectCfg`, et les interfaces connexes\).  
  
 chaque catégorie affichée sous une catégorie de niveau supérieur représente une page de propriétés distincte.  Les entrées de catégorie et de sous\-catégorie disponibles dans la boîte de dialogue sont déterminées par votre implémentation d' `ISpecifyPropertyPages` et d' `IVsPropertyPage`.  
  
 les objets d'`IDispatch` pour les éléments du conteneur de sélection qui ont des propriétés à afficher dans les pages de propriétés implémentent `ISpecifyPropertyPages` pour énumérer une liste des ID de classe.  Les ID de classe sont passés en tant que variables à `ISpecifyPropertyPages` et sont utilisés pour instancier les pages de propriétés.  La liste des ID de classe est également passé à `IVsPropertyPage` pour créer l'arborescence le à gauche de la boîte de dialogue.  Les pages de propriétés passent ensuite les informations vers l'objet d' `IDispatch` qui implémente `ISpecifyPropertyPages` et fournit les informations pour chaque page.  
  
 Les propriétés de l'objet de parcourir sont récupérées à l'aide de `IDispatch` pour chaque objet dans le conteneur de sélection.  
  
 Implémenter `Help::DisplayTopicFromF1Keyword` dans votre VSPackage fournit les fonctionnalités pour le bouton d'aide.  
  
 Pour plus d'informations, consultez `IDispatch` et l' `ISpecifyPropertyPages`dans MSDN Library.  
  
 Le second type de pages de propriétés affichées dans les exemples héberge un formulaire de la grille des propriétés, comme indiqué dans la capture d'écran suivante.  
  
 ![Pages de propriétés VC](~/extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
Boîte de dialogue pages de propriétés avec la grille des propriétés  
  
 les interfaces `IVSMDPropertyBrowser` et `IVSMDPropertyGrid` \(déclarés dans vsmanaged.h\) sont utilisées pour créer et remplir la grille des propriétés dans une boîte de dialogue ou une fenêtre.  
  
 L'architecture des projets a changé considérablement les versions précédentes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  En particulier, la notion dont le projet est actif a changé.  Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], aucun concept d'un projet actif.  Dans les environnements de développement précédents, le projet actif était le projet qui génère et de déployer des commandes auraient par défaut indépendamment du contexte.  Maintenant, la solution contrôle et arbitre qui génèrent et de déployer des commandes s'appliquent à quels projets.  
  
 Ce qui était précédemment un projet actif est maintenant capturé de trois façons différentes :  
  
-   Le projet de démarrage  
  
     Vous pouvez spécifier un projet ou des projets de la page de propriétés de la solution qui sera lancée lorsque l'utilisateur appuie sur F5 ou sélectionne le passage du menu de génération.  Cela fonctionne de manière semblable au projet actif ancien dans le sens que son nom est affiché dans l'explorateur de solutions avec la police de caractère grasse.  
  
     Vous pouvez extraire le projet de démarrage en tant que propriété dans le modèle Automation en appelant `DTE.Solution.SolutionBuild.StartupProjects`.  dans un VSPackage, vous appelez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> ou les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> .  `IVsSolutionBuildManager` est disponible en tant que service par `QueryService` sur SID\_SVsSolutionBuildManager.  Pour plus d'informations, consultez [Objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md) et [Configuration de la solution](../../extensibility/internals/solution-configuration.md).  
  
-   Configuration de build de solution active  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possède une configuration de solution active, disponible dans le modèle Automation en implémentant `DTE.Solution.SolutionBuild.ActiveConfiguration`.  Une configuration de solution est une collection qui contient une configuration de projet pour chaque projet dans la solution \(chaque projet peut avoir plusieurs configurations, sur plusieurs plateformes, avec des noms différents\).  Pour plus d'informations sur les pages de propriétés de la solution, consultez [Configuration de la solution](../../extensibility/internals/solution-configuration.md).  
  
-   projet actuellement sélectionné  
  
     Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> pour récupérer la hiérarchie de projet et l'élément de projet ou les éléments sélectionnés.  DTE, vous devez utiliser les méthodes d' `SelectedItems.SelectedItem.Project` et d' `SelectedItems.SelectedItem.ProjectItem` .  Il existe exemple de code dans ces titres dans des documents de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)