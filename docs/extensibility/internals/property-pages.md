---
title: Pages de propriétés | Microsoft Docs
description: En savoir plus sur l’utilisation des pages de propriétés pour votre nouveau type de projet dans le kit de développement logiciel (SDK) Visual Studio, qui permet aux utilisateurs d’afficher et de modifier les propriétés d’un projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 88ebf99ef2361a232c4a5c4c02b9a140155d66e9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903409"
---
# <a name="property-pages"></a>Pages de propriétés
Les utilisateurs peuvent afficher et modifier les propriétés dépendantes et indépendantes de la configuration de projet à l’aide des pages de propriétés. Le bouton **pages de propriétés** est activé dans la fenêtre **Propriétés** ou dans la barre d’outils Explorateur de solutions pour les objets qui fournissent une vue de page de propriétés de l’objet sélectionné. Les pages de propriétés sont créées par l’environnement et sont disponibles pour les solutions et les projets. Toutefois, elles peuvent également être mises à disposition pour les éléments de projet qui utilisent des propriétés dépendantes de la configuration. Cette fonctionnalité peut être utilisée lorsque des fichiers dans un projet requièrent des paramètres de commutateur de compilateur différents pour une génération correcte.

## <a name="using-property-pages"></a>Utilisation des pages de propriétés
 Si une page de propriétés est déjà affichée et que la sélection change (par exemple, d’une solution à un projet), les informations affichées dans les pages changent pour afficher les propriétés de la nouvelle sélection. S’il n’existe aucune propriété sur l’objet qui prend en charge les pages de propriétés, la page de propriétés est vide.

 Si plusieurs objets sont sélectionnés, la page de propriétés affiche l’intersection des propriétés de tous les éléments sélectionnés. Si l’élément sélectionné ne contient pas de propriétés dépendantes de la configuration et que l’utilisateur clique sur le bouton **pages de propriétés** dans la barre d’outils Explorateur de solutions, le focus passe au fenêtre Propriétés. Pour plus d’informations sur le Fenêtre Propriétés et la sélection, consultez [extension des propriétés](../../extensibility/internals/extending-properties.md).

 Si des propriétés sont affichées pour plusieurs objets et que vous modifiez une valeur dans une page de propriétés, toutes les valeurs des objets sont définies sur la nouvelle valeur même si elles ont été initialement différentes et la page était vide lorsque les propriétés d’un objet individuel étaient affichées.

 Il existe deux types généraux de boîtes de dialogue de **pages ProjectProperty** disponibles dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Dans le premier cas, pour les projets Visual Basic, par exemple, les pages de propriétés s’affichent à l’aide d’un format de champ, comme illustré dans la capture d’écran suivante. Dans la seconde, présentée plus loin dans cette section, la page de propriétés héberge une grille de propriétés similaire à celle trouvée dans la fenêtre Propriétés.

 ![Pages de propriétés de Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Boîte de dialogue pages de propriétés du projet avec format de champ et arborescence

 L’arborescence de la boîte de dialogue pages de propriétés n’est pas construite à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . L’environnement, en fonction du nom de niveau qui lui est transmis par les <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfaces et, le génère.

 Seules deux catégories de niveau supérieur sont disponibles sur les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pages de propriétés :

- Propriétés communes, qui affichent des informations indépendantes de la configuration pour les objets sélectionnés. Par conséquent, lorsque l’une des sous-catégories de propriétés communes est sélectionnée, les options de configuration, de plateforme et de Configuration Manager dans la partie supérieure de la boîte de dialogue ne sont pas disponibles.

- Propriétés de configuration, qui contiennent des informations dépendantes de la configuration relatives au débogage, à l’optimisation et aux paramètres de build pour la solution ou le projet.

  Vous ne pouvez pas créer de catégories de niveau supérieur supplémentaires, mais vous pouvez choisir de ne pas en afficher l’une ou l’autre dans votre implémentation de `IVsPropertyPage` . Si, par exemple, vous ne disposez pas de propriétés indépendantes de la configuration à afficher pour un objet, vous pouvez choisir de ne pas afficher la catégorie Propriétés communes. Vous affichez les propriétés communes si `ISpecifyPropertyPages` est implémenté à partir de l’objet de navigation et des propriétés de configuration de l’élément lorsque vous implémentez `ISpecifyPropertyPages` dans l’objet de configuration (l’objet implémentant `IVsCfg` , `IVsProjectCfg` et les interfaces associées).

  Chaque catégorie affichée sous une catégorie de niveau supérieur représente une page de propriétés distincte. Les entrées de catégorie et de sous-catégorie disponibles dans la boîte de dialogue sont déterminées par votre implémentation de `ISpecifyPropertyPages` et `IVsPropertyPage` .

  `IDispatch` les objets des éléments du conteneur de sélection qui ont des propriétés à afficher sur les pages de propriétés implémentent `ISpecifyPropertyPages` pour énumérer une liste d’ID de classe. Les ID de classe sont passés en tant que variables à `ISpecifyPropertyPages` et sont utilisés pour instancier les pages de propriétés. La liste des ID de classe est également passée à `IVsPropertyPage` pour créer l’arborescence à gauche de la boîte de dialogue. Les pages de propriétés repassent ensuite les informations à l' `IDispatch` objet qui implémente `ISpecifyPropertyPages` et renseigne les informations pour chaque page.

  Les propriétés de l’objet parcourir sont extraites à l’aide `IDispatch` de pour chaque objet dans le conteneur de sélection.

  L’implémentation `Help::DisplayTopicFromF1Keyword` de dans votre VSPackage fournit les fonctionnalités du bouton aide.

  Pour plus d’informations, consultez `IDispatch` et `ISpecifyPropertyPages` dans MSDN Library.

  Le deuxième type des pages de propriétés affichées dans les exemples héberge une forme de la grille des propriétés, comme illustré dans la capture d’écran suivante.

  ![Pages de propriétés VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Boîte de dialogue pages de propriétés avec grille des propriétés

  Les interfaces `IVSMDPropertyBrowser` et `IVSMDPropertyGrid` (déclarées dans vsmanaged. h) sont utilisées pour créer et remplir la grille de propriétés dans une boîte de dialogue ou une fenêtre.

  L’architecture des projets a considérablement changé par rapport aux versions antérieures de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . En particulier, la notion de projet actif a changé. Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , il n’existe aucun concept de projet actif. Dans les environnements de développement précédents, le projet actif était le projet dans lequel les commandes de génération et de déploiement seraient par défaut, quel que soit le contexte. À présent, la solution contrôle et arbitre les commandes de génération et de déploiement qui s’appliquent aux projets.

  Ce qui était auparavant un projet actif est maintenant capturé de l’une des trois façons suivantes :

- Projet de démarrage

   Vous pouvez spécifier un ou des projets à partir de la page de propriétés de la solution qui est démarrée quand l’utilisateur appuie sur F5 ou sélectionne exécuter dans le menu Générer. Cela fonctionne de manière similaire à l’ancien projet actif dans la mesure où son nom est affiché en Explorateur de solutions avec une police en gras.

   Vous pouvez récupérer le projet de démarrage en tant que propriété dans le modèle Automation en appelant `DTE.Solution.SolutionBuild.StartupProjects` . Dans un VSPackage, vous appelez les <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> méthodes ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> . `IVsSolutionBuildManager` est disponible en tant que service par `QueryService` sur SID_SVsSolutionBuildManager. Pour plus d’informations, consultez [objet de configuration de projet](../../extensibility/internals/project-configuration-object.md) et configuration de [solution](../../extensibility/internals/solution-configuration.md).

- Configuration de build de solution active

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dispose d’une configuration de solution active, disponible dans le modèle Automation en implémentant `DTE.Solution.SolutionBuild.ActiveConfiguration` . Une configuration de solution est une collection qui contient une configuration de projet pour chaque projet dans la solution (chaque projet peut avoir plusieurs configurations, sur plusieurs plateformes, avec des noms différents). Pour plus d’informations sur les pages de propriétés de la solution, consultez Configuration de la [solution](../../extensibility/internals/solution-configuration.md).

- Projet actuellement sélectionné

   Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> méthode pour récupérer la hiérarchie de projet et les éléments de projet sélectionnés. À partir de DTE, vous devez utiliser les `SelectedItems.SelectedItem.Project` `SelectedItems.SelectedItem.ProjectItem` méthodes et. Il y a un exemple de code sous ces en-têtes dans les documents de base [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Objet de configuration de projet](../../extensibility/internals/project-configuration-object.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
