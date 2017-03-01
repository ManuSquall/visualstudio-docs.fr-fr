---
title: Objet de Configuration de projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 11
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
ms.openlocfilehash: 0518e4844dd7fa7710935f742bf44943a5ef945d
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-object"></a>Objet de Configuration de projet
L’objet de configuration de projet gère l’affichage des informations de configuration à l’interface utilisateur.  
  
 ![Configuration de projet Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Pages de propriétés de configuration de projet  
  
 Le fournisseur de Configuration de projet gère les configurations de projet. L’environnement et autres packages, d’accéder à et récupérer des informations sur les configurations d’un projet, appelez les interfaces attachés à un objet de fournisseur de Configuration de projet.  
  
> [!NOTE]
>  Impossible de créer ou modifier des fichiers de configuration de solution par programme. Vous devez utiliser `DTE.SolutionBuilder`. Consultez la page [Configuration de la Solution](../../extensibility/internals/solution-configuration.md) pour plus d’informations.  
  
 Pour publier un nom complet à utiliser dans la configuration de l’interface utilisateur, votre projet doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> L’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, qui renvoie une liste de `IVsCfg` pointeurs que vous pouvez utiliser pour obtenir les noms d’affichage pour les informations de Configuration et de plateforme apparaissent dans l’interface utilisateur de l’environnement.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> La configuration active et la plateforme sont déterminés par la configuration du projet stockée dans la configuration de solution active. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>méthode peut être utilisée pour récupérer la configuration du projet actif.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>  
  
 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>objet peut éventuellement être implémenté sur le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>de l’objet avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>objet vous permet de récupérer une `IVsProjectCfg2` objet basé sur le nom de configuration de projet canonique.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>  
  
 Une autre consiste à fournir l’environnement et autres projets d’accéder aux configurations de projet pour les projets fournir une implémentation de la `IVsCfgProvider2::GetCfgs` méthode pour retourner un ou plusieurs objets de configuration. Les projets peuvent également implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, qui hérite de `IVsProjectCfg` et ainsi de `IVsCfg`, pour fournir des informations spécifiques à la configuration.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>prend en charge de plateformes et fonctionnalités pour l’ajout, suppression et modification du nom des configurations de projet.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>  
  
> [!NOTE]
>  Étant donné que Visual Studio n’est plus limité à deux types de configuration, le code qui traite les configurations ne doit pas être écrites avec les hypothèses sur le nombre de configurations, ni qu’il reconnaisse la supposition qu’un projet n'a qu’une seule configuration est nécessairement Retail ou Debug. Cela permet l’utilisation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>et <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>obsolète.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>  
  
 Appel de `QueryInterface` sur l’objet retourné à partir de`IVsGetCfgProvider::GetCfgProvider` récupère `IVsCfgProvider2`. Si `IVsGetCfgProvider` est introuvable en appelant `QueryInterface` sur la `IVsProject3` objet de projet, vous pouvez accéder à l’objet de fournisseur de configuration en appelant `QueryInterface` sur l’objet de navigateur hiérarchie racine de l’objet retourné pour `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, ou via un pointeur vers le fournisseur de configuration retourné pour `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2`principalement, fournit un accès à générer, déboguer et les objets de gestion de déploiement et permet aux projets de la liberté de sorties de groupe. Les méthodes de `IVsProjectCfg` et `IVsProjectCfg2` peut être utilisé pour implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>pour gérer le processus de génération et <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>des pointeurs pour les groupes de sortie d’une configuration.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>  
  
 Le projet doit retourner le même nombre de groupes pour chaque configuration pris en charge, même si le nombre de sorties contenue dans un groupe peut varier à partir de la configuration de. Les groupes doivent également posséder les mêmes informations d’identificateur (nom complet, nom d’affichage et les informations du groupe) à partir de la configuration de dans un projet. Pour plus d’informations, consultez [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).  
  
 Pour activer le débogage, vos configurations doivent implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> `IVsDebuggableProjectCfg`est une interface facultative est implémentée par les projets pour autoriser le débogueur à lancer une configuration et est implémentée sur l’objet de configuration avec `IVsCfg` et `IVsProjectCfg`. L’environnement appelle lorsque l’utilisateur choisit de démarrer le débogueur en appuyant sur F5.  
  
 `ISpecifyPropertyPages`et `IDispatch` sont utilisés conjointement avec les pages de propriétés pour récupérer et afficher des informations dépendantes de la configuration à l’utilisateur. Pour plus d’informations, consultez [Pages de propriétés](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des Options de Configuration](../../extensibility/internals/managing-configuration-options.md)   
 [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)   
 [Pages de propriétés](../../extensibility/internals/property-pages.md)   
 [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
