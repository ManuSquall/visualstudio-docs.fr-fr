---
title: Pages de propriétés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a45e4a98326fe829b8f87a4ecfce669118cd9d0e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952116"
---
# <a name="property-pages"></a>Pages de propriétés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les utilisateurs peuvent afficher et modifier les propriétés du projet dépend de la configuration et - indépendante à l’aide des pages de propriétés. Un **Pages de propriétés** bouton est activé dans le **propriétés** fenêtre ou sur la barre d’outils de l’Explorateur de solutions pour les objets qui fournissent une vue de page de propriété de l’objet sélectionné. Pages de propriétés sont créés par l’environnement et sont disponibles pour les projets et solutions. Ils peuvent, toutefois, également être mis à disposition pour les éléments de projet qui utilisent les propriétés dépendantes de la configuration. Cette fonctionnalité peut être utilisée lorsque les fichiers dans un projet nécessitent des paramètres de commutateur de compilateur différente générer correctement.  
  
## <a name="using-property-pages"></a>À l’aide des Pages de propriétés  
 Si une page de propriétés est déjà affichée et la sélection est modifiée (par exemple, à partir d’une solution à un projet), les informations affichées dans les pages de modifications pour afficher les propriétés de la nouvelle sélection. S’il n’y a pas de propriétés sur l’objet qui prennent en charge des pages de propriétés, la page de propriétés est vide.  
  
 Si plusieurs objets sont sélectionnés, la page de propriétés affiche l’intersection des propriétés pour tous les éléments sélectionnés. Si l’élément sélectionné ne contient pas de propriétés dépendantes de la configuration et la **Pages de propriétés** bouton sur la barre d’outils de l’Explorateur de solutions, le focus passe à la fenêtre Propriétés. Pour plus d’informations relatives à la fenêtre Propriétés et la sélection, consultez [étendre les propriétés](../../extensibility/internals/extending-properties.md).  
  
 Si les propriétés sont affichées pour plusieurs objets et que vous modifiez une valeur dans une page de propriétés, toutes les valeurs pour les objets sont définies sur la nouvelle valeur même si elles étaient initialement différents et la page était vide lorsque les propriétés d’un objet ont été affichées.  
  
 Il existe deux types généraux de **ProjectProperty Pages** boîtes de dialogue disponibles dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Dans le premier, pour les projets Visual Basic, par exemple, les pages de propriétés sont affichés à l’aide d’un format de champ, comme illustré dans la capture d’écran suivante. Dans la seconde, présenté plus loin dans cette section, la propriété des hôtes de page une grille de propriétés similaire à celle trouvée dans la fenêtre Propriétés.  
  
 ![Pages de propriétés de Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Boîte de dialogue Pages de propriétés de projet avec la structure d’arborescence et de format de champ  
  
 L’arborescence dans la boîte de dialogue Pages de propriétés n’est pas généré à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. L’environnement, basé sur le nom du niveau lui est passé par le <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfaces, il génère.  
  
 Il existe seulement deux catégories de niveau supérieur sur [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pages de propriétés :  
  
- Propriétés communes, qui affiche des informations liées à la configuration pour l’ou les objets sélectionnés. Par conséquent, lorsque l’un des sous-catégories de propriétés communes est sélectionné, les options de Configuration, la plateforme et Configuration Manager dans la partie supérieure de la boîte de dialogue ne sont pas disponibles.  
  
- Propriétés de configuration, qui contient des informations dépend de la configuration relatives aux paramètres de débogage, d’optimisation et de Build pour la solution ou le projet.  
  
  Impossible de créer des catégories de niveau supérieur supplémentaires, mais vous pouvez choisir de n’une ou l’autre dans votre implémentation de `IVsPropertyPage`. Si, par exemple, vous n’avez pas toutes les propriétés indépendantes de la configuration à afficher pour un objet, vous pouvez choisir de ne la catégorie de propriétés communes. Afficher les propriétés communes si `ISpecifyPropertyPages` est implémentée à partir de l’objet de recherche de l’élément et les propriétés de Configuration lorsque vous implémentez `ISpecifyPropertyPages` dans l’objet de configuration (l’objet implémentant `IVsCfg`, `IVsProjectCfg`et connexes interfaces).  
  
  Chaque catégorie affichée sous la catégorie de niveau supérieur représente une page de propriétés distinctes. Entrées de catégorie et sous-catégorie disponibles dans la boîte de dialogue sont déterminées par votre implémentation de `ISpecifyPropertyPages` et `IVsPropertyPage`.  
  
  `IDispatch` objets pour les éléments dans le conteneur de sélection qui ont des propriétés à afficher sur l’implémentation de pages de propriété `ISpecifyPropertyPages` pour énumérer une liste d’ID de classe. Les ID de classe sont passés en tant que variables à `ISpecifyPropertyPages` et sont utilisés pour instancier les pages de propriétés. La liste des ID de classe est également passée à `IVsPropertyPage` pour créer la structure d’arborescence à gauche de la boîte de dialogue. Les pages de propriétés, puis passez les informations de sauvegarde à la `IDispatch` objet qui implémente `ISpecifyPropertyPages` et remplit les informations relatives à chaque page.  
  
  Les propriétés de l’objet de recherche sont extraites à l’aide de `IDispatch` pour chaque objet dans le conteneur de sélection.  
  
  Implémentation `Help::DisplayTopicFromF1Keyword` dans votre VSPackage fournit les fonctionnalités pour le bouton aide.  
  
  Pour plus d’informations, consultez `IDispatch` et `ISpecifyPropertyPages`dans MSDN library.  
  
  Le deuxième type de pages de propriétés affichées dans les hôtes exemples une forme de la grille des propriétés, comme indiqué dans la capture d’écran suivante.  
  
  ![Pages de propriété VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
  Boîte de dialogue Pages de propriétés avec la grille des propriétés  
  
  Les interfaces `IVSMDPropertyBrowser` et `IVSMDPropertyGrid` (déclaré dans vsmanaged.h) sont utilisés pour créer et remplir la grille des propriétés au sein d’une boîte de dialogue ou une fenêtre.  
  
  L’architecture de projets a changé considérablement à partir de versions précédentes de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. En particulier, la notion de projet qui est active a changé. Dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], il n’existe aucun concept d’un projet actif. Dans les environnements de développement précédent, le projet actif a été le projet que vous créez et déployez des commandes est par défaut, quel que soit le contexte. À présent, la solution de contrôle et arbitre qui générer et déployer des commandes s’appliquent à des projets.  
  
  Ce qui était un projet actif est désormais capturée dans une des trois façons différentes :  
  
- Le projet de démarrage  
  
   Vous pouvez spécifier un ou plusieurs projets à partir de la page de propriétés de la solution qui démarrera lorsque l’utilisateur appuie sur F5 ou sélectionne l’exécution dans le menu Générer. Cela fonctionne de manière similaire à l’ancien projet actif en ce sens que son nom est affiché dans l’Explorateur de solutions avec la police en gras.  
  
   Vous pouvez récupérer le projet de démarrage en tant que propriété dans le modèle automation en appelant `DTE.Solution.SolutionBuild.StartupProjects`. Dans un VSPackage, vous appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> méthodes. `IVsSolutionBuildManager` est disponible en tant que service par `QueryService` sur SID_SVsSolutionBuildManager. Pour plus d’informations, consultez [objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md) et [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).  
  
- Configuration de build de solution Active  
  
   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a une configuration de solution active, disponible dans le modèle automation en implémentant `DTE.Solution.SolutionBuild.ActiveConfiguration`. Une configuration de solution est une collection qui contient une configuration de projet pour chaque projet dans la solution (chaque projet peut avoir plusieurs configurations, sur plusieurs plateformes, avec des noms différents). Pour plus d’informations relatives aux pages de propriétés de la solution, consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md).  
  
- Projet actuellement sélectionné  
  
   Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> méthode pour récupérer la hiérarchie de projet et les élément de projet ou les éléments sélectionnés. À partir de DTE, vous utiliseriez le `SelectedItems.SelectedItem.Project` et `SelectedItems.SelectedItem.ProjectItem` méthodes. Exemples de code sous ces en-têtes dans le cœur [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documents.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Objet de Configuration de projet](../../extensibility/internals/project-configuration-object.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
