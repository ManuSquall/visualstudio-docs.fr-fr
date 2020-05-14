---
title: Objet de configuration du projet (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706658"
---
# <a name="project-configuration-object"></a>Objet de configuration de projet
L’objet de configuration du projet gère l’affichage des informations de configuration à l’interface utilisateur.

 ![Configuration de projet de studio visuel](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Pages de propriété de configuration de projet

 Le fournisseur de configuration de projet gère les configurations du projet. L’environnement et d’autres paquets, pour accéder et récupérer des informations sur les configurations d’un projet, appellent les interfaces attachées à l’objet Project Configuration Provider.

> [!NOTE]
> Vous ne pouvez pas créer ou modifier les fichiers de configuration de solution de manière programmatique. Vous devez utiliser `DTE.SolutionBuilder`. Voir [Configuration de solution](../../extensibility/internals/solution-configuration.md) pour plus d’informations.

 Pour publier un nom d’affichage à utiliser dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>l’interface utilisateur de configuration, votre projet doit implémenter . L’environnement <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>appelle , qui `IVsCfg` renvoie une liste de pointeurs que vous pouvez utiliser pour obtenir les noms d’affichage pour les informations configuration et plate-forme à listed dans l’interface utilisateur de l’environnement. La configuration et la plate-forme actives sont déterminées par la configuration du projet stockée dans la configuration de la solution active. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> méthode peut être utilisée pour récupérer la configuration active du projet.

 L’objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> peut être implémenté sur l’objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> avec l’objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> pour vous permettre de récupérer un `IVsProjectCfg2` objet basé sur le nom de configuration du projet canonique.

 Une autre façon de fournir à l’environnement et à d’autres `IVsCfgProvider2::GetCfgs` projets l’accès aux configurations de projets est que les projets fournissent une mise en œuvre de la méthode pour retourner un ou plusieurs objets de configuration. Les projets <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>peuvent également implémenter , qui hérite de `IVsProjectCfg` et donc de `IVsCfg`, pour fournir des informations spécifiques à la configuration. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>prend en charge les plates-formes et les fonctionnalités pour l’ajout, la suppression et le changement de nom des configurations de projet.

> [!NOTE]
> Étant donné que Visual Studio ne se limite plus à deux types de configuration, le code qui traite les configurations ne doit pas être écrit avec des hypothèses sur le nombre de configurations, ni l’hypothèse qu’un projet qui n’a qu’une seule configuration est nécessairement Debug ou Retail. Cela rend l’utilisation <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsolète.

 Appel `QueryInterface` sur l’objet retourné de`IVsGetCfgProvider::GetCfgProvider` récupérations `IVsCfgProvider2`. Si `IVsGetCfgProvider` vous n’êtes pas trouvé en faisant appel `QueryInterface` à l’objet du `IVsProject3` projet, vous pouvez accéder à l’objet du fournisseur de configuration en faisant appel `QueryInterface` à l’objet de navigateur racine de hiérarchie pour l’objet retourné pour, `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`ou par un pointeur au fournisseur de configuration retourné pour `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 `IVsProjectCfg2`permet principalement aux projets d’accéder à des objets de gestion de construction, de débogé et de déploiement et permet aux projets la liberté de regrouper les extrants. Les méthodes `IVsProjectCfg` `IVsProjectCfg2` et peuvent être <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> utilisées pour mettre <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> en œuvre pour gérer le processus de construction, et les pointeurs pour les groupes de sortie d’une configuration.

 Le projet doit retourner le même nombre de groupes pour chaque configuration qu’il prend en charge, même si le nombre de sorties contenues dans un groupe peut varier d’une configuration à l’autre. Les groupes doivent également disposer des mêmes informations d’identification (nom canonique, nom d’affichage et informations de groupe) de la configuration à la configuration au sein d’un projet. Pour plus d’informations, voir [Configuration du projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).

 Pour permettre le débogage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>vos configurations doivent être implémentées. `IVsDebuggableProjectCfg`est une interface facultative mise en œuvre par des projets pour `IVsCfg` `IVsProjectCfg`permettre au débbugeur de lancer une configuration et est implémentée sur l’objet de configuration avec et . L’environnement l’appelle lorsque l’utilisateur choisit de démarrer le débbuggeur en appuyant sur F5.

 `ISpecifyPropertyPages`et `IDispatch` sont utilisés en conjonction avec les pages de propriété pour récupérer et afficher des informations dépendantes de la configuration à l’utilisateur. Pour plus d’informations, voir [Pages de propriété](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)
- [Pages de propriétés](../../extensibility/internals/property-pages.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
