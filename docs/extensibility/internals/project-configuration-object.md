---
title: Objet de configuration de projet | Microsoft Docs
description: Découvrez comment l’objet de configuration de projet gère l’affichage des informations de configuration dans l’interface utilisateur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 15a999f78d017c76ee021f86d81cb611310d079d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899860"
---
# <a name="project-configuration-object"></a>Objet de configuration de projet
L’objet de configuration de projet gère l’affichage des informations de configuration dans l’interface utilisateur.

 ![Configuration de projet Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Pages de propriétés de configuration du projet

 Le fournisseur de configuration de projet gère les configurations de projet. L’environnement et d’autres packages, pour accéder et récupérer des informations sur les configurations d’un projet, appelez les interfaces attachées à l’objet de fournisseur de configuration de projet.

> [!NOTE]
> Vous ne pouvez pas créer ou modifier des fichiers de configuration de solution par programmation. Vous devez utiliser `DTE.SolutionBuilder`. Pour plus d’informations, consultez Configuration de la [solution](../../extensibility/internals/solution-configuration.md) .

 Pour publier un nom complet à utiliser dans l’interface utilisateur de configuration, votre projet doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . L’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , qui retourne une liste de `IVsCfg` pointeurs que vous pouvez utiliser pour obtenir les noms d’affichage des informations de configuration et de plateforme à répertorier dans l’interface utilisateur de l’environnement. La configuration et la plateforme actives sont déterminées par la configuration du projet stockée dans la configuration de la solution active. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> méthode peut être utilisée pour récupérer la configuration du projet actif.

 L’objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> peut éventuellement être implémenté sur l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> objet avec l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objet pour vous permettre de récupérer un `IVsProjectCfg2` objet en fonction du nom de la configuration de projet canonique.

 Une autre façon de fournir l’environnement et d’autres projets avec accès aux configurations de projet est que les projets fournissent une implémentation de la `IVsCfgProvider2::GetCfgs` méthode pour retourner un ou plusieurs objets de configuration. Les projets peuvent également implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> , qui hérite de `IVsProjectCfg` et par conséquent de `IVsCfg` , pour fournir des informations spécifiques à la configuration. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> prend en charge les plateformes et les fonctionnalités permettant d’ajouter, de supprimer et de renommer des configurations de projet.

> [!NOTE]
> Étant donné que Visual Studio n’est plus limité à deux types de configuration, le code qui traite les configurations ne doit pas être écrit avec des hypothèses sur le nombre de configurations et ne doit pas non plus être écrit en supposant qu’un projet qui n’a qu’une seule configuration est nécessairement Debug ou Retail. Cela rend l’utilisation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsolète.

 Appel `QueryInterface` de sur l’objet retourné par les `IVsGetCfgProvider::GetCfgProvider` récupérations `IVsCfgProvider2` . Si `IVsGetCfgProvider` est introuvable en appelant `QueryInterface` sur l' `IVsProject3` objet de projet, vous pouvez accéder à l’objet de fournisseur de configuration en appelant `QueryInterface` sur l’objet de navigateur racine de la hiérarchie pour l’objet retourné pour `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` , ou via un pointeur vers le fournisseur de configuration retourné pour `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` fournit principalement un accès aux objets de gestion de build, de débogage et de déploiement et permet aux projets de regrouper les sorties. Les méthodes de `IVsProjectCfg` et `IVsProjectCfg2` peuvent être utilisées pour implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> pour gérer le processus de génération et des <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> pointeurs pour les groupes de sorties d’une configuration.

 Le projet doit retourner le même nombre de groupes pour chaque configuration qu’il prend en charge, même si le nombre de sorties contenues dans un groupe peut varier de la configuration à la configuration. Les groupes doivent également avoir les mêmes informations d’identificateur (nom canonique, nom d’affichage et informations de groupe) entre la configuration et la configuration au sein d’un projet. Pour plus d’informations, consultez [configuration du projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).

 Pour activer le débogage, vos configurations doivent implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` est une interface facultative implémentée par les projets pour permettre au débogueur de lancer une configuration et est implémentée sur l’objet de configuration avec `IVsCfg` et `IVsProjectCfg` . L’environnement l’appelle lorsque l’utilisateur choisit de démarrer le débogueur en appuyant sur F5.

 `ISpecifyPropertyPages` et `IDispatch` sont utilisés conjointement avec les pages de propriétés pour récupérer et afficher des informations dépendantes de la configuration pour l’utilisateur. Pour plus d’informations, consultez [pages de propriétés](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)
- [Pages de propriétés](../../extensibility/internals/property-pages.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)
