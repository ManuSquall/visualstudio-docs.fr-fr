---
title: Pages de propriété (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706059"
---
# <a name="property-pages"></a>Pages de propriétés
Les utilisateurs peuvent afficher et modifier les propriétés dépendantes de la configuration du projet et indépendantes à l’aide de pages de propriété. Un bouton **Pages de propriété** est activé dans la fenêtre **Propriété** ou sur la barre d’outils Solution Explorer pour les objets qui fournissent une vue de page de propriété de l’objet sélectionné. Les pages de propriété sont créées par l’environnement et sont disponibles pour des solutions et des projets. Ils peuvent cependant également être mis à disposition pour les éléments du projet qui font usage de propriétés dépendantes de la configuration. Cette capacité peut être utilisée lorsque les fichiers d’un projet nécessitent différents paramètres de compilateur de commutateur pour construire correctement.

## <a name="using-property-pages"></a>Utilisation des pages de propriété
 Si une page de propriété est déjà affichée et que la sélection change (par exemple, d’une solution à un projet), les informations affichées dans les pages changent pour afficher les propriétés de la nouvelle sélection. S’il n’y a pas de propriétés sur l’objet qui prennent en charge les pages de propriété, la page de propriété est vide.

 Si plusieurs objets sont sélectionnés, la page de propriété affiche l’intersection des propriétés pour tous les éléments sélectionnés. Si l’élément sélectionné ne contient pas de propriétés dépendantes de la configuration et que le bouton **Pages de propriété** sur la barre d’outils Solution Explorer est cliqué, concentrez-vous sur la fenêtre Propriétés. Pour plus d’informations relatives à la fenêtre et la sélection des propriétés, voir [Extending Properties](../../extensibility/internals/extending-properties.md).

 Si les propriétés sont affichées pour plusieurs objets et que vous modifiez une valeur sur une page de propriété, toutes les valeurs des objets sont définies à la nouvelle valeur même si elles étaient initialement différentes et que la page était vide lorsque les propriétés d’un objet individuel étaient affichées.

 Il existe deux types généraux de boîtes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dialogue **ProjectProperty Pages** disponibles dans . Dans le premier, pour les projets Visual Basic, par exemple, les pages de propriété sont affichées à l’aide d’un format de champ, comme indiqué dans la capture d’écran suivante. Dans la seconde, montrée plus tard dans cette section, la page de propriété héberge une grille de propriétés semblable à celle trouvée dans la fenêtre des propriétés.

 ![Pages de propriété de base visuelle](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Boîte de dialogue project Property Pages avec format champ et structure d’arbre

 La structure de l’arbre dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>boîte de dialogue des pages de propriété n’est pas construite en utilisant . L’environnement, basé sur le nom <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> niveau qui lui est transmis par les interfaces et les interfaces, le construit.

 Il n’y a que deux [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] catégories de haut niveau disponibles sur les pages de propriété :

- Propriétés communes, qui affiche des informations indépendantes de configuration pour l’objet ou les objets sélectionnés. Par conséquent, lorsque l’une des sous-catégories Common Properties est sélectionnée, les options Configuration, Plate-forme et Gestionnaire de configuration en haut de la boîte de dialogue ne sont pas disponibles.

- Configuration Properties, qui contient des informations dépendantes de la configuration relatives aux paramètres Debugging, Optimization et Build pour la solution ou le projet.

  Vous ne pouvez pas créer d’autres catégories de haut niveau, mais `IVsPropertyPage`vous pouvez choisir de ne pas afficher l’une ou l’autre dans votre implémentation de . Si, par exemple, vous n’avez pas de propriétés indépendantes de configuration à afficher pour un objet, vous pouvez choisir de ne pas afficher la catégorie Propriétés communes. Vous affichez `ISpecifyPropertyPages` les propriétés communes si elle est implémentée à partir de l’objet de navigation de l’élément et des propriétés configuration lorsque vous implémentez `ISpecifyPropertyPages` dans l’objet de configuration (l’objet implémentant, `IVsCfg` `IVsProjectCfg`et les interfaces connexes).

  Chaque catégorie affichée dans une catégorie de haut niveau représente une page de propriété distincte. Catégorie et sous-catégorie entrées disponibles dans la boîte `ISpecifyPropertyPages` de `IVsPropertyPage`dialogue sont déterminées par votre mise en œuvre et .

  `IDispatch`objets pour les articles dans le conteneur de sélection `ISpecifyPropertyPages` qui ont des propriétés à afficher sur les pages de propriété implémenter une liste d’ID de classe. Les UDI de classe sont `ISpecifyPropertyPages` transmises comme variables et sont utilisées pour instantanér les pages de propriété. La liste des cartes d’été `IVsPropertyPage` de classe est également transmise pour créer la structure de l’arbre à gauche de la boîte de dialogue. Les pages de propriété transmettent `IDispatch` ensuite les `ISpecifyPropertyPages` informations à l’objet qui implémente et remplit les informations pour chaque page.

  Les propriétés de l’objet `IDispatch` de navigation sont récupérées à l’aide de chaque objet dans le conteneur de sélection.

  La `Help::DisplayTopicFromF1Keyword` mise en œuvre de votre VSPackage fournit la fonctionnalité pour le bouton Aide.

  Pour plus d’informations, voir `IDispatch` et `ISpecifyPropertyPages`dans la bibliothèque MSDN.

  Le deuxième type de pages de propriété affichées dans les échantillons héberge une forme de grille de propriétés, comme indiqué dans la capture d’écran suivante.

  ![Pages de propriété de VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Boîte de dialogue de pages de propriété avec grille de propriétés

  Les `IVSMDPropertyBrowser` interfaces `IVSMDPropertyGrid` et (déclaré en vsmanaged.h) sont utilisés pour créer et peupler la grille des propriétés dans une boîte de dialogue ou une fenêtre.

  L’architecture des projets a considérablement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]changé par le passé versions de . En particulier, la notion de projet actif a changé. En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], il n’y a pas de concept d’un projet actif. Dans les environnements de développement antérieurs, le projet actif était le projet qui construisait et déploierait des commandes par défaut, quel que soit le contexte. Maintenant, les contrôles de solution et les arbitrages qui construisent et déploient des commandes s’appliquent aux projets.

  Ce qui était auparavant un projet actif est maintenant capturé de l’une des trois façons différentes :

- Le projet Startup

   Vous pouvez spécifier un projet ou des projets à partir de la page de propriété de la solution qui sera commencé lorsque l’utilisateur appuie F5 ou sélectionne Run à partir du menu Build. Cela fonctionne d’une manière similaire à l’ancien projet actif dans le sens où son nom est affiché dans Solution Explorer avec une police audacieuse.

   Vous pouvez récupérer le projet de démarrage comme `DTE.Solution.SolutionBuild.StartupProjects`une propriété dans le modèle d’automatisation en appelant . Dans un VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> vous <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> appelez les méthodes ou les méthodes. `IVsSolutionBuildManager`est disponible en `QueryService` service sur SID_SVsSolutionBuildManager. Pour plus d’informations, voir [Project Configuration Object](../../extensibility/internals/project-configuration-object.md) and Solution [Configuration](../../extensibility/internals/solution-configuration.md).

- Configuration active de construction de solutions

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]a une configuration de solution active, disponible `DTE.Solution.SolutionBuild.ActiveConfiguration`dans le modèle d’automatisation par la mise en œuvre . Une configuration de solution est une collection qui contient une configuration de projet pour chaque projet dans la solution (chaque projet peut avoir plusieurs configurations, sur plusieurs plates-formes, avec des noms différents). Pour plus d’informations sur les pages de propriété de la solution, voir [Solution Configuration](../../extensibility/internals/solution-configuration.md).

- Projet actuellement sélectionné

   Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> méthode pour récupérer la hiérarchie du projet et l’élément du projet ou les éléments sélectionnés. De DTE, vous `SelectedItems.SelectedItem.Project` utiliseriez les méthodes et `SelectedItems.SelectedItem.ProjectItem` les méthodes. Il y a un code d’échantillon sous ces rubriques dans les documents de base. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Objet de configuration de projet](../../extensibility/internals/project-configuration-object.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
