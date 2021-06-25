---
title: Configuration du projet pour la génération | Microsoft Docs
description: Découvrez comment une liste de configurations de solutions pour une solution particulière est gérée par la boîte de dialogue configurations de solutions dans un nouveau type de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf98698d3527220c4bc25cdf36132f0088ae4ea7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899925"
---
# <a name="project-configuration-for-building"></a>Configuration de projet pour la création
La liste des configurations de solution pour une solution donnée est gérée par la boîte de dialogue configurations de solution.

 Un utilisateur peut créer des configurations de solution supplémentaires, chacune avec son propre nom unique. Lorsque l’utilisateur crée une configuration de solution, l’IDE a comme valeur par défaut le nom de configuration correspondant dans les projets, ou Déboguer si aucun nom correspondant n’existe. L’utilisateur peut modifier la sélection pour répondre à des exigences spécifiques si nécessaire. La seule exception à ce comportement est lorsque le projet prend en charge une configuration qui correspond au nom de la nouvelle configuration de solution. Par exemple, supposons qu’une solution contient Projet1 et project2. Project1 présente des configurations de projet Debug, Retail et MyConfig1. Project2 présente des configurations de projet Debug, Retail et MyConfig2.

 Si l’utilisateur crée une configuration de solution nommée MyConfig2, Project1 lie sa configuration Debug à la configuration de la solution par défaut. Project2 lie également sa configuration MyConfig2 à la configuration de la solution par défaut.

> [!NOTE]
> La liaison ne respecte pas la casse.

 Lorsque l’utilisateur sélectionne l’élément **sélection multiple** dans la liste déroulante Configuration, l’environnement affiche une boîte de dialogue qui fournit la liste des configurations disponibles.

 ![Configurations multiples](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Configurations multiples

 Dans cette boîte de dialogue, l’utilisateur peut sélectionner une ou plusieurs configurations. Une fois sélectionné, les valeurs de propriété affichées dans la boîte de dialogue pages de propriétés reflètent l’intersection des valeurs des configurations sélectionnées.

 Pour plus d’informations sur l’ajout et le changement de nom des configurations pour les solutions et les projets, consultez Configuration de la [solution](../../extensibility/internals/solution-configuration.md) .

 Les dépendances de projet et l’ordre de génération sont indépendants de la configuration de solution : autrement dit, vous ne pouvez configurer qu’une seule arborescence de dépendances pour tous les projets de la solution. Si vous cliquez avec le bouton droit sur la solution ou le projet et que vous sélectionnez l’option **dépendances** du projet ou **ordre de génération** du projet, la boîte de dialogue **dépendances** du projet s’ouvre. Vous pouvez également l’ouvrir à partir du menu **projet** .

 ![Dépendances du projet](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Dépendances du projet

 Les dépendances de projet déterminent l’ordre dans lequel les projets sont générés. Utilisez l’onglet ordre de la génération de la boîte de dialogue pour afficher l’ordre exact dans lequel les projets d’une solution seront générés, et utilisez l’onglet dépendances pour modifier l’ordre de génération.

> [!NOTE]
> Les projets de la liste dont les cases à cocher sont activées mais qui apparaissent grisées ont été ajoutés par l’environnement en raison de dépendances explicites spécifiées par les <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaces ou, et ne peuvent pas être modifiées. Par exemple, l’ajout d’une référence de projet d’un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projet à un autre projet ajoute automatiquement une dépendance de génération qui peut uniquement être supprimée en supprimant la référence. Les projets dont les cases à cocher sont claires et qui apparaissent grisées ne peuvent pas être sélectionnés, car cela crée une boucle de dépendance (par exemple, Project1 dépend de Project2 et Project2 dépend de Projet1), ce qui bloquerait la Build.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les processus de génération incluent les opérations de compilation et de liaison classiques qui sont appelées avec une seule commande de génération. Deux autres processus de génération peuvent également être pris en charge : une opération de nettoyage pour supprimer tous les éléments de sortie d’une build précédente et une vérification à jour pour déterminer si un élément de sortie d’une configuration a changé.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> les objets retournent un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (retourné par <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ) correspondant pour gérer leurs processus de génération. Pour signaler l’état d’une opération de génération pendant qu’elle se produit, les configurations effectuent des appels à <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> , une interface implémentée par l’environnement et tout autre objet qui s’intéresse aux événements d’état de Build.

 Une fois générés, les paramètres de configuration peuvent être utilisés pour déterminer s’ils peuvent ou non être exécutés sous le contrôle du débogueur. Les configurations implémentent <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> pour prendre en charge le débogage.

 Après avoir implémenté les dépendances du projet, vous pouvez manipuler par programmation les dépendances par le biais du modèle Automation. Vous appelez <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> dans le modèle Automation. Il n’y a pas d’interfaces de niveau d’API VSIP disponibles qui autorisent la manipulation directe des configurations du gestionnaire de build de solution et de leurs propriétés.

 En outre, vous pouvez fournir une grille dans la fenêtre dépendances du projet. Pour plus d’informations, consultez Affichage de la [grille des propriétés](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la gestion du déploiement](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configuration de projet pour la sortie](../../extensibility/internals/project-configuration-for-output.md)
