---
title: Projet sous-types conception | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 126bee146d1f53233db3c14672f80da4c0d60e9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes-design"></a>Conception des sous-types de projet
Les sous-types de projet permettent VSPackages d’étendre des projets basés sur Microsoft Build Engine (MSBuild). L’utilisation d’agrégation vous permet de réutiliser la majeure partie du système de projet de base managées implémentée dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] toujours personnaliser le comportement pour un scénario particulier.  
  
 Les rubriques suivantes décrivent la conception de base et l’implémentation de sous-types de projet :  
  
-   Conception du sous-type de projet.  
  
-   Agrégation de plusieurs niveaux.  
  
-   Prise en charge des Interfaces.  
  
## <a name="project-subtype-design"></a>Conception de sous-type de projet  
 L’initialisation d’un sous-type de projet s’effectue en agrégeant les principaux <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objets. Cette agrégation permet un sous-type de projet substituer ou améliorer la plupart des fonctionnalités du projet de base. Les sous-types de projet obtenir la première occasion de gérer à l’aide des propriétés <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, à l’aide des commandes <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>et la gestion de l’élément projet à l’aide <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Les sous-types de projet peuvent également étendre :  
  
-   Objets de configuration de projet.  
  
-   Objets dépend de la configuration.  
  
-   Indépendant de la configuration de parcourir les objets.  
  
-   Objets automation de projet.  
  
-   Collections de propriétés automation de projet.  
  
 Pour plus d’informations sur l’extensibilité aux sous-types de projet, consultez [propriétés et méthodes étendues aux sous-types de projet](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Fichiers de stratégie  
 Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement fournit un exemple d’extension du système de projet de base avec un sous-type de projet dans son implémentation de fichiers de stratégie. Un fichier de stratégie permet la mise en forme de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement grâce à la gestion des fonctionnalités qui incluent l’Explorateur de solutions, **ajouter un projet** boîte de dialogue, **ajouter un nouvel élément** boîte de dialogue et les  **Propriétés** boîte de dialogue. Le sous-type de stratégie remplace et améliore ces fonctionnalités via <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> implémentations.  
  
##### <a name="aggregation-mechanism"></a>Mécanisme d’agrégation  
 Mécanisme d’agrégation sous-type de projet de l’environnement prend en charge plusieurs niveaux d’agrégation, ce qui permet un sous-type avancé à être implémentées par AROMATISANT supplémentaire pour un projet de plusieurs versions. En outre, les objets de prise en charge d’un projet de sous-type, tel que <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, sont conçus pour permettre à plusieurs niveaux de superposition. Dans les contraintes de COM et COM règles d’agrégation, sous-types de projet et projets de base doivent être programmées de manière coopérative pour activer le sous-type interne ou le projet de base de participer correctement de déléguer des appels de méthode et la gestion des décomptes de références . Autrement dit, le projet sur le point d’être agrégée doit être programmées pour prendre en charge d’agrégation.  
  
 L’illustration suivante montre une représentation schématique d’une agrégation de sous-type de projet à plusieurs niveaux.  
  
 ![Graphique de projet à plusieurs niveaux Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Sous-type de projet à plusieurs niveaux  
  
 Une agrégation de sous-type de projet à plusieurs niveaux se compose de trois niveaux, un projet de base, qui est agrégée par un sous-type de projet, puis davantage agrégées par un sous-type avancées du projet. La figure met l’accent sur certaines interfaces de prise en charge qui sont fournis dans le cadre de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] architecture du sous-type de projet.  
  
##### <a name="deployment-mechanisms"></a>Mécanismes de déploiement  
 Parmi d’autres du système de projet de base de fonctionnalités améliorées grâce à un sous-type de projet sont des mécanismes de déploiement. Un sous-type de projet détermine les mécanismes de déploiement en implémentant des interfaces de configuration (tel que <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) qui sont récupérées par l’appel QueryInterface sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. Dans un scénario où le sous-type de projet et le sous-type de projet avancé ajouter des implémentations de configuration différente, le projet de base appelle `QueryInterface` sur le sous-type de projet avancé `IUnknown`. Si le sous-type de projet interne contient l’implémentation de configuration demandant le projet de base, le sous-type de projet avancé délègue à l’implémentation fournie par le sous-type de projet interne. Comme un mécanisme pour rendre persistant l’état de niveau d’une agrégation vers un autre, tous les niveaux de sous-types de projet implémentent <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pour conserver la build non lié les données XML dans les fichiers de projet. Pour plus d’informations, consultez [persistance des données dans le fichier projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>est implémenté comme un mécanisme permettant de récupérer les sous-types de projet des extendeurs automation.  
  
 L’illustration suivante met l’accent sur l’implémentation d’extendeur automation, l’objet configuration projet en particulier, utilisé par les sous-types de projet pour étendre le système de projet de base.  
  
 ![Graphique d’extendeur automatique de la version projet VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Extendeur de Automation de sous-type de projet.  
  
 Les sous-types de projet peuvent étendre davantage le système de projet de base en étendant le modèle objet automation. Ceux-ci sont définies dans le cadre de l’objet automation DTE et sont utilisés pour étendre l’objet de projet, le `ProjectItem` objet et le `Configuration` objet. Pour plus d’informations, consultez [extension du modèle d’objet du projet de Base de](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Agrégation de plusieurs niveaux  
 Une implémentation de sous-type de projet qui encapsule un sous-type de projet de niveau inférieur doit être programmées de manière coopérative pour autoriser le sous-type de projet interne fonctionner correctement. Une liste des responsabilités de programmation comprend :  
  
-   Le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> mise en œuvre du sous-type de projet qui encapsule le sous-type interne doit déléguer à la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> mise en œuvre du sous-type de projet interne pour les deux <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> méthodes.  
  
-   Le <xref:EnvDTE80.IInternalExtenderProvider> implémentation du sous-type de projet wrapper doit déléguer à celui de son sous-type de projet interne. En particulier, l’implémentation de <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> doit obtenir la chaîne des noms à partir du sous-type de projet interne et puis concaténer les chaînes qu’il souhaite ajouter en tant qu’extensions.  
  
-   Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> implémentation d’un sous-type de projet wrapper doit instancier la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objet de son interne sous-type de projet et maintenez-le enfoncé comme un délégué privé, étant donné qu’uniquement l’objet de configuration de projet du projet de base sait directement que le wrapper objet de configuration de sous-type de projet existe. Le sous-type de projet externe peut initialement choisissez il souhaite gérer directement des interfaces de configuration, puis de déléguer le reste à l’implémentation du sous-type de projet interne de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Prise en charge des Interfaces  
 Le projet de base délègue les appels à la prise en charge des interfaces ajoutées par un sous-type de projet, d’étendre les différents aspects de son implémentation. Cela inclut l’extension des objets de configuration de projet et les différents objets de navigateur de propriété. Ces interfaces sont récupérés en appelant `QueryInterface` sur `punkOuter` (un pointeur vers le `IUnknown`) de l’agrégation de sous-type de projet extérieur.  
  
|Interface|Sous-type de projet|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permet le sous-type de projet pour :<br /><br /> -Fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Contrôler le lancement du débogueur en autorisant le sous-type de projet fournir sa propre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Désactiver l’évaluation de l’expression au moment du design en gérant correctement le `DBGLAUNCH_DesignTimeExprEval` cas dans son implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Permet le sous-type de projet pour :<br /><br /> -Permet d’étendre le <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> du projet pour ajouter ou supprimer des propriétés indépendantes de configuration du projet.<br />-Extension de l’objet automation de projet (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) du projet.<br /><br /> Les valeurs de propriété ci-dessus sont tirées de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> énumération.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permet le sous-type de projet à mapper vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objet en fonction de l’objet configuration projet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permet le sous-type de projet à mapper vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ou `VSITEMID` objet, en fonction de l’objet configuration projet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permet le sous-type de projet rendre persistantes des données XML structurée arbitraires dans le fichier projet (.vbproj ou .csproj). Ces données ne sont pas visibles à MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permet le sous-type de projet pour :<br /><br /> -Ajouter de nouvelles propriétés de MSBuild à rendre persistantes.<br />-Supprimer les propriétés inutiles dans MSBuild.<br />-Requête pour une valeur actuelle d’une propriété de MSBuild.<br />-Modifier la valeur actuelle d’une propriété de MSBuild.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>