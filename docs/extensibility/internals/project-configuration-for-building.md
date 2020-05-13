---
title: Configuration du projet pour la construction (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706728"
---
# <a name="project-configuration-for-building"></a>Configuration de projet pour la création
La liste des configurations de solutions pour une solution donnée est gérée par la boîte de dialogue Solution Configurations.

 Un utilisateur peut créer des configurations de solutions supplémentaires, chacune avec son propre nom unique. Lorsque l’utilisateur crée une nouvelle configuration de solution, l’IDE est par défaut au nom de configuration correspondant dans les projets, ou Debug si aucun nom correspondant n’existe. L’utilisateur peut modifier la sélection pour répondre à des exigences spécifiques si nécessaire. La seule exception à ce comportement est lorsque le projet prend en charge une configuration qui correspond au nom de la nouvelle configuration de solution. Supposons, par exemple, qu’une solution contient Project1 et Project2. Project1 a des configurations de projet Debug, Retail, et MyConfig1. Project2 a des configurations de projet Debug, Retail, et MyConfig2.

 Si l’utilisateur crée une nouvelle configuration de solution nommée MyConfig2, Project1 lie sa configuration Debug à la configuration de la solution par défaut. Project2 lie également sa configuration MyConfig2 à la configuration de la solution par défaut.

> [!NOTE]
> La liaison est insensible aux cas.

 Lorsque l’utilisateur sélectionne **l’élément de sélection multiple** dans la liste d’abandon de configuration, l’environnement affiche une boîte de dialogue qui fournit la liste des configurations disponibles.

 ![Configurations multiples](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Configurations multiples

 Dans cette boîte de dialogue, l’utilisateur peut sélectionner une ou plusieurs configurations. Une fois sélectionnées, les valeurs de propriété affichées sur la boîte de dialogue des pages de propriété reflètent l’intersection des valeurs des configurations sélectionnées.

 Consultez [la configuration de solution](../../extensibility/internals/solution-configuration.md) pour obtenir des informations relatives à l’ajout et au changement de nom des configurations pour les solutions et les projets.

 Les dépendances du projet et l’ordre de construction sont indépendantes de configuration de solution : c’est-à-dire que vous ne pouvez mettre en place qu’un seul arbre de dépendance pour tous les projets de la solution. Cliquer à droite sur la solution ou le projet et choisir les **dépendances** du projet ou l’option **d’ordre de construction de projets** ouvre la boîte de dialogue **de dépendances de projet.** Il peut également être ouvert à partir du menu **du Projet.**

 ![Dépendances du projet](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Dépendances du projet

 Les dépendances du projet déterminent l’ordre dans lequel les projets s’accumulent. Utilisez l’onglet Commandez sur la boîte de dialogue pour voir l’ordre exact dans lequel les projets dans une solution s’accumuleront et utilisez l’onglet Dépendances pour modifier l’ordre de construction.

> [!NOTE]
> Les projets de la liste qui ont leurs cases à cocher sélectionnées mais <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> qui <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> semblent atténués ont été ajoutés par l’environnement en raison de dépendances explicites spécifiées par les interfaces ou les interfaces, et ne peuvent pas être modifiés. Par exemple, l’ajout [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] d’une référence de projet d’un projet à un autre projet ajoute automatiquement une dépendance à l’égard de la construction qui ne peut être supprimée qu’en supprimant la référence. Les projets dont les cases à cocher sont claires et semblent tamisées ne peuvent pas être sélectionnés parce que cela créerait une boucle de dépendance (par exemple, le projet1 dépendrait du projet2, et le projet2 dépendrait du projet1), ce qui retarderait la construction.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]les processus de construction comprennent les opérations de compilation et de liaison typiques qui sont invoquées avec une seule commande build. Deux autres processus de construction peuvent également être pris en charge : une opération propre pour supprimer tous les éléments de sortie d’une version précédente, et une vérification à jour pour déterminer si un élément de sortie dans une configuration a changé.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>les objets <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> renvoient <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>un correspondant (retourné de ) pour gérer leurs processus de construction. Pour signaler l’état d’une opération de construction <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>pendant qu’elle se produit, les configurations font des appels à , une interface implémentée par l’environnement et tout autre objet intéressé à construire des événements de statut.

 Une fois construits, les paramètres de configuration peuvent être utilisés pour déterminer s’ils peuvent être exécutés sous le contrôle du débbuggeur. Configurations <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> implémenter pour soutenir le débogage.

 Après la mise en œuvre des dépendances du projet, vous pouvez manipuler programmatiquement les dépendances à travers le modèle d’automatisation. Vous <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> appelez le modèle d’automatisation. Il n’existe pas d’interfaces vsIP au niveau de l’API disponibles qui permettent la manipulation directe des configurations de gestionnaire de construction de solutions et de leurs propriétés.

 En outre, vous pouvez fournir une grille dans la fenêtre de dépendances du projet. Pour plus d’informations, voir [Properties Display Grid](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la gestion du déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)
