---
title: Conception des sous-types de projet | Microsoft Docs
description: Découvrez comment les sous-types de projet permettent aux VSPackages d’étendre des projets basés sur le Microsoft Build Engine (MSBuild).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c04c8e681646aed6816c645defe7ffd87ac7033c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899691"
---
# <a name="project-subtypes-design"></a>Conception de sous-types de projets

Les sous-types de projet permettent aux VSPackages d’étendre les projets en fonction de l’Microsoft Build Engine (MSBuild). L’utilisation de l’agrégation vous permet de réutiliser la majeure partie du système de projet géré principal implémenté dans tout en configurant [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] toujours le comportement pour un scénario particulier.

 Les rubriques suivantes décrivent en détail la conception et l’implémentation de base des sous-types de projet :

- Conception de sous-type de projet.

- Agrégation à plusieurs niveaux.

- Interfaces de prise en charge.

## <a name="project-subtype-design"></a>Conception de sous-type de projet

L’initialisation d’un sous-type de projet est obtenue en regroupant <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> les <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objets main et. Cette agrégation permet à un sous-type de projet de remplacer ou d’améliorer la plupart des fonctionnalités du projet de base. Les sous-types de projet permettent de gérer les propriétés à l’aide des <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> commandes, à l’aide <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de et de et de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> gestion des éléments de projet à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Les sous-types de projet peuvent également étendre les éléments suivants :

- Objets de configuration de projet.

- Objets dépendants de la configuration.

- Objets de navigation indépendants de la configuration.

- Objets Automation de projet.

- Collections de propriétés Automation de projet.

Pour plus d’informations sur l’extensibilité par les sous-types de projet, consultez [Propriétés et méthodes étendues par les sous-types de projet](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>Fichiers de stratégie

L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement fournit un exemple d’extension du système de projet de base avec un sous-type de projet dans son implémentation des fichiers de stratégie. Un fichier de stratégie permet la mise en forme de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement en gérant les fonctionnalités qui incluent les Explorateur de solutions, la boîte de dialogue **Ajouter un projet** , la boîte de dialogue **Ajouter un nouvel élément** et la boîte de dialogue **Propriétés** . Le sous-type de stratégie remplace et améliore ces fonctionnalités par le biais des <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` implémentations de et de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .

### <a name="aggregation-mechanism"></a>Mécanisme d’agrégation

Le mécanisme d’agrégation de sous-type de projet de l’environnement prend en charge plusieurs niveaux d’agrégation, ce qui permet d’implémenter un sous-type avancé en renforçant davantage un projet aromatisé. En outre, les objets de prise en charge d’un sous-type de projet, tels que <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> , sont conçus pour autoriser plusieurs niveaux de superposition. Conformément aux contraintes des règles d’agrégation com et COM, les sous-types de projet et les projets de base doivent être programmés de manière coopérative pour permettre au sous-type interne ou au projet de base de participer correctement à la délégation des appels de méthode et à la gestion des nombres de références. Autrement dit, le projet sur le sujet de l’agrégation doit être programmé pour prendre en charge l’agrégation.

L’illustration suivante montre une représentation schématique d’une agrégation de sous-types de projet à plusieurs niveaux.

![Graphique projectflavor à plusieurs niveaux Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Une agrégation de sous-types de projet à plusieurs niveaux se compose de trois niveaux, un projet de base, qui est agrégé par un sous-type de projet, puis regroupé par un sous-type de projet avancé. La figure se concentre sur certaines des interfaces de prise en charge fournies dans le cadre de l’architecture du sous- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] type de projet.

### <a name="deployment-mechanisms"></a>Mécanismes de déploiement

Parmi les nombreuses fonctionnalités du système de projet de base améliorées par un sous-type de projet, citons les mécanismes de déploiement. Un sous-type de projet influence les mécanismes de déploiement en implémentant des interfaces de configuration (telles que <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ) qui sont récupérées en appelant QueryInterface sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . Dans un scénario où le sous-type de projet et le sous-type de projet avancé ajoutent des implémentations de configuration différentes, le projet de base appelle `QueryInterface` sur le sous-type de projet avancé `IUnknown` . Si le sous-type de projet interne contient l’implémentation de configuration demandée par le projet de base, le sous-type de projet avancé délègue à l’implémentation fournie par le sous-type de projet interne. Comme mécanisme de conservation de l’état d’un niveau d’agrégation à un autre, tous les niveaux des sous-types de projet implémentent <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pour conserver les données XML non liées à la génération dans les fichiers projet. Pour plus d’informations, consultez [persistance des données dans le fichier projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider> est implémenté comme un mécanisme permettant de récupérer les extendeurs Automation à partir des sous-types de projet.

L’illustration suivante se concentre sur l’implémentation de l’extendeur Automation, l’objet parcourir de la configuration de projet, en particulier, utilisé par les sous-types de projet pour étendre le système de projet de base.

![Graphique d'extendeur automatique de la version d'un projet VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Les sous-types de projet peuvent étendre davantage le système de projet de base en étendant le modèle objet Automation. Ils sont définis dans le cadre de l’objet d’automatisation DTE et sont utilisés pour étendre l’objet de projet, l' `ProjectItem` objet et l' `Configuration` objet. Pour plus d’informations, consultez [extension du modèle objet du projet de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agrégation à plusieurs niveaux

Une implémentation de sous-type de projet qui encapsule un sous-type de projet de niveau inférieur doit être programmée de manière coopérative pour permettre au sous-type de projet interne de fonctionner correctement. La liste des responsabilités de programmation comprend les éléments suivants :

- L' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implémentation du sous-type de projet qui encapsule le sous-type interne doit déléguer à l' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> implémentation du sous-type de projet interne pour les deux <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> méthodes et.

- L' <xref:EnvDTE80.IInternalExtenderProvider> implémentation du sous-type de projet wrapper doit déléguer à celle de son sous-type de projet interne. En particulier, l’implémentation de <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> doit obtenir la chaîne de noms du sous-type de projet interne, puis concaténer les chaînes qu’elle souhaite ajouter en tant qu’extendeurs.

- L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> implémentation d’un sous-type de projet wrapper doit instancier l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> objet de son sous-type de projet interne et le conserver en tant que délégué privé, étant donné que seul l’objet de configuration de projet du projet de base sait directement que l’objet de configuration de sous-type de projet de wrapper existe. Le sous-type de projet externe peut choisir initialement les interfaces de configuration qu’il souhaite gérer directement, puis déléguer le reste à l’implémentation du sous-type de projet interne de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Interfaces de prise en charge

Le projet de base délègue les appels aux interfaces de prise en charge ajoutées par un sous-type de projet, afin d’étendre les différents aspects de son implémentation. Cela comprend l’extension des objets de configuration de projet et divers objets de l’Explorateur de propriétés. Ces interfaces sont récupérées en appelant `QueryInterface` on `punkOuter` (pointeur vers `IUnknown` ) de l’agrégateur de sous-type de projet le plus à l’extérieur.

|Interface|Sous-type de projet|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permet au sous-type de projet d’effectuer les opérations suivantes :<br /><br /> -Fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />-Contrôler le lancement du débogueur en permettant au sous-type de projet de fournir sa propre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />-Désactiver l’évaluation d’une expression au moment du design en gérant de manière appropriée le `DBGLAUNCH_DesignTimeExprEval` cas dans son implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Permet au sous-type de projet d’effectuer les opérations suivantes :<br /><br /> -Étendez le <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> du projet pour ajouter ou supprimer des propriétés indépendantes de la configuration du projet.<br />-Étendre l’objet Automation de projet ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) du projet.<br /><br /> Les valeurs des propriétés ci-dessus sont extraites de l' <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> énumération.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permet au sous-type de projet d’être mappé à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> objet en fonction de l’objet parcourir de la configuration de projet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permet au sous-type de projet d’être mappé à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> `VSITEMID` objet ou, en fonction de l’objet de navigation de la configuration de projet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permet au sous-type de projet de conserver des données structurées XML arbitraires dans le fichier projet (. vbproj ou. csproj). Ces données ne sont pas visibles par MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permet au sous-type de projet d’effectuer les opérations suivantes :<br /><br /> -Ajouter de nouvelles propriétés MSBuild à rendre persistantes.<br />-Supprimez les propriétés inutiles de MSBuild.<br />-Requête pour obtenir la valeur actuelle d’une propriété MSBuild.<br />-Modifier la valeur actuelle d’une propriété MSBuild.|

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
