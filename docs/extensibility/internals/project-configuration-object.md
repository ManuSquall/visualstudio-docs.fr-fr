---
title: Objet de Configuration de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d96766918f554e2b99dd8abc5faea9badaf69b5e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63423095"
---
# <a name="project-configuration-object"></a>Objet de configuration de projet
L’objet de configuration de projet gère l’affichage des informations de configuration à l’interface utilisateur.

 ![Configuration de projet Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") pages de propriétés de configuration de projet

 Le fournisseur de Configuration de projet gère les configurations de projet. L’environnement et autres packages, pour accéder à et récupérer des informations sur les configurations d’un projet, appelez les interfaces attachées à un objet de fournisseur de Configuration de projet.

> [!NOTE]
> Impossible de créer ou de modifier les fichiers de configuration de solution par programmation. Vous devez utiliser `DTE.SolutionBuilder`. Consultez [Configuration de la Solution](../../extensibility/internals/solution-configuration.md) pour plus d’informations.

 Pour publier un nom d’affichage à utiliser dans la configuration de l’interface utilisateur, votre projet doit implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. L’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, qui renvoie une liste de `IVsCfg` pointeurs que vous pouvez utiliser pour obtenir les noms d’affichage pour les informations de Configuration et la plateforme à lister dans l’interface utilisateur de l’environnement. La configuration active et la plateforme sont déterminés par la configuration du projet stockée dans la configuration de solution active. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> méthode peut être utilisée pour récupérer la configuration de projet actif.

 Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> objet peut éventuellement être implémenté sur le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> de l’objet avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> objet vous permet de récupérer un `IVsProjectCfg2` objet basé sur le nom de configuration de projet canonique.

 Une autre consiste à fournir l’environnement et autres projets ayant accès à des configurations de projet pour les projets afin de fournir une implémentation de la `IVsCfgProvider2::GetCfgs` méthode pour retourner un ou plusieurs objets de configuration. Les projets peuvent également implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, qui hérite de `IVsProjectCfg` et ainsi de `IVsCfg`, pour fournir des informations spécifiques à la configuration. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> prend en charge des plateformes et fonctionnalités pour ajouter, supprimer et renommer les configurations de projet.

> [!NOTE]
> Dans la mesure où Visual Studio n’est plus limité à deux types de configuration, le code qui traite les configurations ne doit pas être écrit avec hypothèses sur le nombre de configurations, ni doivent être écrits en partant du principe qu’un projet qui a un seul configuration n’est nécessairement Debug ou vente au détail. Cela rend l’utilisation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> obsolète.

 Appel `QueryInterface` sur l’objet retourné par`IVsGetCfgProvider::GetCfgProvider` récupère `IVsCfgProvider2`. Si `IVsGetCfgProvider` est introuvable en appelant `QueryInterface` sur le `IVsProject3` l’objet de projet, vous pouvez accéder à l’objet de fournisseur de configuration en appelant `QueryInterface` sur l’objet de navigateur hiérarchie racine pour l’objet retourné pour `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, ou via un pointeur vers le fournisseur de configuration retourné pour `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.

 `IVsProjectCfg2` principalement fournit un accès pour créer, déboguer et les objets de gestion de déploiement et permet aux projets de la possibilité de regrouper les sorties. Les méthodes de `IVsProjectCfg` et `IVsProjectCfg2` peut être utilisé pour implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> pour gérer le processus de génération et <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> des pointeurs pour les groupes de sortie d’une configuration.

 Le projet doit retourner le même nombre de groupes pour chaque configuration pris en charge, même si le nombre de sorties contenues dans un groupe peut varier à partir d’une configuration à une configuration. Les groupes doivent également posséder les mêmes informations d’identificateur (nom canonique, nom d’affichage et les informations de groupe) à partir d’une configuration à une configuration au sein d’un projet. Pour plus d’informations, consultez [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md).

 Pour activer le débogage, vos configurations doivent implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` est une interface facultative implémentée par les projets pour autoriser le débogueur à lancer une configuration et est implémenté sur l’objet de configuration avec `IVsCfg` et `IVsProjectCfg`. L’environnement appelle lorsque l’utilisateur choisit de démarrer le débogueur en appuyant sur F5.

 `ISpecifyPropertyPages` et `IDispatch` sont utilisés conjointement avec les pages de propriétés pour récupérer et afficher des informations dépend de la configuration à l’utilisateur. Pour plus d’informations, consultez [Pages de propriétés](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)
- [Pages de propriétés](../../extensibility/internals/property-pages.md)
- [Configuration de la solution](../../extensibility/internals/solution-configuration.md)