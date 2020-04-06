---
title: Conception de sous-types de projets Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706444"
---
# <a name="project-subtypes-design"></a>Conception de sous-types de projets

Les sous-types de projet permettent à VSPackages d’étendre des projets basés sur le moteur microsoft Build (MSBuild). L’utilisation de l’agrégation vous permet de réutiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la majeure partie du système de projet géré de base mis en œuvre tout en personnaliser le comportement pour un scénario particulier.

 Les sujets suivants détaillent la conception de base et la mise en œuvre des sous-types de projets :

- Conception de sous-type de projet.

- Agrégation multi-niveaux.

- Interfaces de soutien.

## <a name="project-subtype-design"></a>Conception de sous-type de projet

L’initialisation d’un sous-type de projet est <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> réalisée en agrégeant le principal et les objets. Cette agrégation permet à un sous-type de projet de remplacer ou d’améliorer la plupart des capacités du projet de base. Les sous-types de projet obtiennent la <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>première chance <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>de manipuler des <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>propriétés utilisant, commandes utilisant et, et gestion d’élément de projet utilisant . Les sous-types de projet peuvent également s’étendre :

- Objets de configuration de projet.

- Objets dépendants de la configuration.

- Configuration-indépendant parcourir les objets.

- Objets d’automatisation de projet.

- Collections de propriétés d’automatisation de projet.

Pour plus d’informations sur l’extéabilité par les sous-types de projet, voir [Propriétés et méthodes étendues par les sous-types de projet .](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

### <a name="policy-files"></a>Fichiers de stratégie

L’environnement [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit un exemple d’extension du système de projet de base avec un sous-type de projet dans sa mise en œuvre des dossiers de politique. Un fichier de politique [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] permet de façonner l’environnement en gérant les fonctionnalités qui incluent la solution Explorer, **add Project** dialog box, **Add New Item** dialog box et la boîte de dialogue **Properties.** Le sous-type de stratégie l’emporte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>et `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> améliore ces fonctionnalités par le biais et les implémentations.

### <a name="aggregation-mechanism"></a>Mécanisme d’agrégation

Le mécanisme d’agrégation de sous-types de projet de l’environnement prend en charge de multiples niveaux d’agrégation, permettant ainsi la mise en œuvre d’un sous-type avancé en aromatisant davantage un projet aromatisé. En outre, les objets de soutien d’un sous-type de projet, tels que <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, sont conçus pour permettre plusieurs niveaux de superposition. Conformément aux contraintes des règles d’agrégation com et COM, les sous-types de projets et les projets de base doivent être programmés en coopération pour permettre au sous-type intérieur ou au projet de base de participer correctement à la délégation des appels de méthode et à la gestion des comptes de référence. Autrement dit, le projet sur le point d’être agrégé doit être programmé pour soutenir l’agrégation.

L’illustration suivante montre une représentation schématique d’une agrégation de sous-type de projet à plusieurs niveaux.

![Graphique projectflavor à plusieurs niveaux Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Une agrégation de sous-type de projet à plusieurs niveaux se compose de trois niveaux, un projet de base, qui est agrégé par un sous-type de projet, puis encore agrégé par un sous-type de projet avancé. Le chiffre se concentre sur certaines des interfaces de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] soutien qui sont fournis dans le cadre de l’architecture de sous-type du projet.

### <a name="deployment-mechanisms"></a>Mécanismes de déploiement

Parmi les nombreuses fonctionnalités du système de projet de base améliorées par un sous-type de projet, il y a les mécanismes de déploiement. Un sous-type de projet influence les mécanismes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> déploiement <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>en mettant en œuvre des <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>interfaces de configuration (telles que et ) qui sont récupérées en appelant QueryInterface sur . Dans un scénario où le sous-type de projet et le sous-type `QueryInterface` avancé du projet ajoutent des `IUnknown`implémentations de configuration différentes, le projet de base fait appel au sous-type de projet avancé. Si le sous-type de projet intérieur contient la mise en œuvre de configuration que le projet de base demande, le sous-type de projet avancé délégue à la mise en œuvre fournie par le sous-type de projet intérieur. En tant que mécanisme permettant de maintenir l’état d’un niveau d’agrégation à l’autre, tous les niveaux de sous-types de projet mettent en œuvre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pour persister les données XML non-build connexes dans les fichiers du projet. Pour plus d’informations, voir [Données persistantes dans le fichier de projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>est mis en œuvre comme un mécanisme pour récupérer les extenseurs d’automatisation des sous-types de projet.

L’illustration suivante se concentre sur la mise en œuvre de l’extension d’automatisation, la configuration du projet parcourir l’objet en particulier, utilisé par les sous-types de projet pour étendre le système de projet de base.

![Graphique d'extendeur automatique de la version d'un projet VS](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Les sous-types de projet peuvent étendre davantage le système de projet de base en étendant le modèle d’objet d’automatisation. Ceux-ci sont définis comme faisant partie de l’objet d’automatisation DTE et sont utilisés pour étendre l’objet Project, l’objet `ProjectItem` et l’objet. `Configuration` Pour plus d’informations voir, [Extension du modèle d’objet du projet de base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Agrégation multi-niveaux

Une mise en œuvre de sous-type de projet qui enveloppe un sous-type de projet de niveau inférieur doit être programmée en coopération pour permettre au sous-type de projet intérieur de fonctionner correctement. Une liste des responsabilités en matière de programmation comprend :

- La <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> mise en œuvre du sous-type du projet <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> qui enveloppe le sous-type <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> intérieur <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> doit déléguer à la mise en œuvre du sous-type de projet intérieur pour les deux et les méthodes.

- La <xref:EnvDTE80.IInternalExtenderProvider> mise en œuvre du sous-type du projet d’emballage doit déléguer à celle de son sous-type de projet intérieur. En particulier, la <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> mise en œuvre des besoins pour obtenir la chaîne de noms du sous-type de projet intérieur, puis concatenate les chaînes qu’il veut ajouter comme extenseurs.

- La <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> mise en œuvre d’un sous-type de projet d’emballage doit instantané l’objet de son sous-type de projet intérieur et le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> tenir comme un délégué privé, puisque seul l’objet de configuration du projet de base sait directement que l’objet de configuration de sous-type de projet d’emballage existe. Le sous-type de projet externe peut d’abord choisir des interfaces de configuration qu’il veut <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>gérer directement, puis déléguer le reste à la mise en œuvre du sous-type de projet intérieur de .

## <a name="supporting-interfaces"></a>Interfaces de soutien

Les délégués du projet de base appellent à soutenir les interfaces ajoutées par un sous-type de projet, afin d’étendre divers aspects de sa mise en œuvre. Cela comprend l’extension des objets de configuration de projet et divers objets de navigateur de propriété. Ces interfaces sont récupérées `punkOuter` en faisant `IUnknown`appel `QueryInterface` (un pointeur à la ) de l’agrégateur de sous-type de projet le plus externe.

|Interface|Projet Subtype|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Permet au sous-type du projet de :<br /><br /> - Fournir une <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>mise en œuvre de .<br />- Contrôler le lancement du débbugger en permettant au sous-type de projet de fournir sa propre mise en œuvre de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />- Désactiver l’évaluation de l’expression `DBGLAUNCH_DesignTimeExprEval` en temps <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>de conception en traitant convenablement le cas dans sa mise en œuvre de .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Permet au sous-type du projet de :<br /><br /> - Étendre <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> le projet pour ajouter ou supprimer les propriétés indépendantes de configuration du projet.<br />- Étendre l’objet<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>d’automatisation du projet ( ) du projet.<br /><br /> Les valeurs des <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> propriétés ci-dessus sont tirées de l’énumération.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permet au sous-type de projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> de remonter à l’objet étant donné que la configuration du projet navigue sur l’objet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permet au sous-type de projet <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de `VSITEMID` remonter à l’objet ou à l’objet, étant donné que la configuration du projet navigue sur l’objet.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permet au sous-type du projet de maintenir arbitraires des données structurées XML au fichier du projet (.vbproj ou .csproj). Ces données ne sont pas visibles par MSBuild.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Permet au sous-type du projet de :<br /><br /> - Ajouter de nouvelles propriétés MSBuild à persister.<br />- Supprimer les propriétés inutiles de MSBuild.<br />- Requête pour une valeur actuelle d’une propriété MSBuild.<br />- Modifier la valeur actuelle d’une propriété MSBuild.|

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
