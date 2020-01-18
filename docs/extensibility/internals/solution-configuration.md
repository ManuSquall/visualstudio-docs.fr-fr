---
title: Configuration de la solution | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d0a4243d0d64fbd9a436b49f42c99c275e9714b
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269107"
---
# <a name="solution-configuration"></a>Configuration de la solution
Les configurations de solution stockent les propriétés au niveau de la solution. Ils dirigent le comportement de la clé de **démarrage** (F5) et des commandes de **génération** . Par défaut, ces commandes génèrent et démarrent la configuration Debug. Les deux commandes s’exécutent dans le contexte d’une configuration de solution. Cela signifie que l’utilisateur peut s’attendre à ce que la touche F5 démarre et génère la configuration de la solution active par le biais des paramètres. L’environnement est conçu pour optimiser les solutions plutôt que les projets lorsqu’il s’agit de générer et d’exécuter.

 La barre d’outils standard de Visual Studio contient un bouton Démarrer et une liste déroulante de configuration de solution à droite du bouton Démarrer. Cette liste permet aux utilisateurs de choisir la configuration à démarrer lorsque la touche F5 est enfoncée, de créer leurs propres configurations de solution ou de modifier une configuration existante.

> [!NOTE]
> Il n’existe aucune interface d’extensibilité pour créer ou modifier les configurations de solution. Vous devez utiliser `DTE.SolutionBuild`. Toutefois, il existe des API d’extensibilité pour la gestion de la génération de la solution. Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 Voici comment vous pouvez implémenter les configurations de solutions prises en charge par votre type de projet :

- Projet

   Affiche les noms des projets trouvés dans la solution actuelle.

- Configuration

   Pour fournir la liste des configurations prises en charge par votre type de projet et affichées dans les pages de propriétés, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>.

   La colonne configuration affiche le nom de la configuration de projet à générer dans cette configuration de solution et répertorie toutes les configurations de projet lorsque vous cliquez sur le bouton fléché. L’environnement appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> pour remplir cette liste. Si la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> indique que le projet prend en charge la modification de la configuration, les sélections nouveau ou modifier s’affichent également sous le titre configuration. Chacune de ces sélections lance des boîtes de dialogue qui appellent des méthodes de l’interface `IVsCfgProvider2` pour modifier les configurations du projet.

   Si un projet ne prend pas en charge les configurations, la colonne de configuration affiche la valeur aucun et est désactivée.

- Platform

   Affiche la plateforme pour laquelle la configuration de projet sélectionnée est générée et répertorie toutes les plateformes disponibles pour le projet lorsque vous cliquez sur le bouton fléché. L’environnement appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> pour remplir cette liste. Si la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> indique que le projet prend en charge la modification de la plateforme, les sélections nouveau ou modifier sont également affichées sous le titre de la plateforme. Chacune de ces sélections lance des boîtes de dialogue qui appellent `IVsCfgProvider2` méthodes pour modifier les plateformes disponibles du projet.

   Si un projet ne prend pas en charge les plateformes, la colonne plate-forme pour ce projet affiche aucun et est désactivée.

- Générer

   Spécifie si le projet est généré par la configuration de solution actuelle. Les projets non sélectionnés ne sont pas générés lorsque les commandes de génération au niveau de la solution sont appelées malgré les dépendances de projet qu’ils contiennent. Les projets qui ne sont pas sélectionnés pour être générés sont toujours inclus dans le débogage, l’exécution, l’empaquetage et le déploiement de la solution.

- Déployer

   Spécifie si le projet doit être déployé lorsque les commandes Démarrer ou déployer sont utilisées avec la configuration de build de solution sélectionnée. La case à cocher de ce champ sera disponible si le projet prend en charge le déploiement en implémentant l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> sur son objet <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>.

  Une fois que vous avez ajouté une nouvelle configuration de solution, l’utilisateur peut la sélectionner dans la zone de liste déroulante Configuration de la solution dans la barre d’outils standard pour générer et/ou démarrer cette configuration.

## <a name="see-also"></a>Voir aussi
- [Gestion des options de configuration](../../extensibility/internals/managing-configuration-options.md)
- [Configuration de projet pour la création](../../extensibility/internals/project-configuration-for-building.md)
- [Objet de configuration de projet](../../extensibility/internals/project-configuration-object.md)