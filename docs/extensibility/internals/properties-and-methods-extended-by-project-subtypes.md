---
title: "Propriétés et méthodes étendu aux sous-types de projet | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 38bb86636edeaeda4485b7ebe6c8a6349450343c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Propriétés et méthodes étendus par les sous-types de projets
Un sous-type de projet a beaucoup d’énergie pour influencer le comportement du projet, car il est construit comme une agrégation d’un projet de base. Cette section présente certaines des fonctionnalités qui peuvent être améliorées ou modifiées par les sous-types de projets.  
  
## <a name="features-gained-by-aggregation"></a>Fonctionnalités acquises par agrégation  
 Le tableau suivant résume la plupart des méthodes permettant d’agrégation sous-types de projets à remplacer dans les projets de base.  
  
|Méthodes de substitution par agrégation|Sous-type de projet|  
|---------------------------------------|---------------------|  
|À partir de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Permet à un sous-type de projet<br /><br /> -Modifier la légende et l’icône du nœud de projet.<br />-Substituent projets `Browse` objet.<br />-Contrôle si le projet peut être renommé.<br />-Ordre de tri control.<br />-Contrôle utilisateur final pour l’aide dynamique.|  
|À partir de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Permet à un sous-type de projet contrôler les services contextuels sont fournies pour les concepteurs et les éditeurs.|  
|À partir de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Permet à un sous-type de projet<br /><br /> -Participer le routage des commandes pour les commandes du projet.<br />-Permet d’ajouter, supprimer ou désactiver des commandes ambiante de projet et les commandes actives de l’Explorateur de solutions.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Permet le sous-type de projet filtrer ce que l’utilisateur voit dans le **ajouter un nouvel élément** boîte de dialogue.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Permet à un sous-type de projet<br /><br /> -Déterminez le générateur par défaut avec une extension de fichier.<br />-Mapper un nom de générateur lisible humaine à un objet COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Propriétés utilisées par les sous-types de projets  
 Le système de projet d’environnement et de base peut utiliser les propriétés de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>et <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>énumérations décrites dans le tableau suivant pour activer un sous-type de projet contrôler les différentes fonctionnalités du système de projet.</xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> </xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>  
  
|Propriété VSHPROPID|Sous-type de projet|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Permet à un sous-type de projet contrôler le contenu de la **ajouter un élément** boîte de dialogue. Du sous-type de projet permettre fournir une nouvelle spécification de répertoires de modèle, ajouter de nouveaux types d’éléments, supprimez des éléments et réorganiser un sous-ensemble des éléments dans le projet de base de **ajouter un élément** boîte de dialogue.|  
|`PropertyPagesCLSIDList`|Permet à un sous-type de projet Ajouter ou supprimer des pages de propriétés de configuration indépendants.|  
|`CfgPropertyPagesCLSIDList`|Permet à un sous-type de projet Ajouter ou supprimer des pages de propriétés de dépend de la configuration.|  
|`ExtObjectCATID`|Permet à un sous-type de projet fournir un extendeur Automation pour le projet ou le projet d’objets d’élément en connaissant le CATID de l’extendeur. Par exemple, un sous-type de projet peut fournir un personnalisé `Project.Extender("<subtype>")` objet.|  
|`BrowseObjectCATID`|Permet à un sous-type de projet fournir un extendeur Automation pour le `Browse` objet en connaissant le CATID de l’extendeur. Par exemple, un sous-type de projet permettre ajouter des propriétés supplémentaires à la <xref:EnvDTE.Project.Properties%2A>collection.</xref:EnvDTE.Project.Properties%2A>|  
|`CfgBrowseObjectCATID`|Permet à un sous-type de projet fournir un extendeur de l’automatisation de l’objet configuration projet. Par exemple, un sous-type de projet permettre ajouter des propriétés supplémentaires à la <xref:EnvDTE.Configuration.Properties%2A>collection.</xref:EnvDTE.Configuration.Properties%2A>|  
|`CfgExtObjectCATID`|Permet à un sous-type de projet fournir un extendeur Automation de l’objet de configuration.|  
|`DefaultPlatformName`|Permet à un sous-type de projet déterminer le nom de la plateforme pour les objets de configuration du projet.|  
  
 Le projet de base fournit une implémentation par défaut des propriétés ci-dessus. Le projet de base obtient en appelant `QueryInterface` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>sur le sous-type de projet extérieur, ce qui permet de substituer l’implémentation des propriétés du sous-type de projet.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
## <a name="see-also"></a>Voir aussi  
 [Conception des sous-types de projet](../../extensibility/internals/project-subtypes-design.md)
